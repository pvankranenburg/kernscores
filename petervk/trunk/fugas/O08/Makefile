kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > O08-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d O08-temp.krn > O08.krn
	rm O08-temp.krn
	proof O08.krn

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
	yank -o ^= -r '$$-10-$$' O08.krn > O08-test.krn
	midi -u -q 90 < O08-test.krn > O08-test.hmd
	hmd2mid O08-test.hmd
	rm O08-test.hmd

midi: kernfile
	midi -u -q 90 < O08.krn > O08.hmd
	hmd2mid O08.hmd
	rm O08.hmd

play: midi
	timidity O08.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O08.wav

testplay: testmidi
	timidity O08-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O08-test.wav

clean:
	rm *.krn
	rm *.mid
