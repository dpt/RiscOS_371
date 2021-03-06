# Makefile for Independent JPEG Group's software

# This makefile is for Microsoft C for MS-DOS, version 5.x.

# Read SETUP instructions before saying "make" !!

# Microsoft's brain-damaged version of make uses nonstandard syntax (a blank
# line is needed to terminate a command list) and it simply scans the rules
# in order, rather than doing a true dependency-tree walk.  Furthermore,
# expanded command lines can't exceed 128 chars (this is a DOS bug, not
# make's fault); so we can't just name all the objectfiles in the link steps.
# Instead we shove each objectfile into a library as it is made, and link
# from the library.  The objectfiles are also kept separately as timestamps.

# You may need to adjust these cc options:
CFLAGS=  /AS /I. /W3 /Oail /Gs   # NB: /Gs turns off stack oflo checks
LDFLAGS= /Fm /F 2000             # /F hhhh  sets stack size (in hex)
# In particular:
#   Add /DMSDOS if your compiler doesn't automatically #define MSDOS.
#   Add /DMEM_STATS to enable gathering of memory usage statistics.
# You might also want to add /G2 if you have an 80286, etc.


# source files (independently compilable files)
SOURCES= jbsmooth.c jcarith.c jccolor.c jcdeflts.c jcexpand.c jchuff.c \
        jcmain.c jcmaster.c jcmcu.c jcpipe.c jcsample.c jdarith.c jdcolor.c \
        jddeflts.c jdhuff.c jdmain.c jdmaster.c jdmcu.c jdpipe.c jdsample.c \
        jerror.c jquant1.c jquant2.c jfwddct.c jrevdct.c jutils.c jmemmgr.c \
        jrdjfif.c jrdgif.c jrdppm.c jrdrle.c jrdtarga.c jwrjfif.c jwrgif.c \
        jwrppm.c jwrrle.c jwrtarga.c
# virtual source files (not present in distribution file)
VIRTSOURCES= jmemsys.c
# system-dependent implementations of source files
SYSDEPFILES= jmemansi.c jmemname.c jmemnobs.c jmemdos.c jmemdos.h \
        jmemdosa.asm
# files included by source files
INCLUDES= jinclude.h jconfig.h jpegdata.h jversion.h jmemsys.h egetopt.c
# documentation, test, and support files
DOCS= README SETUP USAGE CHANGELOG cjpeg.1 djpeg.1 architecture codingrules
MAKEFILES= makefile.ansi makefile.unix makefile.manx makefile.sas \
        makefile.mc5 makefile.mc6 makcjpeg.lnk makdjpeg.lnk makefile.bcc \
        makcjpeg.lst makdjpeg.lst makefile.pwc makcjpeg.cf makdjpeg.cf \
        makljpeg.cf makefile.mms makefile.vms makvms.opt
OTHERFILES= ansi2knr.c ckconfig.c example.c
TESTFILES= testorig.jpg testimg.ppm testimg.gif testimg.jpg
DISTFILES= $(DOCS) $(MAKEFILES) $(SOURCES) $(SYSDEPFILES) $(INCLUDES) \
        $(OTHERFILES) $(TESTFILES)
# objectfiles common to cjpeg and djpeg
COMOBJECTS= jutils.obj jerror.obj jmemmgr.obj jmemsys.obj jmemdosa.obj
# compression objectfiles
CLIBOBJECTS= jcmaster.obj jcdeflts.obj jcarith.obj jccolor.obj jcexpand.obj \
        jchuff.obj jcmcu.obj jcpipe.obj jcsample.obj jfwddct.obj \
        jwrjfif.obj jrdgif.obj jrdppm.obj jrdrle.obj jrdtarga.obj
COBJECTS= jcmain.obj $(CLIBOBJECTS) $(COMOBJECTS)
# decompression objectfiles
DLIBOBJECTS= jdmaster.obj jddeflts.obj jbsmooth.obj jdarith.obj jdcolor.obj \
        jdhuff.obj jdmcu.obj jdpipe.obj jdsample.obj jquant1.obj \
        jquant2.obj jrevdct.obj jrdjfif.obj jwrgif.obj jwrppm.obj \
        jwrrle.obj jwrtarga.obj
DOBJECTS= jdmain.obj $(DLIBOBJECTS) $(COMOBJECTS)
# These objectfiles are included in libjpeg.lib
LIBOBJECTS= $(CLIBOBJECTS) $(DLIBOBJECTS) $(COMOBJECTS)


# inference rule used for all compilations except jcmain.c, jdmain.c
# notice that objectfile is also inserted into libjpeg.lib
.c.obj:
	cl $(CFLAGS) /c $*.c
	lib libjpeg -+$*.obj;

# inference rule for assembly code
.asm.obj:
	masm /mx $*;
	lib libjpeg -+$*.obj;


jbsmooth.obj : jbsmooth.c jinclude.h jconfig.h jpegdata.h

jcarith.obj : jcarith.c jinclude.h jconfig.h jpegdata.h

jccolor.obj : jccolor.c jinclude.h jconfig.h jpegdata.h

jcdeflts.obj : jcdeflts.c jinclude.h jconfig.h jpegdata.h

jcexpand.obj : jcexpand.c jinclude.h jconfig.h jpegdata.h

jchuff.obj : jchuff.c jinclude.h jconfig.h jpegdata.h

jcmain.obj : jcmain.c jinclude.h jconfig.h jpegdata.h jversion.h egetopt.c
	cl $(CFLAGS) /c $*.c

jcmaster.obj : jcmaster.c jinclude.h jconfig.h jpegdata.h

jcmcu.obj : jcmcu.c jinclude.h jconfig.h jpegdata.h

jcpipe.obj : jcpipe.c jinclude.h jconfig.h jpegdata.h

jcsample.obj : jcsample.c jinclude.h jconfig.h jpegdata.h

jdarith.obj : jdarith.c jinclude.h jconfig.h jpegdata.h

jdcolor.obj : jdcolor.c jinclude.h jconfig.h jpegdata.h

jddeflts.obj : jddeflts.c jinclude.h jconfig.h jpegdata.h

jdhuff.obj : jdhuff.c jinclude.h jconfig.h jpegdata.h

jdmain.obj : jdmain.c jinclude.h jconfig.h jpegdata.h jversion.h egetopt.c
	cl $(CFLAGS) /c $*.c

jdmaster.obj : jdmaster.c jinclude.h jconfig.h jpegdata.h

jdmcu.obj : jdmcu.c jinclude.h jconfig.h jpegdata.h

jdpipe.obj : jdpipe.c jinclude.h jconfig.h jpegdata.h

jdsample.obj : jdsample.c jinclude.h jconfig.h jpegdata.h

jerror.obj : jerror.c jinclude.h jconfig.h jpegdata.h

jquant1.obj : jquant1.c jinclude.h jconfig.h jpegdata.h

jquant2.obj : jquant2.c jinclude.h jconfig.h jpegdata.h

jfwddct.obj : jfwddct.c jinclude.h jconfig.h jpegdata.h

jrevdct.obj : jrevdct.c jinclude.h jconfig.h jpegdata.h

jutils.obj : jutils.c jinclude.h jconfig.h jpegdata.h

jmemmgr.obj : jmemmgr.c jinclude.h jconfig.h jpegdata.h jmemsys.h

jrdjfif.obj : jrdjfif.c jinclude.h jconfig.h jpegdata.h

jrdgif.obj : jrdgif.c jinclude.h jconfig.h jpegdata.h

jrdppm.obj : jrdppm.c jinclude.h jconfig.h jpegdata.h

jrdrle.obj : jrdrle.c jinclude.h jconfig.h jpegdata.h

jrdtarga.obj : jrdtarga.c jinclude.h jconfig.h jpegdata.h

jwrjfif.obj : jwrjfif.c jinclude.h jconfig.h jpegdata.h

jwrgif.obj : jwrgif.c jinclude.h jconfig.h jpegdata.h

jwrppm.obj : jwrppm.c jinclude.h jconfig.h jpegdata.h

jwrrle.obj : jwrrle.c jinclude.h jconfig.h jpegdata.h

jwrtarga.obj : jwrtarga.c jinclude.h jconfig.h jpegdata.h

jmemsys.obj : jmemsys.c jinclude.h jconfig.h jpegdata.h jmemsys.h

jmemdosa.obj : jmemdosa.asm


cjpeg.exe: $(COBJECTS)
	cl /Fecjpeg.exe jcmain.obj libjpeg.lib $(LDFLAGS)

djpeg.exe: $(DOBJECTS)
	cl /Fedjpeg.exe jdmain.obj libjpeg.lib $(LDFLAGS)
