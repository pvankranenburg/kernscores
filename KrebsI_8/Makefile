COM = "Krebs, Johann Ludwig"
OTL = "Fuga"
OMV = "2"
SCT = "I.8"
SCA = "Johann Ludwig Krebs, Sämtliche Orgelwerke. Herausgegeven von Gerhard Weinberger."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = KrebsI_8

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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > $(basename)-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d $(basename)-temp.krn >> $(basename).krn
	rm $(basename)-temp.krn
	proof $(basename).krn
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
	yank -o ^= -r '$$-10-$$' $(basename).krn > $(basename)-test.krn
	midi -u -q 80 < $(basename)-test.krn > $(basename)-test.hmd
	hmd2mid $(basename)-test.hmd
	rm $(basename)-test.hmd

midi: kernfile
	midi -u -q 80 < $(basename).krn > $(basename).hmd
	hmd2mid $(basename).hmd
	rm $(basename).hmd

play: midi
	artsdsp timidity -in -A 140 $(basename).mid

testplay: testmidi
	artsdsp timidity -in -A 140 $(basename)-test.mid

clean:
	rm *.krn
	rm *.mid
