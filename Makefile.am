ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS =

light_guid = 52c2877e-44e1-11e5-8874-a62d1d5d46B0
darker_guid = 8a01dfcc-450f-11e5-909b-fb581d5d46b0
dark_guid = 03cb16aa-4675-11e5-b233-213b1d5d46b0

lighttempdir = $(top_builddir)/arc-firefox-theme-light
darkertempdir = $(top_builddir)/arc-firefox-theme-darker
darktempdir = $(top_builddir)/arc-firefox-theme-darker

extensiondir = $(DESTDIR)/$(libdir)/firefox/browser/extensions


EXTRA_DIST = ${top_srcdir}/README.md \
	     ${top_srcdir}/LICENSE \
	     ${top_srcdir}/arc-firefox-theme \
	     $(top_srcdir)/autogen.sh
NULL =


mkxpi:

if ENABLE_DARK
	cp -R $(top_srcdir)/arc-firefox-theme $(darktempdir)

	cp $(darktempdir)/chrome/browser/sass/browser-dark.css $(darktempdir)/chrome/browser/browser.css
	rm -rf $(darktempdir)/chrome/browser/sass
	rm $(darktempdir)/chrome/overrides.sh

	cd $(darktempdir) && \
		/usr/bin/zip -FS -r ../adapta-firefox-theme-$(VERSION).xpi *

	rm -rf $(darktempdir)
endif # ENABLE_DARK

install-data-local: mkxpi

	$(MKDIR_P) $(extensiondir)

if ENABLE_LIGHT
	/usr/bin/unzip -d $(extensiondir)/\{$(light_guid)\} $(top_builddir)/arc-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARKER
	/usr/bin/unzip -d $(extensiondir)/\{$(darker_guid)\} $(top_builddir)/arc-darker-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARK
	/usr/bin/unzip -d $(extensiondir)/\{$(dark_guid)\} $(top_builddir)/arc-dark-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT


uninstall:
if ENABLE_LIGHT
	rm -rf $(extensiondir)/\{$(light_guid)\}
endif # ENABLE_LIGHT

if ENABLE_DARKER
	rm -rf $(extensiondir)/\{$(darker_guid)\}
endif # ENABLE_DARKER

if ENABLE_DARK
	rm -rf $(extensiondir)/\{$(dark_guid)\}
endif # ENABLE_DARK

CLEANFILES = \
	arc-firefox-theme-$(VERSION).xpi \
	arc-darker-firefox-theme-$(VERSION).xpi \
	arc-dark-firefox-theme-$(VERSION).xpi
