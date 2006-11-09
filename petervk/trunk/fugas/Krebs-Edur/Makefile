kernfile: prekern
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Krebs-Edur-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Krebs-Edur-temp.krn > Krebs-Edur.krn
	rm Krebs-Edur-temp.krn
	proof Krebs-Edur.krn

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
	yank -o ^= -r '$$-20-$$' Krebs-Edur.krn > Krebs-Edur-test.krn
	midi -u -q 100 < Krebs-Edur-test.krn > Krebs-Edur-test.hmd
	hmd2mid Krebs-Edur-test.hmd
	rm Krebs-Edur-test.hmd

midi: kernfile
	midi -u -q 100 < Krebs-Edur.krn > Krebs-Edur.hmd
	hmd2mid Krebs-Edur.hmd
	rm Krebs-Edur.hmd

play: midi
	artsdsp timidity -in -A 140 Krebs-Edur.mid

testplay: testmidi
	artsdsp timidity -in -A 140 Krebs-Edur-test.mid

clean:
	rm *.krn
	rm *.mid
