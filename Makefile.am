AM_CFLAGS = \
	-Wall \
	-Wextra \
	-Werror \
	-Wno-unused-parameter \
	-Wno-missing-field-initializers

libexec_PROGRAMS = jelling
jelling_CFLAGS = $(AM_CFLAGS) @LIBSYSTEMD_CFLAGS@
jelling_LDADD = @LIBSYSTEMD_LIBS@

systemdsystemunit_DATA = jelling.service
modulesload_DATA = jelling.conf

EXTRA_DIST = jelling.service.in jelling.conf
CLEANFILES = $(systemdsystemunit_DATA)

%: %.in
	$(AM_V_GEN)$(SED) -e 's,@libexecdir\@,$(libexecdir),g' $< > $@
