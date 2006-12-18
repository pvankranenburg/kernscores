COM = "Bach, Johann Sebastian"
OTL = "Fuga"
OMV = "2"
SCT = "BWV 543"
SCA = "Thematisches-systematisches Verzeichnis der musikalischen Werke von Johann Sebastian Bach \(Schmieder 1990\)"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = bwv543

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!OMV: $(OMV)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv543-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv543-temp.krn >> bwv543.krn
	rm bwv543-temp.krn
	proof bwv543.krn
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
	midi -u -q 120 < bwv543.krn > bwv543.hmd
	hmd2mid bwv543.hmd
	rm bwv543.hmd

play: midi
	timidity -in bwv543.mid

clean:
	rm *.krn
	rm *.mid
