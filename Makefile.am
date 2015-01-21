
if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl

SUBDIRS		= compat m7

INCLUDES	= $(PTHREAD_FLAGS) $(JANSSON_INCLUDES)
INCLUDES   += -I$(top_srcdir)/m7

bin_PROGRAMS	= minerd

dist_man_MANS	= minerd.1

minerd_SOURCES	= elist.h miner.h compat.h \
		  cpu-miner.c util.c \
		  sha2-old.c scrypt.c m7mhash.c \
		  m7/haval.c m7/keccak.c m7/ripemd.c m7/sha2.c m7/sha2big.c \
		  m7/sph_haval.h m7/sph_keccak.h m7/sph_ripemd.h \
		  m7/sph_sha2.h m7/sph_tiger.h m7/sph_whirlpool.h \
		  m7/tiger.c m7/whirlpool.c


minerd_LDFLAGS	= $(PTHREAD_FLAGS) -flto -fuse-linker-plugin -Ofast
minerd_LDADD	= @JANSSON_LIBS@ @PTHREAD_LIBS@ @WS2_LIBS@ -lgmp -lcurl -lm
minerd_CPPFLAGS = -Im7 -Ofast -march=native -flto -fuse-linker-plugin

