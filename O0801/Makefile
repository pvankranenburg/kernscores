COM = "Kellner, Johann Ludwig"
OTL = "Fuga"
OMV = "2"
SCT = "O08:01"
SCA = "Rolf Dietrich Claus, Johann Peter Kellner - Studien zu Leben und Werk."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = O0801

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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > O0801-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d O0801-temp.krn >> O0801.krn
	rm O0801-temp.krn
	proof O0801.krn
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
	yank -o ^= -r '$$-10-$$' O0801.krn > O0801-test.krn
	midi -u -q 90 < O0801-test.krn > O0801-test.hmd
	hmd2mid O0801-test.hmd
	rm O0801-test.hmd

midi: kernfile
	midi -u -q 90 < O0801.krn > O0801.hmd
	hmd2mid O0801.hmd
	rm O0801.hmd

play: midi
	timidity O0801.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O0801.wav

testplay: testmidi
	timidity O0801-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O0801-test.wav

clean:
	rm *.krn
	rm *.mid
