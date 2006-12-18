COM = "Bach, Wilhelm Friedemann"
OTL = "Fuga"
SCT = "FK 37"
SCA = "Martin Falck, Wilhelm Friedemann Bach - Sein Leben und seine Werke, Leipzig, 1913"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = fk37

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > fk37-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d fk37-temp.krn >> fk37.krn
	rm fk37-temp.krn
	proof fk37.krn
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
	yank -o ^= -r '$$-10-$$' fk37.krn > fk37-test.krn
	midi -u -q 90 < fk37-test.krn > fk37-test.hmd
	hmd2mid fk37-test.hmd
	rm fk37-test.hmd

midi: kernfile
	midi -u -q 90 < fk37.krn > fk37.hmd
	hmd2mid fk37.hmd
	rm fk37.hmd

play: midi
	timidity -in fk37.mid

testplay: testmidi
	timidity -in fk37-test.mid

clean:
	rm *.krn
	rm *.mid
