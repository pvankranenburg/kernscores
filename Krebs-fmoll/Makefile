kernfile: prekern
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Krebs-fmoll-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Krebs-fmoll-temp.krn > Krebs-fmoll.krn
	rm Krebs-fmoll-temp.krn
	proof Krebs-fmoll.krn

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
	yank -o ^= -r '$$-20-$$' Krebs-fmoll.krn > Krebs-fmoll-test.krn
	midi -u -q 60 < Krebs-fmoll-test.krn > Krebs-fmoll-test.hmd
	hmd2mid Krebs-fmoll-test.hmd
	rm Krebs-fmoll-test.hmd

midi: kernfile
	midi -u -q 60 < Krebs-fmoll.krn > Krebs-fmoll.hmd
	hmd2mid Krebs-fmoll.hmd
	rm Krebs-fmoll.hmd

play: midi
	artsdsp timidity -in -A 140 Krebs-fmoll.mid

testplay: testmidi
	artsdsp timidity -in -A 140 Krebs-fmoll-test.mid

clean:
	rm *.krn
	rm *.mid
