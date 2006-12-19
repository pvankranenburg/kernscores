COM = "Schneider, Johann"
OTL = "Fuga"
OMV = "2"
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = Schneidergmoll

kernfile: prekern
	echo "!!!COM: $(COM)" > $(basename).krn
	echo "!!!OTL: $(OTL)" >> $(basename).krn
	echo "!!!OMV: $(OMV)" >> $(basename).krn
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > Schneidergmoll-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d Schneidergmoll-temp.krn >> Schneidergmoll.krn
	rm Schneidergmoll-temp.krn
	proof Schneidergmoll.krn
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
	yank -o ^= -r '$$-15-$$' Schneidergmoll.krn > Schneidergmoll-test.krn
	midi -u -q 70 < Schneidergmoll-test.krn > Schneidergmoll-test.hmd
	hmd2mid Schneidergmoll-test.hmd
	rm Schneidergmoll-test.hmd

midi: kernfile
	midi -u -q 70 < Schneidergmoll.krn > Schneidergmoll.hmd
	hmd2mid Schneidergmoll.hmd
	rm Schneidergmoll.hmd

play: midi
	timidity -in Schneidergmoll.mid

testplay: testmidi
	timidity -in Schneidergmoll-test.mid

clean:
	rm *.krn
	rm *.mid
