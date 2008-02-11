#SConstruct

# needed imports
import sys
import os
import SCons.Util

PROGRAM_NAME = 'D1X-Rebirth'

# version number
D1XMAJOR = 0
D1XMINOR = 53

# installation path
PREFIX = '/usr/local/'
BIN_SUBDIR = 'bin/'
DATA_SUBDIR = 'share/games/d1x-rebirth/'
BIN_DIR = PREFIX + BIN_SUBDIR
DATA_DIR = PREFIX + DATA_SUBDIR

# command-line parms
sharepath = str(ARGUMENTS.get('sharepath', DATA_DIR))
debug = int(ARGUMENTS.get('debug', 0))
profiler = int(ARGUMENTS.get('profiler', 0))
sdl_only = int(ARGUMENTS.get('sdl_only', 0))
asm = int(ARGUMENTS.get('asm', 0))
editor = int(ARGUMENTS.get('editor', 0))
sdlmixer = int(ARGUMENTS.get('sdlmixer', 0))
arm = int(ARGUMENTS.get('arm', 0))
ipv6 = int(ARGUMENTS.get('ipv6', 0))
micro = int(ARGUMENTS.get('micro', 0))

if (micro > 0):
	D1XMICRO = micro
else:
	D1XMICRO = 0

VERSION_STRING = ' v' + str(D1XMAJOR) + '.' + str(D1XMINOR)
if (D1XMICRO):
	VERSION_STRING += '.' + str(D1XMICRO)

print '\n===== ' + PROGRAM_NAME + VERSION_STRING + ' =====\n'

# general source files
common_sources = [
'2d/2dsline.c',
'2d/bitblt.c',
'2d/bitmap.c',
'2d/box.c',
'2d/canvas.c',
'2d/circle.c',
'2d/disc.c',
'2d/font.c',
'2d/gpixel.c',
'2d/ibitblt.c',
'2d/line.c',
'2d/palette.c',
'2d/pcx.c',
'2d/pixel.c',
'2d/poly.c',
'2d/rect.c',
'2d/rle.c',
'2d/scalec.c',
'2d/tmerge.c',
'3d/clipper.c',
'3d/draw.c',
'3d/globvars.c',
'3d/instance.c',
'3d/interp.c',
'3d/matrix.c',
'3d/points.c',
'3d/rod.c',
'3d/setup.c',
'arch/sdl/event.c',
'arch/sdl/joy.c',
'arch/sdl/joydefs.c',
'arch/sdl/key.c',
'arch/sdl/mouse.c',
'arch/sdl/timer.c',
'arch/sdl/digi.c',
'arch/sdl/digi_audio.c',
'iff/iff.c',
'main/ai.c',
'main/aipath.c',
'main/digiobj.c',
'main/automap.c',
'main/bm.c',
'main/bmread.c',
'main/cntrlcen.c',
'main/collide.c',
'main/config.c',
'main/controls.c',
'main/credits.c',
'main/custom.c',
'main/d_conv.c',
'main/d_gamecv.c',
'main/dumpmine.c',
'main/effects.c',
'main/endlevel.c',
'main/fireball.c',
'main/fuelcen.c',
'main/fvi.c',
'main/game.c',
'main/gamefont.c',
'main/gamemine.c',
'main/gamesave.c',
'main/gameseg.c',
'main/gameseq.c',
'main/gauges.c',
'main/hash.c',
'main/hostage.c',
'main/hud.c',
'main/inferno.c',
'main/kconfig.c',
'main/kmatrix.c',
'main/laser.c',
'main/lighting.c',
'main/menu.c',
'main/mglobal.c',
'main/mission.c',
'main/morph.c',
'main/multi.c',
'main/multibot.c',
'main/multipow.c',
'main/netdrv.c',
'main/netdrv_udp.c',
'main/netlist.c',
'main/netpkt.c',
'main/network.c',
'main/newdemo.c',
'main/newmenu.c',
'main/object.c',
'main/paging.c',
'main/physics.c',
'main/piggy.c',
'main/playsave.c',
'main/polyobj.c',
'main/powerup.c',
'main/reorder.c',
'main/render.c',
'main/robot.c',
'main/scores.c',
'main/slew.c',
'main/snddecom.c',
'main/songs.c',
'main/state.c',
'main/switch.c',
'main/terrain.c',
'main/texmerge.c',
'main/text.c',
'main/titles.c',
'main/vclip.c',
'main/wall.c',
'main/weapon.c',
'mem/mem.c',
'misc/args.c',
'misc/compare.c',
'misc/dl_list.c',
'misc/error.c',
'misc/ignorecase.c',
'misc/strio.c',
'misc/strutil.c',
'texmap/ntmap.c',
'texmap/scanline.c'
]

# for editor
editor_sources = [
'editor/centers.c',
'editor/curves.c',
'editor/autosave.c',
'editor/eglobal.c',
'editor/ehostage.c',
'editor/elight.c',
'editor/eobject.c',
'editor/eswitch.c',
'editor/fixseg.c',
'editor/func.c',
'editor/group.c',
'editor/info.c',
'editor/kbuild.c',
'editor/kcurve.c',
'editor/kfuncs.c',
'editor/kgame.c',
'editor/khelp.c',
'editor/kmine.c',
'editor/ksegmove.c',
'editor/ksegsel.c',
'editor/ksegsize.c',
'editor/ktmap.c',
'editor/kview.c',
'editor/med.c',
'editor/meddraw.c',
'editor/medmisc.c',
'editor/medrobot.c',
'editor/medsel.c',
'editor/medwall.c',
'editor/mine.c',
'editor/objpage.c',
'editor/segment.c',
'editor/seguvs.c',
'editor/texpage.c',
'editor/texture.c',
'ui/button.c',
'ui/checkbox.c',
'ui/gadget.c',
'ui/icon.c',
'ui/inputbox.c',
'ui/keypad.c',
'ui/keypress.c',
'ui/keytrap.c',
'ui/lfile.c',
'ui/listbox.c',
'ui/menu.c',
'ui/menubar.c',
'ui/message.c',
'ui/mouse.c',
'ui/popup.c',
'ui/radio.c',
'ui/scroll.c',
'ui/ui.c',
'ui/uidraw.c',
'ui/userbox.c',
'ui/window.c'
]

# for linux
arch_linux_sources = [
'arch/linux/netdrv_ipx.c',
'arch/linux/netdrv_kali.c',
'arch/linux/mono.c',
'arch/linux/ukali.c'
]

# for windows
arch_win32_sources = [
'arch/win32/hmpfile.c',
'arch/win32/netdrv_ipx.c',
'arch/win32/mono.c',
]

# for Mac OS X
arch_macosx_sources = [
'arch/cocoa/SDLMain.m'
]

# for opengl
arch_ogl_sources = [
'arch/ogl/gr.c',
'arch/ogl/ogl.c',
'arch/ogl/sdlgl.c'
]

# for sdl
arch_sdl_sources = [
'arch/sdl/gr.c',
'texmap/tmapflat.c'
]

# assembler related
asm_sources = [
'2d/linear.asm',
'2d/tmerge_a.asm',
'maths/fix.asm',
'maths/rand.c',
'maths/vecmat.c',
'maths/vecmata.asm',
'texmap/tmap_ll.asm',
'texmap/tmap_flt.asm',
'texmap/tmapfade.asm',
'texmap/tmap_lin.asm',
'texmap/tmap_per.asm'
]

noasm_sources = [
'maths/fixc.c',
'maths/rand.c',
'maths/tables.c',
'maths/vecmat.c'
]

# SDL_mixer sound implementation
arch_sdlmixer = [
'misc/hmp2mid.c',
'arch/sdl/digi_mixer.c',
'arch/sdl/digi_mixer_music.c', 
'arch/sdl/jukebox.c'
]

if (sdlmixer == 1):
        arch_linux_sources += arch_sdlmixer
	arch_macosx_sources += arch_sdlmixer


# flags and stuff for all platforms
env = Environment(ENV = os.environ)
env.ParseConfig('sdl-config --cflags')
env.ParseConfig('sdl-config --libs')
env.Append(CPPFLAGS = ['-Wall', '-funsigned-char'])
env.Append(CPPDEFINES = [('D1XMAJOR', '\\"' + str(D1XMAJOR) + '\\"'), ('D1XMINOR', '\\"' + str(D1XMINOR) + '\\"')])
env.Append(CPPDEFINES = ['NMONO', 'NETWORK', 'HAVE_NETIPX_IPX_H', '__SDL__', 'SDL_AUDIO', '_REENTRANT'])
env.Append(CPPPATH = ['include', 'main', 'arch/include'])
generic_libs = ['SDL', 'physfs']
sdlmixerlib = ['SDL_mixer']

if sdlmixer:
	env.Append(CPPDEFINES = ['USE_SDLMIXER'])

if (D1XMICRO):
	env.Append(CPPDEFINES = [('D1XMICRO', '\\"' + str(D1XMICRO) + '\\"')])

# Get traditional compiler environment variables
if os.environ.has_key('CC'):
	env['CC'] = os.environ['CC']
if os.environ.has_key('CFLAGS'):
	env['CCFLAGS'] += SCons.Util.CLVar(os.environ['CFLAGS'])
if os.environ.has_key('CXX'):
	env['CXX'] = os.environ['CXX']
if os.environ.has_key('CXXFLAGS'):
	env['CXXFLAGS'] += SCons.Util.CLVar(os.environ['CXXFLAGS'])
if os.environ.has_key('LDFLAGS'):
	env['LINKFLAGS'] += SCons.Util.CLVar(os.environ['LDFLAGS'])

# windows or *nix?
if sys.platform == 'win32':
	print "compiling on Windows"
	osdef = '__WINDOWS__'
	osasmdef = 'win32'
	sharepath = ''
	env.Append(CPPDEFINES = ['__WINDOWS__'])
	env.Append(CPPPATH = ['arch/win32/include'])
	ogldefines = ['SDL_GL', 'OGL']
	common_sources += arch_win32_sources
	ogllibs = ''
	winlibs = ['glu32', 'wsock32', 'winmm', 'mingw32', 'SDLmain']
	libs = winlibs + generic_libs
	lflags = '-mwindows'
elif sys.platform == 'darwin':
	print "compiling on Mac OS X"
	osdef = '__APPLE__'
	env.Append(CPPDEFINES = ['__unix__'])
	no_asm = 1
	ogldefines = ['SDL_GL_VIDEO', 'OGL']
	common_sources += arch_macosx_sources
	ogllibs = ''
	libs = ''
	# Ugly way of linking to frameworks, but kreator has seen uglier
	lflags = '-framework Cocoa -framework SDL -framework physfs'
	if (sdl_only == 0):
		lflags += ' -framework OpenGL'
	if (sdlmixer == 1):
		print "including SDL_mixer"
		lflags += ' -framework SDL_mixer'
	sys.path += ['./arch/cocoa']
	VERSION = str(D1XMAJOR) + '.' + str(D1XMINOR)
	if (D1XMICRO):
		VERSION += '.' + str(D1XMICRO)
	env['VERSION_NUM'] = VERSION
	env['VERSION_NAME'] = PROGRAM_NAME + ' v' + VERSION
	import tool_bundle
else:
	print "compiling on *NIX"
	osdef = '__LINUX__'
	osasmdef = 'elf'
	sharepath += '/'
	env.Append(CPPDEFINES = ['__LINUX__'])
	env.Append(CPPPATH = ['arch/linux/include'])
	ogldefines = ['SDL_GL', 'OGL']
	common_sources += arch_linux_sources
	ogllibs = ['GL', 'GLU']
	libs = generic_libs
	lflags = '-L/usr/X11R6/lib'

# arm architecture?
if (arm == 1):
	asm = 0
	env.Append(CPPDEFINES = ['WORDS_NEED_ALIGNMENT'])
	env.Append(CPPFLAGS = ['-mstructure-size-boundary=8'])

# sdl or opengl?
if (sdl_only == 1):
	print "building with SDL"
	target = 'd1x-rebirth-sdl'
	env.Append(CPPDEFINES = ['SDL_VIDEO'])
	common_sources += arch_sdl_sources
else:
	print "building with OpenGL"
	target = 'd1x-rebirth-gl'
	env.Append(CPPDEFINES = ogldefines)
	common_sources += arch_ogl_sources
	libs += ogllibs

# SDL_mixer for sound? (*NIX only)
if (sdlmixer == 1) and (sys.platform != 'darwin'):
	print "including SDL_mixer"
	libs += sdlmixerlib

# debug?
if (debug == 1):
	print "including: DEBUG"
	env.Append(CPPFLAGS = ['-g'])
else:
	env.Append(CPPDEFINES = ['NDEBUG', 'RELEASE'])
	env.Append(CPPFLAGS = ['-O2'])

# profiler?
if (profiler == 1):
	env.Append(CPPFLAGS = ['-pg'])
	lflags += ' -pg'

# assembler code?
if (asm == 1) and (sdl_only == 1):
	print "including: ASSEMBLER"
	env.Append(CPPDEFINES = ['ASM_VECMAT'])
	Object(['texmap/tmappent.S', 'texmap/tmapppro.S'], AS='gcc', ASFLAGS='-D' + str(osdef) + ' -c ')
	env.Replace(AS = 'nasm')
	env.Append(ASCOM = ' -f ' + str(osasmdef) + ' -d' + str(osdef) + ' -Itexmap/ ')
	common_sources += asm_sources + ['texmap/tmappent.o', 'texmap/tmapppro.o']
else:
	env.Append(CPPDEFINES = ['NO_ASM'])
	common_sources += noasm_sources

#editor build?
if (editor == 1):
	env.Append(CPPDEFINES = ['EDITOR'])
	env.Append(CPPPATH = ['include/editor'])
	common_sources += editor_sources

# IPv6 compability?
if (ipv6 == 1):
	env.Append(CPPDEFINES = ['IPv6'])

print '\n'

env.Append(CPPDEFINES = [('SHAREPATH', '\\"' + str(sharepath) + '\\"')])
# finally building program...
env.Program(target=str(target), source = common_sources, LIBS = libs, LINKFLAGS = str(lflags))
if (sys.platform != 'darwin'):
	env.Install(BIN_DIR, str(target))
	env.Alias('install', BIN_DIR)
else:
	tool_bundle.TOOL_BUNDLE(env)
	env.MakeBundle(PROGRAM_NAME + '.app', target,
                       'free.d1x-rebirth', 'd1xgl-Info.plist',
                       typecode='APPL', creator='DCNT',
                       icon_file='arch/cocoa/d1x-rebirth.icns',
                       subst_dict={'d1xgl' : target},	# This is required; manually update version for Xcode compatibility
                       resources=[['English.lproj/InfoPlist.strings', 'English.lproj/InfoPlist.strings']])

# show some help when running scons -h
Help(PROGRAM_NAME + ', SConstruct file help:' +
	"""

	Type 'scons' to build the binary.
	Type 'scons install' to build (if it hasn't been done) and install.
	Type 'scons -c' to clean up.
	
	Extra options (add them to command line, like 'scons extraoption=value'):
	
	'sharepath=DIR'   (*NIX only) use DIR for shared game data. (default: /usr/local/share/games/d1x-rebirth)
	'sdl_only=1'      don't include OpenGL, use SDL-only instead
	'sdlmixer=1'      (*NIX only) use SDL_Mixer for sound (includes external music support)
	'asm=1'           use ASSEMBLER code (only with sdl_only=1, requires NASM and x86)
	'debug=1'         build DEBUG binary which includes asserts, debugging output, cheats and more output
	'profiler=1'      do profiler build
	'editor=1'        build editor !EXPERIMENTAL!
	'arm=1'           compile for ARM architecture
	'ipv6=1'          enables IPv6 copability (not compatible to non-IPv6 build)
	
	Default values:
	""" + ' sharepath = ' + DATA_DIR + """

	Some influential environment variables:
	  CC          C compiler command
	  CFLAGS      C compiler flags
	  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
                      nonstandard directory <lib dir>
                      <include dir>
	  CXX         C++ compiler command
	  CXXFLAGS    C++ compiler flags
        """)

#EOF
