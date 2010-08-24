import sys

AddOption( '--platform',
  default=sys.platform,
  dest='platform',
  type='string',
  nargs=1,
  action='store',
  metavar=sys.platform,
  help='platform to build for (win32, darwin, darwin32, etc..)'
)

#################################################################
# Build contirb and configure env for linking against those libs
#################################################################
env = SConscript('contrib/Sconscript')


#################################################################
# Platform specific build settings for movid 
#################################################################
if GetOption('platform') == 'darwin32':
	print "Forcing 32bit build for platform=darwin32"
	env.PrependUnique(CCFLAGS   = ['-m32'])
	env.PrependUnique(LINKFLAGS = ['-m32'])



#################################################################
# Build Rule for libmovid
#################################################################
libmovid = env.Library('libmovid', [
	'src/moDaemon.cpp',
	'src/moDataGenericContainer.cpp',
	'src/moDataStream.cpp',
	'src/moFactory.cpp',
	'src/moLog.cpp',
	'src/moModule.cpp',
	'src/moOSC.cpp',
	'src/moPipeline.cpp',
	'src/moProperty.cpp',
	'src/moThread.cpp',
	'src/moUtils.cpp',
	'src/modules/moAmplifyModule.cpp',
	'src/modules/moBackgroundSubtractModule.cpp',
	'src/modules/moBlobFinderModule.cpp',
	'src/modules/moCalibrationModule.cpp',
	'src/modules/moCameraModule.cpp',
	'src/modules/moCannyModule.cpp',
	'src/modules/moCombineModule.cpp',
	'src/modules/moDilateModule.cpp',
	'src/modules/moDistanceTransformModule.cpp',
	'src/modules/moDumpModule.cpp',
	'src/modules/moErodeModule.cpp',
	'src/modules/moFiducialTrackerModule.cpp',
	'src/modules/moFingerTipFinderModule.cpp',
	'src/modules/moGreedyBlobTrackerModule.cpp',
	'src/modules/moGrayScaleModule.cpp',
	'src/modules/moHighpassModule.cpp',
	'src/modules/moHsvModule.cpp',
	'src/modules/moImageDisplayModule.cpp',
	'src/modules/moImageFilterModule.cpp',
	'src/modules/moImageModule.cpp',
	'src/modules/moInvertModule.cpp',
	'src/modules/moJustifyModule.cpp',
	'src/modules/moMaskModule.cpp',
	'src/modules/moMirrorImageModule.cpp',
	'src/modules/moPeakFinderModule.cpp',
	'src/modules/moRoiModule.cpp',
	'src/modules/moSmoothModule.cpp',
	'src/modules/moThresholdModule.cpp',
	'src/modules/moTuioModule.cpp',
	'src/modules/moTuio2Module.cpp',
	'src/modules/moVideoModule.cpp',
	'src/modules/moYCrCbThresholdModule.cpp' ],
)



#################################################################
# Build Rule for movid daemon
#################################################################
env.Program('movid', ['src/movid.cpp', 'contrib/cJSON/cJSON.c', libmovid])

