COM = "Kellner, Johann Ludwig"
OTL = "Fuga"
OMV = "2"
SCT = "O08:[C]"
SCA = "Rolf Dietrich Claus, Johann Peter Kellner - Studien zu Leben und Werk."
ENC = "Peter van Kranenburg \(peter@musical-style-recognition.net\)"
END = `getdatemodified 1.pk`

basename = O08C

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
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > O08C-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d O08C-temp.krn >> O08C.krn
	rm O08C-temp.krn
	proof O08C.krn
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
	yank -o ^= -r '$$-10-$$' O08C.krn > O08C-test.krn
	midi -u -q 90 < O08C-test.krn > O08C-test.hmd
	hmd2mid O08C-test.hmd
	rm O08C-test.hmd

midi: kernfile
	midi -u -q 90 < O08C.krn > O08C.hmd
	hmd2mid O08C.hmd
	rm O08C.hmd

play: midi
	timidity O08C.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O08C.wav

testplay: testmidi
	timidity O08C-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O08C-test.wav

clean:
	rm *.krn
	rm *.mid
