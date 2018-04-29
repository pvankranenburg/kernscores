COM = "Girolamo Frescobaldi"
OTL = "Fantasia Seconda"
OMV = ""
SCT = ""
SCA = ""
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `date -r 1.pk +%F`

basename = Frescobaldi_F2
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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Frescobaldi_F2-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Frescobaldi_F2-temp.krn >> Frescobaldi_F2.krn
	rm Frescobaldi_F2-temp.krn
	proof Frescobaldi_F2.krn
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
	hum2mid -o Frescobaldi_F2.mid Frescobaldi_F2.krn

test: kernfile
	proof Frescobaldi_F2.krn | head | grep -v "identical to measure"

testmidi: kernfile
	#myank -m '$$18-$$' Frescobaldi_F2.krn > Frescobaldi_F2-test.krn
	myank -m '85-$$' Frescobaldi_F2.krn > Frescobaldi_F2-test.krn
	hum2mid -o Frescobaldi_F2-test.mid Frescobaldi_F2-test.krn

testplay: testmidi
	timidity Frescobaldi_F2-test.mid

play: midi
	timidity Frescobaldi_F2.mid

clean:
	rm *.krn
	rm *.mid
	rm *.hmd

