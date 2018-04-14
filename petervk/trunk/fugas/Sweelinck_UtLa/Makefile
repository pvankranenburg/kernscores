COM = "Jan Pieterszn Sweelinck"
OTL = "Fantasia Ut Re Mi Fa Sol La"
OMV = ""
SCT = ""
SCA = ""
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `date -r 1.pk +%F`

basename = Sweelinck_UtLa
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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Sweelinck_UtLa-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Sweelinck_UtLa-temp.krn >> Sweelinck_UtLa.krn
	rm Sweelinck_UtLa-temp.krn
	proof Sweelinck_UtLa.krn
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
	hum2mid -o Sweelinck_UtLa.mid Sweelinck_UtLa.krn

testmidi: kernfile
	#myank -m '$$18-$$' Sweelinck_UtLa.krn > Sweelinck_UtLa-test.krn
	myank -m '196-$$' Sweelinck_UtLa.krn > Sweelinck_UtLa-test.krn
	hum2mid -o Sweelinck_UtLa-test.mid Sweelinck_UtLa-test.krn

testplay: testmidi
	timidity Sweelinck_UtLa-test.mid

play: midi
	timidity Sweelinck_UtLa.mid

clean:
	rm *.krn
	rm *.mid
	rm *.hmd

