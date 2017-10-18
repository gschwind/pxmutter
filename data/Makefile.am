desktopfiles_in_files = \
	pxmutter.desktop.in
desktopfilesdir = $(datadir)/applications
desktopfiles_DATA = $(desktopfiles_in_files:.desktop.in=.desktop)

%.desktop:%.desktop.in
	$(AM_V_GET) $(MSGFMT) --desktop --template $< -d $(top_srcdir)/po -o $@

xmldir = $(GNOME_KEYBINDINGS_KEYSDIR)
xml_DATA = \
        50-pxmutter-navigation.xml \
        50-pxmutter-system.xml \
        50-pxmutter-windows.xml

gschema_in_files = \
	org.gnome.pxmutter.gschema.xml.in	\
	org.gnome.pxmutter.wayland.gschema.xml.in
gsettings_SCHEMAS = $(gschema_in_files:.xml.in=.xml)

%.gschema.xml: %.gschema.xml.in Makefile
	$(AM_V_GEN) sed -e 's|@GETTEXT_DOMAIN[@]|$(GETTEXT_PACKAGE)|g' \
	$< > $@ || rm $@

@GSETTINGS_RULES@

convertdir = $(datadir)/GConf/gsettings
convert_DATA = pxmutter-schemas.convert

CLEANFILES = \
	$(desktopfiles_DATA) \
	$(gsettings_SCHEMAS)

EXTRA_DIST = \
	$(convert_DATA) \
	$(desktopfiles_in_files) \
	$(gschema_in_files) \
	$(xml_DATA)
