kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv535a-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv535a-temp.krn > bwv535a.krn
	rm bwv535a-temp.krn
	proof bwv535a.krn

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
	midi -u -q 120 < bwv535a.krn > bwv535a.hmd
	hmd2mid bwv535a.hmd
	rm bwv535a.hmd

play: midi
	timidity -in bwv535a.mid

clean:
	rm *.krn
	rm *.mid
