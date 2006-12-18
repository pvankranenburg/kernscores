COM = "Bach, Johann Sebastian"
OTL = "Fuga"
OMV = "2"
SCT = "BWV 538"
SCA = "Thematisches-systematisches Verzeichnis der musikalischen Werke von Johann Sebastian Bach \(Schmieder 1990\)"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = bwv538

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!OMV: $(OMV)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > bwv538-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d bwv538-temp.krn >> bwv538.krn
	rm bwv538-temp.krn
	proof bwv538.krn
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

testmidi: kernfile
	yank -o ^= -r '$$-10-$$' bwv538.krn > bwv538-test.krn
	midi -u -q 60 < bwv538-test.krn > bwv538-test.hmd
	hmd2mid bwv538-test.hmd
	rm bwv538-test.hmd

midi: kernfile
	midi -u -q 60 < bwv538.krn > bwv538.hmd
	hmd2mid bwv538.hmd
	rm bwv538.hmd

play: midi
	timidity -in bwv538.mid

testplay: testmidi
	timidity -in bwv538-test.mid

clean:
	rm *.krn
	rm *.mid
