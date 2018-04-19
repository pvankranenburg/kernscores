COM = "Jan Pieterszn Sweelinck"
OTL = "Fantasia Chromatica"
OMV = ""
SCT = ""
SCA = ""
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `date -r 1.pk +%F`

basename = Sweelinck_Chromatica
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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Sweelinck_Chromatica-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Sweelinck_Chromatica-temp.krn >> Sweelinck_Chromatica.krn
	rm Sweelinck_Chromatica-temp.krn
	proof Sweelinck_Chromatica.krn
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
	hum2mid -o Sweelinck_Chromatica.mid Sweelinck_Chromatica.krn

testmidi: kernfile
	#myank -m '$$18-$$' Sweelinck_Chromatica.krn > Sweelinck_Chromatica-test.krn
	myank -m '164-$$' Sweelinck_Chromatica.krn > Sweelinck_Chromatica-test.krn
	hum2mid -o Sweelinck_Chromatica-test.mid Sweelinck_Chromatica-test.krn

testplay: testmidi
	timidity Sweelinck_Chromatica-test.mid

play: midi
	timidity Sweelinck_Chromatica.mid

clean:
	rm *.krn
	rm *.mid
	rm *.hmd

