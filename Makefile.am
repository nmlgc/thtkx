AM_YFLAGS = -d -r all
AM_CFLAGS = -pedantic -Wall -Wextra
LDADD = @iconv_LIBS@
BUILT_SOURCES = parser.h parser.c lexer.c
bin_PROGRAMS = datpacker eclc ecldump thanm

if COMBINE
am_datpacker_OBJECTS = datpacker.o
am_eclc_OBJECTS = eclc.o
am_ecldump_OBJECTS = ecldump.o
am_thanm_OBJECTS = thanm.o

datpacker.o: $(datpacker_SOURCES)
	$(COMPILE) $(datpacker_CFLAGS) @combine_CFLAGS@ -c -o $@ $(filter %.c,$(datpacker_SOURCES))

eclc.o: $(eclc_SOURCES)
	$(COMPILE) $(eclc_CFLAGS) @combine_CFLAGS@ -c -o $@ $(filter %.c,$(eclc_SOURCES)) parser.c lexer.c

ecldump.o: $(ecldump_SOURCES)
	$(COMPILE) $(ecldump_CFLAGS) @combine_CFLAGS@ -c -o $@ $(filter %.c,$(ecldump_SOURCES))

thanm.o: $(thanm_SOURCES)
	$(COMPILE) $(thanm_CFLAGS) @combine_CFLAGS@ -c -o $@ $(filter %.c,$(thanm_SOURCES))
endif

util_SOURCES = \
	program.c \
	program.h \
	util.c \
	util.h

datpacker_CFLAGS = $(OPENMP_CFLAGS)
datpacker_SOURCES = \
	bits.c \
	bits.h \
	datpacker-th02.c \
	datpacker-th06.c \
	datpacker-th08.c \
	datpacker-th75.c \
	datpacker-th95.c \
	datpacker.c \
	datpacker.h \
	thcrypt.c \
	thcrypt.h \
	thdat.c \
	thdat.h \
	thlzss.c \
	thlzss.h \
	thrle.c \
	thrle.h \
	$(util_SOURCES)

eclc_SOURCES = \
	parser.h \
	lexer.l \
	parser.y \
	$(util_SOURCES)

ecldump_LDADD = $(LDADD) -lm
ecldump_SOURCES = \
	ecldump.c \
	instr.c \
	instr.h \
	$(util_SOURCES)

thanm_CFLAGS = $(libpng_CFAGS)
thanm_LDADD = $(LDADD) $(libpng_LIBS)
thanm_SOURCES = \
	thanm.c \
	thanm.h \
	$(util_SOURCES)