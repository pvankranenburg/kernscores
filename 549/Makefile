kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > bwv549-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d bwv549-temp.krn > bwv549.krn
	rm bwv549-temp.krn
	proof bwv549.krn

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

midi: kernfile
	midi -u < bwv549.krn > bwv549.hmd
	hmd2mid bwv549.hmd
	rm bwv549.hmd

play: midi
	timidity -in bwv549.mid

clean:
	rm *.krn
	rm *.mid
	
