COM = "Johann Sebastian Bach"
OTL = "Fuga supra il Magnificat"
OMV = ""
SCT = "BWV 733"
SCA = "Thematisches-systematisches Verzeichnis der musikalischen Werke von Johann Sebastian Bach \(Schmieder 1990\)"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `date -r 1.pk +%F`

basename = bwv733
dolar = '$'

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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > $(basename)-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
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
	prekern 5.pk

proof: prekern
	proof 1.krn
	proof 2.krn
	proof 3.krn
	proof 4.krn
	proof 5.krn

midi: kernfile
	hum2mid -o $(basename).mid $(basename).krn

testmidi: kernfile
	myank -m '130-$$' $(basename).krn > $(basename)-test.krn
	hum2mid -o $(basename)-test.mid $(basename)-test.krn

testplay: testmidi
	timidity $(basename)-test.mid

play: midi
	timidity $(basename).mid

clean:
	rm *.krn
	rm *.mid
	rm *.hmd

