COM = "Bach, Wilhelm Friedemann"
OTL = "Fuga"
SCT = "FK-Add. 211/1"
SCA = "Peter Wollny, Studies in the music of Wilhelm Friedemann Bach, Cambridge, 1993"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = fk211_1

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > fk211_1-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d fk211_1-temp.krn >> fk211_1.krn
	rm fk211_1-temp.krn
	proof fk211_1.krn
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
	yank -o ^= -r '$$-10-$$' fk211_1.krn > fk211_1-test.krn
	midi -u -q 90 < fk211_1-test.krn > fk211_1-test.hmd
	hmd2mid fk211_1-test.hmd
	rm fk211_1-test.hmd

midi: kernfile
	midi -u -q 90 < fk211_1.krn > fk211_1.hmd
	hmd2mid fk211_1.hmd
	rm fk211_1.hmd

play: midi
	timidity -in fk211_1.mid

testplay: testmidi
	timidity -in fk211_1-test.mid

clean:
	rm *.krn
	rm *.mid
