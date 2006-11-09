kernfile: prekern
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn > fk33-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn
	rid -d fk33-temp.krn > fk33.krn
	rm fk33-temp.krn
	proof fk33.krn

prekern:
	prekern 1.pk
	prekern 2.pk
	prekern 3.pk
	
proof: prekern
	proof 1.krn
	proof 2.krn
	proof 3.krn

testmidi: kernfile
	yank -o ^= -r '$$-15-$$' fk33.krn > fk33-test.krn
	midi -u -q 90 < fk33-test.krn > fk33-test.hmd
	hmd2mid fk33-test.hmd
	rm fk33-test.hmd

midi: kernfile
	midi -u -q 90 < fk33.krn > fk33.hmd
	hmd2mid fk33.hmd
	rm fk33.hmd

play: midi
	artsdsp timidity -in -A 140 fk33.mid

testplay: testmidi
	artsdsp timidity -in -A 140 fk33-test.mid

clean:
	rm *.krn
	rm *.mid
