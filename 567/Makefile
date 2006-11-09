kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv567-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv567-temp.krn > bwv567.krn
	#cp bwv567-temp.krn FriedenmannII.krn
	rm bwv567-temp.krn
	proof bwv567.krn

prekern:
	prekern 1.pk
	prekern 2.pk
	prekern 3.pk
	prekern 4.pk

proof: prekern
	proof 1.krn
	proof 2.krn
	proof 3.krn
	proof 4.krn

testmidi: kernfile
	yank -o ^= -r '$$-15-$$' bwv567.krn > bwv567-test.krn
	midi -u -q 90 < bwv567-test.krn > bwv567-test.hmd
	hmd2mid bwv567-test.hmd
	rm bwv567-test.hmd

midi: kernfile
	midi -u -q 90 < bwv567.krn > bwv567.hmd
	hmd2mid bwv567.hmd
	rm bwv567.hmd

play: midi
	timidity -in bwv567.mid

testplay: testmidi
	timidity -in bwv567-test.mid

clean:
	rm *.krn
	rm *.mid
