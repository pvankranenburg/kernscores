kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > fk211_2-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d fk211_2-temp.krn > fk211_2.krn
	#cp fk211_2-temp.krn FriedenmannII.krn
	rm fk211_2-temp.krn
	proof fk211_2.krn

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
	yank -o ^= -r '$$-10-$$' fk211_2.krn > fk211_2-test.krn
	midi -u -q 90 < fk211_2-test.krn > fk211_2-test.hmd
	hmd2mid fk211_2-test.hmd
	rm fk211_2-test.hmd

midi: kernfile
	midi -u -q 90 < fk211_2.krn > fk211_2.hmd
	hmd2mid fk211_2.hmd
	rm fk211_2.hmd

play: midi
	timidity -in fk211_2.mid

testplay: testmidi
	timidity -in fk211_2-test.mid

clean:
	rm *.krn
	rm *.mid
