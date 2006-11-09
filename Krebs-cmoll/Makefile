kernfile: prekern
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Krebs-cmoll-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Krebs-cmoll-temp.krn > Krebs-cmoll.krn
	rm Krebs-cmoll-temp.krn
	proof Krebs-cmoll.krn

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
	yank -o ^= -r '$$-15-$$' Krebs-cmoll.krn > Krebs-cmoll-test.krn
	midi -u -q 90 < Krebs-cmoll-test.krn > Krebs-cmoll-test.hmd
	hmd2mid Krebs-cmoll-test.hmd
	rm Krebs-cmoll-test.hmd

midi: kernfile
	midi -u -q 90 < Krebs-cmoll.krn > Krebs-cmoll.hmd
	hmd2mid Krebs-cmoll.hmd
	rm Krebs-cmoll.hmd

play: midi
	artsdsp timidity -in -A 140 Krebs-cmoll.mid

testplay: testmidi
	artsdsp timidity -in -A 140 Krebs-cmoll-test.mid

clean:
	rm *.krn
	rm *.mid
