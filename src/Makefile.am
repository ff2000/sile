pkglib_LTLIBRARIES = justenoughharfbuzz.la justenoughlibtexpdf.la justenoughfontconfig.la fontmetrics.la
justenoughharfbuzz_la_SOURCES = justenoughharfbuzz.c
justenoughharfbuzz_la_LDFLAGS = -module -avoid-version -shared -no-undefined
justenoughharfbuzz_la_CFLAGS = $(HARFBUZZ_CFLAGS) $(FREETYPE_CFLAGS) $(LUA_INCLUDE)
justenoughharfbuzz_la_LIBADD = $(HARFBUZZ_LIBS) $(FREETYPE_LIBS) $(LUA_LIB)
to_copy = .libs/justenoughharfbuzz.@SHARED_LIB_EXT@

justenoughfontconfig_la_SOURCES = justenoughfontconfig.c
justenoughfontconfig_la_LDFLAGS = -module -avoid-version -shared -no-undefined
justenoughfontconfig_la_CFLAGS = $(FONTCONFIG_CFLAGS) $(LUA_INCLUDE)
justenoughfontconfig_la_LIBADD = $(FONTCONFIG_LIBS) $(LUA_LIB)
to_copy += .libs/justenoughfontconfig.@SHARED_LIB_EXT@

if APPKIT
pkglib_LTLIBRARIES += macfonts.la
macfonts_la_SOURCES = macfonts.m
macfonts_la_LDFLAGS = -module -avoid-version -shared -no-undefined
macfonts_la_OBJCFLAGS = $(FREETYPE_CFLAGS) $(LUA_INCLUDE)  -fmodules
macfonts_la_LIBADD = $(FREETYPE_LIBS) $(LUA_LIB)
to_copy += .libs/macfonts.@SHARED_LIB_EXT@
endif

justenoughlibtexpdf_la_SOURCES = justenoughlibtexpdf.c imagebbox.c
justenoughlibtexpdf_la_LDFLAGS = -module -avoid-version -shared -no-undefined
justenoughlibtexpdf_la_CFLAGS = -I.. $(LIBPNG_INCLUDES) $(ZLIB_INCLUDES) $(LIBPAPER_INCLUDES) $(LUA_INCLUDE) $(FREETYPE_CFLAGS)
justenoughlibtexpdf_la_LIBADD = ../libtexpdf/.libs/libtexpdf.la $(FREETYPE_LIBS) $(LIBPNG_LIBS) $(ZLIB_LIBS) $(LIBPAPER_LIBS) $(LUA_LIB)
to_copy += .libs/justenoughlibtexpdf.@SHARED_LIB_EXT@

fontmetrics_la_SOURCES = fontmetrics.c
fontmetrics_la_LDFLAGS = -module -avoid-version -shared -no-undefined
fontmetrics_la_CFLAGS = $(FREETYPE_CFLAGS) $(LUA_INCLUDE) $(HARFBUZZ_CFLAGS)
fontmetrics_la_LIBADD = $(FREETYPE_LIBS) $(LUA_LIB) $(HARFBUZZ_LIBS)
to_copy += .libs/fontmetrics.@SHARED_LIB_EXT@

if ICU
pkglib_LTLIBRARIES += justenoughicu.la
justenoughicu_la_SOURCES = justenoughicu.c
justenoughicu_la_LDFLAGS = -module -avoid-version -shared -no-undefined
justenoughicu_la_CFLAGS = -I.. $(ICU_CFLAGS) $(LUA_INCLUDE)
justenoughicu_la_LIBADD = $(ICU_LIBS) $(LUA_LIB)
to_copy += .libs/justenoughicu.@SHARED_LIB_EXT@

if LIBTHAI
pkglib_LTLIBRARIES += justenoughthai.la
justenoughthai_la_SOURCES = justenoughthai.c
justenoughthai_la_LDFLAGS = -module -avoid-version -shared -no-undefined
justenoughthai_la_CFLAGS = $(ICU_CFLAGS) $(LIBTHAI_CFLAGS) $(LUA_INCLUDE)
justenoughthai_la_LIBADD = $(ICU_LIBS) $(LIBTHAI_LIBS) $(LUA_LIB)
to_copy += .libs/justenoughthai.@SHARED_LIB_EXT@
endif

endif

all-local: $(pkglib_LTLIBRARIES)
	cp $(to_copy) ../core
