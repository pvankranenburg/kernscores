kernfile: prekern
	timebase -t 32 1.krn > 1-32.krn
	timebase -t 32 2.krn > 2-32.krn
	timebase -t 32 3.krn > 3-32.krn
	timebase -t 32 4.krn > 4-32.krn
	timebase -t 32 5.krn > 5-32.krn
	paste 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn > bwv562-temp.krn
	rm 1-32.krn 2-32.krn 3-32.krn 4-32.krn 5-32.krn
	rid -d bwv562-temp.krn > bwv562.krn
	rm bwv562-temp.krn
	proof bwv562.krn

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
	yank -o ^= -r '$$-10-$$' bwv562.krn > bwv562-test.krn
	midi -u -q 90 < bwv562-test.krn > bwv562-test.hmd
	hmd2mid bwv562-test.hmd
	rm bwv562-test.hmd

midi: kernfile
	midi -u -q 90 < bwv562.krn > bwv562.hmd
	hmd2mid bwv562.hmd
	rm bwv562.hmd

play: midi
	timidity bwv562.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer bwv562.wav

testplay: testmidi
	timidity bwv562-test.mid
	/Applications/MPlayer\ OSX.app/Contents/Resources/External_Binaries/mplayer.app/Contents/MacOS/mplayer bwv562-test.wav

clean:
	rm *.krn
	rm *.mid
	rm *.wav
