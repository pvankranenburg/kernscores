COM = "Krebs, Johann Ludwig"
OTL = "Fuga"
SCT = "II.19"
SCA = "Johann Ludwig Krebs, Sämtliche Orgelwerke. Herausgegeven von Gerhard Weinberger."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = KrebsII_19

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > KrebsII_19-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d KrebsII_19-temp.krn >> KrebsII_19.krn
	rm KrebsII_19-temp.krn
	proof KrebsII_19.krn
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
	yank -o ^= -r '$$-15-$$' KrebsII_19.krn > KrebsII_19-test.krn
	midi -u -q 60 < KrebsII_19-test.krn > KrebsII_19-test.hmd
	hmd2mid KrebsII_19-test.hmd
	rm KrebsII_19-test.hmd

midi: kernfile
	midi -u < KrebsII_19.krn > KrebsII_19.hmd
	hmd2mid KrebsII_19.hmd
	rm KrebsII_19.hmd

play: midi
	artsdsp timidity -in KrebsII_19.mid

testplay: testmidi
	artsdsp timidity -in KrebsII_19-test.mid

clean:
	rm *.krn
	rm *.mid
	
