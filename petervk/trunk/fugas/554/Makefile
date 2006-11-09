kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > bwv554-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d bwv554-temp.krn > bwv554.krn
	rm bwv554-temp.krn
	proof bwv554.krn

prekern:
	prekern 1.pk
	prekern 2.pk
	prekern 3.pk
	prekern 4.pk
	prekern 5.pk

proof: prekern
	proof 1.krn
	proof 2.krn
	proof 3.krn
	proof 4.krn
	proof 5.krn

testmidi: kernfile
	yank -o ^= -r '$$-15-$$' bwv554.krn > bwv554-test.krn
	midi -u -q 90 < bwv554-test.krn > bwv554-test.hmd
	hmd2mid bwv554-test.hmd
	rm bwv554-test.hmd

midi: kernfile
	midi -u -q 90 < bwv554.krn > bwv554.hmd
	hmd2mid bwv554.hmd
	rm bwv554.hmd

play: midi
	artsdsp timidity -in -A 140 bwv554.mid

testplay: testmidi
	artsdsp timidity -in -A 140 bwv554-test.mid

clean:
	rm *.krn
	rm *.mid
