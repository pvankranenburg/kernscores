COM = "Kellner, Johann Ludwig"
OTL = "Fuga"
OMV = "2"
SCT = "O08:06"
SCA = "Rolf Dietrich Claus, Johann Peter Kellner - Studien zu Leben und Werk."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = O0806

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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > O0806-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d O0806-temp.krn >> O0806.krn
	rm O0806-temp.krn
	proof O0806.krn
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
	yank -o ^= -r '$$-10-$$' O0806.krn > O0806-test.krn
	midi -u -q 90 < O0806-test.krn > O0806-test.hmd
	hmd2mid O0806-test.hmd
	rm O0806-test.hmd

midi: kernfile
	midi -u -q 90 < O0806.krn > O0806.hmd
	hmd2mid O0806.hmd
	rm O0806.hmd

play: midi
	timidity -in O0806.mid

testplay: testmidi
	timidity -in O0806-test.mid

clean:
	rm *.krn
	rm *.mid
