kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv559-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv559-temp.krn > bwv559.krn
	rm bwv559-temp.krn
	proof bwv559.krn

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
	yank -o ^= -r '$$-10-$$' bwv559.krn > bwv559-test.krn
	midi -u -q 60 < bwv559-test.krn > bwv559-test.hmd
	hmd2mid bwv559-test.hmd
	rm bwv559-test.hmd

midi: kernfile
	midi -u -q 60 < bwv559.krn > bwv559.hmd
	hmd2mid bwv559.hmd
	rm bwv559.hmd

play: midi
	timidity -in bwv559.mid

testplay: testmidi
	timidity -in bwv559-test.mid

clean:
	rm *.krn
	rm *.mid
