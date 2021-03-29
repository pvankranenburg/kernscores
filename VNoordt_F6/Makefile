COM = "Anthoni van Noordt"
OTL = "Fantasia"
OMV = ""
SCT = ""
SCA = ""
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `date -r 1.pk +%F`

basename = VNoordt_F6
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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > VNoordt_F6-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d VNoordt_F6-temp.krn >> VNoordt_F6.krn
	rm VNoordt_F6-temp.krn
	proof VNoordt_F6.krn
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
	hum2mid -o VNoordt_F6.mid VNoordt_F6.krn

testmidi: kernfile
	myank -m '77-$$' VNoordt_F6.krn > VNoordt_F6-test.krn
	hum2mid -o VNoordt_F6-test.mid VNoordt_F6-test.krn

testplay: testmidi
	timidity VNoordt_F6-test.mid

play: midi
	timidity -T VNoordt_F6.mid

clean:
	rm *.krn
	rm *.mid
	rm *.hmd

