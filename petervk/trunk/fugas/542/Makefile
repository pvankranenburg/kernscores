kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv542-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv542-temp.krn > bwv542.krn
	rm bwv542-temp.krn
	proof bwv542.krn

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
	midi -u -q 100 < bwv542.krn > bwv542.hmd
	hmd2mid bwv542.hmd
	rm bwv542.hmd

play: midi
	timidity -in bwv542.mid

clean:
	rm *.krn
	rm *.mid
