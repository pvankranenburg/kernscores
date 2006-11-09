kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv557-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv557-temp.krn > bwv557.krn
	rm bwv557-temp.krn
	proof bwv557.krn

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
	yank -o ^= -r '$$-10-$$' bwv557.krn > bwv557-test.krn
	midi -u -q 60 < bwv557-test.krn > bwv557-test.hmd
	hmd2mid bwv557-test.hmd
	rm bwv557-test.hmd

midi: kernfile
	midi -u -q 60 < bwv557.krn > bwv557.hmd
	hmd2mid bwv557.hmd
	rm bwv557.hmd

play: midi
	timidity -in bwv557.mid

testplay: testmidi
	timidity -in bwv557-test.mid

clean:
	rm *.krn
	rm *.mid
