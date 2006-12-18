COM = "Bach, Johann Sebastian \(disputed\)"
OTL = "Fuga"
OMV = "2"
SCT = "BWV 556"
SCA = "Thematisches-systematisches Verzeichnis der musikalischen Werke von Johann Sebastian Bach \(Schmieder 1990\)"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = bwv556

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
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > bwv556-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d bwv556-temp.krn >> bwv556.krn
	rm bwv556-temp.krn
	proof bwv556.krn
	echo "!!!ENC: $(ENC)" >> $(basename).krn
	echo "!!!END: $(END)" >> $(basename).krn

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

testmidi: kernfile
	yank -o ^= -r '$$-15-$$' bwv556.krn > bwv556-test.krn
	midi -u -q 90 < bwv556-test.krn > bwv556-test.hmd
	hmd2mid bwv556-test.hmd
	rm bwv556-test.hmd

midi: kernfile
	midi -u -q 90 < bwv556.krn > bwv556.hmd
	hmd2mid bwv556.hmd
	rm bwv556.hmd

play: midi
	artsdsp timidity -in -A 140 bwv556.mid

testplay: testmidi
	artsdsp timidity -in -A 140 bwv556-test.mid

clean:
	rm *.krn
	rm *.mid
