kernfile: prekern
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Krebs-Gdur-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Krebs-Gdur-temp.krn > Krebs-Gdur.krn
	rm Krebs-Gdur-temp.krn
	proof Krebs-Gdur.krn

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
	yank -o ^= -r '$$-10-$$' Krebs-Gdur.krn > Krebs-Gdur-test.krn
	midi -u -q 80 < Krebs-Gdur-test.krn > Krebs-Gdur-test.hmd
	hmd2mid Krebs-Gdur-test.hmd
	rm Krebs-Gdur-test.hmd

midi: kernfile
	midi -u -q 80 < Krebs-Gdur.krn > Krebs-Gdur.hmd
	hmd2mid Krebs-Gdur.hmd
	rm Krebs-Gdur.hmd

play: midi
	artsdsp timidity -in -A 140 Krebs-Gdur.mid

testplay: testmidi
	artsdsp timidity -in -A 140 Krebs-Gdur-test.mid

clean:
	rm *.krn
	rm *.mid
