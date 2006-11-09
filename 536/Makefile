kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv536-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv536-temp.krn > bwv536.krn
	rm bwv536-temp.krn
	proof bwv536.krn

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

midi: kernfile
	midi -u -q 80 < bwv536.krn > bwv536.hmd
	hmd2mid bwv536.hmd
	rm bwv536.hmd

play: midi
	timidity -in bwv536.mid

clean:
	rm *.krn
	rm *.mid
