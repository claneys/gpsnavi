AUTOMAKE_OPTIONS = foreign
SUBDIRS = src
DIST_SUBDIRS = src
CLEANFILES = package/navigation.wgt flite jtalk

bin_SCRIPTS = flite jtalk navigation.wgt
flite: flite.in
	sed -e 's,[@]datadir[@],$(datadir),g' $(srcdir)/flite.in > flite
	chmod +x flite

jtalk: jtalk.in
	sed -e 's,[@]datadir[@],$(datadir),g' -e 's,[@]exec_prefix[@],$(exec_prefix),g' $(srcdir)/jtalk.in > jtalk
	chmod +x jtalk

navigation.wgt:src/navi
	rm -rf package/
	mkdir -p package/root
	cp src/.libs/navi package/root/
	cp $(srcdir)/agl/config.xml package/root/
	cp $(srcdir)/agl/HMI_AppLauncher_Navigation_Active-01.png package/root/navigation.png
	wgtpkg-pack -f -o package/navigation.wgt package/root
