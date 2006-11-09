kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv560-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv560-temp.krn > bwv560.krn
	rm bwv560-temp.krn
	proof bwv560.krn

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
	yank -o ^= -r '$$-10-$$' bwv560.krn > bwv560-test.krn
	midi -u -q 60 < bwv560-test.krn > bwv560-test.hmd
	hmd2mid bwv560-test.hmd
	rm bwv560-test.hmd

midi: kernfile
	midi -u -q 60 < bwv560.krn > bwv560.hmd
	hmd2mid bwv560.hmd
	rm bwv560.hmd

play: midi
	timidity -in bwv560.mid

testplay: testmidi
	timidity -in bwv560-test.mid

clean:
	rm *.krn
	rm *.mid
