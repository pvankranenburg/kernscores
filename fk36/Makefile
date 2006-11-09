kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > fk36-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d fk36-temp.krn > fk36.krn
	rm fk36-temp.krn
	proof fk36.krn

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
	yank -o ^= -r '$$-15-$$' fk36.krn > fk36-test.krn
	midi -u -q 100 < fk36-test.krn > fk36-test.hmd
	hmd2mid fk36-test.hmd
	rm fk36-test.hmd

midi: kernfile
	midi -u -q 100 < fk36.krn > fk36.hmd
	hmd2mid fk36.hmd
	rm fk36.hmd

play: midi
	artsdsp timidity -in fk36.mid

testplay: testmidi
	artsdsp timidity -in fk36-test.mid

clean:
	rm *.krn
	rm *.mid
	
