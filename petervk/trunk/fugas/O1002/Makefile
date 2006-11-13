kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > O1002-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d O1002-temp.krn > O1002.krn
	rm O1002-temp.krn
	proof O1002.krn

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
	yank -o ^= -r '$$-10-$$' O1002.krn > O1002-test.krn
	midi -u -q 90 < O1002-test.krn > O1002-test.hmd
	hmd2mid O1002-test.hmd
	rm O1002-test.hmd

midi: kernfile
	midi -u -q 90 < O1002.krn > O1002.hmd
	hmd2mid O1002.hmd
	rm O1002.hmd

play: midi
	timidity O1002.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O1002.wav

testplay: testmidi
	timidity O1002-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O1002-test.wav

clean:
	rm *.krn
	rm *.mid
