kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv555-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv555-temp.krn > bwv555.krn
	rm bwv555-temp.krn
	proof bwv555.krn

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
	yank -o ^= -r '$$-10-$$' bwv555.krn > bwv555-test.krn
	midi -u -q 60 < bwv555-test.krn > bwv555-test.hmd
	hmd2mid bwv555-test.hmd
	rm bwv555-test.hmd

midi: kernfile
	midi -u -q 60 < bwv555.krn > bwv555.hmd
	hmd2mid bwv555.hmd
	rm bwv555.hmd

play: midi
	timidity -in bwv555.mid

testplay: testmidi
	timidity -in bwv555-test.mid

clean:
	rm *.krn
	rm *.mid
