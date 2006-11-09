kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv565-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv565-temp.krn > bwv565.krn
	#cp bwv565-temp.krn FriedenmannII.krn
	rm bwv565-temp.krn
	proof bwv565.krn

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
	yank -o ^= -r '$$-10-$$' bwv565.krn > bwv565-test.krn
	midi -u -q 90 < bwv565-test.krn > bwv565-test.hmd
	hmd2mid bwv565-test.hmd
	rm bwv565-test.hmd

midi: kernfile
	midi -u -q 90 < bwv565.krn > bwv565.hmd
	hmd2mid bwv565.hmd
	rm bwv565.hmd

play: midi
	timidity -in bwv565.mid

testplay: testmidi
	timidity -in bwv565-test.mid

clean:
	rm *.krn
	rm *.mid
