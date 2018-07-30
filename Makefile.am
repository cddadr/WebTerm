AM_CPPFLAGS          =
AM_CFLAGS            = -g -std=gnu99 -Wall
AM_LDFLAGS           = -g -lm

noinst_LTLIBRARIES   = libhttp.la                                             \
                       liblogging.la
noinst_DATA          = $(top_srcdir)/demo/demo.js
bin_PROGRAMS         = webtermd
man_MANS             = webtermd.1
noinst_HEADERS       = libhttp/http.h
dist_doc_DATA        = AUTHORS                                                \
                       COPYING                                                \
                       LICENSE                                                  \
                       ChangeLog                                              \
                       INSTALL                                                \
                       NEWS                                                   \
                       README                                                 \
                       TODO                                                   \
                       webterm/white-on-black.css                         \
                       webterm/black-on-white.css                         \
                       webterm/monochrome.css                             \
                       webterm/color.css
EXTRA_DIST           = INSTALL.Debian                                         \
                       README.Fedora                                          \
                       demo/beep.wav                                          \
                       demo/favicon.ico                                       \
                       demo/demo.html                                         \
                       demo/demo.js                                           \
                       demo/demo.jspp                                         \
                       demo/demo.xml                                          \
                       demo/enabled.gif                                       \
                       demo/keyboard.html                                     \
                       demo/keyboard.png                                      \
                       demo/styles.css                                        \
                       demo/print-styles.css                                  \
                       demo/vt100.js                                          \
                       demo/usercss-0.css                                     \
                       demo/usercss-1.css                                     \
                       demo/usercss-2.css                                     \
                       demo/usercss-3.css                                     \
                       etc-pam.d-webterm-example                          \
                       webterm/webtermd.man.in                        \
                       webterm/shell_in_a_box.js                          \
                       webterm/vt100.js                                   \
                       webterm/cgi-mode-example.sh                        \
                       debian/README                                          \
                       debian/README.available                                \
                       debian/README.enabled                                  \
                       debian/changelog                                       \
                       debian/compat                                          \
                       debian/control                                         \
                       debian/copyright                                       \
                       debian/docs                                            \
                       debian/rules                                           \
                       debian/webterm.default                             \
                       debian/webterm.dirs                                \
                       debian/webterm.init                                \
                       debian/webterm.install                             \
                       debian/webterm.postinst                            \
                       debian/webterm.postrm                              \
                       debian/source/format                                   \
                       debian/watch
LIBLOGGING_INCLUDES  = logging/logging.h                                      \
                       config.h
liblogging_la_SOURCES= logging/logging.c                                      \
                       $(LIBLOGGING_INCLUDES)
liblogging_la_LDFLAGS= -version 1:0:0

LIBHTTP_INCLUDES     = libhttp/hashmap.h                                      \
                       libhttp/trie.h                                         \
                       libhttp/httpconnection.h                               \
                       libhttp/server.h                                       \
                       libhttp/ssl.h                                          \
                       libhttp/url.h                                          \
                       config.h
libhttp_la_SOURCES   = libhttp/hashmap.c                                      \
                       libhttp/trie.c                                         \
                       libhttp/httpconnection.c                               \
                       libhttp/server.c                                       \
                       libhttp/ssl.c                                          \
                       libhttp/url.c                                          \
                       $(LIBHTTP_INCLUDES)                                    \
                       libhttp/libhttp.sym
libhttp_la_LDFLAGS   = -export-symbols  $(top_srcdir)/libhttp/libhttp.sym     \
                       -version 1:0:0

webtermd_SOURCES = webterm/webtermd.c                             \
                       webterm/externalfile.c                             \
                       webterm/externalfile.h                             \
                       webterm/launcher.c                                 \
                       webterm/launcher.h                                 \
                       webterm/privileges.c                               \
                       webterm/privileges.h                               \
                       webterm/service.c                                  \
                       webterm/service.h                                  \
                       webterm/session.c                                  \
                       webterm/session.h                                  \
                       webterm/usercss.c                                  \
                       webterm/usercss.h                                  \
                       webterm/cgi_root.html                              \
                       webterm/root_page.html                             \
                       webterm/vt100.jspp                                 \
                       webterm/shell_in_a_box.jspp                        \
                       webterm/styles.css                                 \
                       webterm/print-styles.css                           \
                       webterm/enabled.gif                                \
                       webterm/favicon.ico                                \
                       webterm/keyboard.png                               \
                       webterm/keyboard-layout.html                       \
                       webterm/beep.wav                                   \
                       config.h
BUILT_SOURCES        = webterm/beep.h                                     \
                       webterm/cgi_root.h                                 \
                       webterm/enabled.h                                  \
                       webterm/favicon.h                                  \
                       webterm/keyboard.h                                 \
                       webterm/keyboard-layout.h                          \
                       webterm/print-styles.h                             \
                       webterm/root_page.h                                \
                       webterm/shell_in_a_box.h                           \
                       webterm/shell_in_a_box.js                          \
                       webterm/styles.h                                   \
                       webterm/vt100.h                                    \
                       webterm/vt100.js


webtermd_LDADD   = liblogging.la                                          \
                       libhttp.la
webtermd_LDFLAGS = -static

symbolname           =                                                        \
  sed -e 's/.*\/\([^.]*\)[.].*/\1/'                                           \
      -e 't0'                                                                 \
      -e 's/\([^.]*\)[.].*/\1/'                                               \
      -e ':0'                                                                 \
      -e 's/$$/ aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ/'        \
      -e ':1'                                                                 \
      -e 's/\([^-_]*\)[-_]\([a-z]\)\([^ ]* .*\2\)\(.\)/\1\4\3\4/'             \
      -e 't1'                                                                 \
      -e 's/.\{53\}$$//'                                                      \
      -e 's/[-/.]/_/g'

libtool: $(LIBTOOL_DEPS)
	$(SHELL) ./config.status --recheck


${top_srcdir}/demo/demo.js: ${top_srcdir}/demo/beep.wav                       \
                            ${top_srcdir}/demo/demo.jspp                      \
                            ${top_srcdir}/demo/enabled.gif                    \
                            ${top_srcdir}/demo/favicon.ico                    \
                            ${top_srcdir}/demo/keyboard.html                  \
                            ${top_srcdir}/demo/keyboard.png                   \
                            ${top_srcdir}/demo/styles.css                     \
                            ${top_srcdir}/demo/print-styles.css               \
                            ${top_srcdir}/demo/vt100.js                       \
                            ${top_srcdir}/demo/usercss-0.css                  \
                            ${top_srcdir}/demo/usercss-1.css                  \
                            ${top_srcdir}/demo/usercss-2.css                  \
                            ${top_srcdir}/demo/usercss-3.css

${top_srcdir}/demo/beep.wav: ${top_srcdir}/webterm/beep.wav
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/enabled.gif: ${top_srcdir}/webterm/enabled.gif
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/favicon.ico: ${top_srcdir}/webterm/favicon.ico
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/keyboard.html: ${top_srcdir}/webterm/keyboard-layout.html
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/keyboard.png: ${top_srcdir}/webterm/keyboard.png
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/styles.css: ${top_srcdir}/webterm/styles.css
	@rm -f "$@"
	sed -e '/\[if DEFINES_COLORS\]/,/\[endif DEFINES_COLORS\]/d' "$?" >"$@"

${top_srcdir}/demo/print-styles.css: ${top_srcdir}/webterm/print-styles.css
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/usercss-0.css: ${top_srcdir}/webterm/white-on-black.css
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/usercss-1.css: ${top_srcdir}/webterm/black-on-white.css
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/usercss-2.css: ${top_srcdir}/webterm/monochrome.css
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/usercss-3.css: ${top_srcdir}/webterm/color.css
	@rm -f "$@"
	ln "$?" "$@"

${top_srcdir}/demo/vt100.js: ${top_srcdir}/webterm/vt100.js
	@rm -f "$@"
	ln "$?" "$@"

webtermd.1: ${top_srcdir}/webterm/webtermd.man.in                 \
		${top_srcdir}/config.h
	@src="${top_srcdir}/webterm/webtermd.man.in";                 \
	echo preprocess  "$$src" '>'"$@";                                     \
	if sed -e 's/^#define \([^ ]*\).*/\1/' -e t -e d config.h |           \
             grep 'HAVE_BIN_LOGIN' >/dev/null 2>&1; then                      \
	  sed -e '/^#ifndef  *HAVE_BIN_LOGIN$$/,/^#endif$$/d' "$$src";        \
	else                                                                  \
	  sed -e '/^#ifdef  *HAVE_BIN_LOGIN$$/,/^#endif$$/d' "$$src";         \
	fi |                                                                  \
	if [ `sed -e 's/^#define \([^ ]*\).*/\1/' -e t -e d config.h |        \
             egrep 'HAVE_OPENSSL_BIO_H|HAVE_OPENSSL_ERR_H|HAVE_OPENSSL_SSL_H'|\
             wc -l` -eq 3 ]; then                                             \
	  sed -e '/^#ifndef  *HAVE_OPENSSL$$/,/^#endif$$/d';                  \
	else                                                                  \
	  sed -e '/^#ifdef  *HAVE_OPENSSL$$/,/^#endif$$/d';                   \
	fi |                                                                  \
	if sed -e 's/^#define \([^ ]*\).*/\1/' -e t -e d config.h |           \
             grep 'HAVE_SECURITY_PAM_APPL_H' >/dev/null 2>&1; then            \
	  sed -e '/^#ifndef  *HAVE_PAM$$/,/^#endif$$/d';                      \
	else                                                                  \
	  sed -e '/^#ifdef  *HAVE_PAM$$/,/^#endif$$/d';                       \
	fi |                                                                  \
	if [ -n "${DPKGBUILD}" ]; then                                        \
	  sed -e '/^#ifndef  *DPKGBUILD$$/,/^#endif$$/d';                     \
	else                                                                  \
	  sed -e '/^#ifdef  *DPKGBUILD$$/,/^#endif$$/d';                      \
	fi |                                                                  \
	sed -e '/^#/d' >"$@"
	@out=`echo "$@" 2>/dev/null|sed -e 's/\.[^.]*$$/.ps/'`;               \
	man -Tps "./$@" >"$${out}" 2>/dev/null || rm -f "$${out}"

clean-local:
	-rm -rf webtermd.1                                                \
	        webtermd.ps
	-rm -rf debian/webterm                                            \
	        debian/webterm*.debhelper*                                \
	        debian/webterm.substvars                                  \
	        debian/tmp
	-rm -rf webterm/beep.h                                            \
	        webterm/cgi_root.h      				      \
	        webterm/enabled.h       				      \
	        webterm/favicon.h       				      \
	        webterm/keyboard.h      				      \
	        webterm/keyboard-layout.h				      \
	        webterm/print-styles.h  				      \
	        webterm/root_page.h     				      \
	        webterm/shell_in_a_box.h				      \
	        webterm/styles.h                                          \
	        webterm/vt100.h

.css.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"

.gif.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"

.png.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"

.html.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"


.ico.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"

.jspp.js:
	@echo preprocess "$<" "$@"
	@mkdir -p "`dirname "$@"`"
	sed -e "`sed -e 's/^#define *\([^ ]*\) *\(.*\)/\/^[^#]\/s\/\1\/\2 \\\\\/* \1 *\\\\\/\/g/' \
	             -e t                                                     \
	             -e d "$<"`"                                              \
	     -e "s/^#/\/\/ #/"                                                \
	     -e "s/VERSION/\"@VERSION@ (revision @VCS_REVISION@)\"/g"         \
	     "$<" >"$@"

.js.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"


.wav.h:
	@echo od "$<" '>'"$@"
	@mkdir -p "`dirname "$@"`"
	@{ sym="`echo "$<" | $(symbolname)`";                                 \
	   echo "static const char $${sym}Start[] =";                         \
	   od -vb "$<" | sed 's/[0-7]*/"/;s/ *$$/"/;/^""$$/d;s/  */\\/g';     \
	   echo ';';                                                          \
	   echo "static const int $${sym}Size ATTR_UNUSED ="                  \
	           "(int)sizeof($${sym}Start);";                              \
	 } >"$@"

