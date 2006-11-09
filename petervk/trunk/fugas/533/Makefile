kernfile:
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv533-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv533-temp.krn > bwv533.krn
	rm bwv533-temp.krn
	proof bwv533.krn

proof:
	proof 1.krn
	proof 2.krn
	proof 3.krn
	proof 4.krn

midi: kernfile
	midi -u -q 100 < bwv533.krn > bwv533.hmd
	hmd2mid bwv533.hmd
	rm bwv533.hmd

play: midi
	timidity -in bwv533.mid
