kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn > O0807-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn
	rid -d O0807-temp.krn > O0807.krn
	rm O0807-temp.krn
	proof O0807.krn

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
	yank -o ^= -r '$$-10-$$' O0807.krn > O0807-test.krn
	midi -u -q 90 < O0807-test.krn > O0807-test.hmd
	hmd2mid O0807-test.hmd
	rm O0807-test.hmd

midi: kernfile
	midi -u -q 90 < O0807.krn > O0807.hmd
	hmd2mid O0807.hmd
	rm O0807.hmd

play: midi
	timidity O0807.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O0807.wav

testplay: testmidi
	timidity O0807-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer O0807-test.wav

clean:
	rm *.krn
	rm *.mid
