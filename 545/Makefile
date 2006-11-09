kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv545-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv545-temp.krn > bwv545.krn
	rm bwv545-temp.krn
	proof bwv545.krn

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
	midi -u -q 80 < bwv545.krn > bwv545.hmd
	hmd2mid bwv545.hmd
	rm bwv545.hmd

play: midi
	timidity -in bwv545.mid

clean:
	rm *.krn
	rm *.mid
