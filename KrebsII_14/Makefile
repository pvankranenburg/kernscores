COM = "Krebs, Johann Ludwig"
OTL = "Fuga"
SCT = "II.14"
SCA = "Johann Ludwig Krebs, Sämtliche Orgelwerke. Herausgegeven von Gerhard Weinberger."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = KrebsII_14

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!SCT: $(SCT)" >> $(basename).krn
	echo "!!!SCA: $(SCA)" >> $(basename).krn
	timebase -t 64 1.krn > 1-32.krn
	timebase -t 64 2.krn > 2-32.krn
	timebase -t 64 3.krn > 3-32.krn
	timebase -t 64 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > KrebsII_14-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d KrebsII_14-temp.krn >> KrebsII_14.krn
	rm KrebsII_14-temp.krn
	proof KrebsII_14.krn
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
	yank -o ^= -r '$$-15-$$' KrebsII_14.krn > KrebsII_14-test.krn
	midi -u -q 60 < KrebsII_14-test.krn > KrebsII_14-test.hmd
	hmd2mid KrebsII_14-test.hmd
	rm KrebsII_14-test.hmd

midi: kernfile
	midi -u -q 60 < KrebsII_14.krn > KrebsII_14.hmd
	hmd2mid KrebsII_14.hmd
	rm KrebsII_14.hmd

play: midi
	artsdsp timidity -in -A 140 KrebsII_14.mid

testplay: testmidi
	artsdsp timidity -in -A 140 KrebsII_14-test.mid

clean:
	rm *.krn
	rm *.mid
