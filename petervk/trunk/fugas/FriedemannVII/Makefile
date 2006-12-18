COM = "Bach, Wilhelm Friedemann ??"
OTL = "Fuga"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = FriedemannVII

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > VII-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d VII-temp.krn >> FriedemannVII.krn
	rm VII-temp.krn
	proof FriedemannVII.krn
	echo "!!!ENC: $(ENC)" >> $(basename).krn
	echo "!!!END: $(END)" >> $(basename).krn

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
	midi -u -q 80 < FriedemannVII.krn > FriedemannVII.hmd
	hmd2mid FriedemannVII.hmd
	rm FriedemannVII.hmd

play: midi
	timidity -in FriedemannVII.mid

clean:
	rm *.krn
	rm *.mid
