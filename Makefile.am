AUTOMAKE_OPTIONS = foreign
SUBDIRS = src
DIST_SUBDIRS = src
CLEANFILES = agl/navigation.wgt flite jtalk

bin_SCRIPTS = flite jtalk package
flite: flite.in
	sed -e 's,[@]datadir[@],$(datadir),g' $(srcdir)/flite.in > flite
	chmod +x flite

jtalk: jtalk.in
	sed -e 's,[@]datadir[@],$(datadir),g' -e 's,[@]exec_prefix[@],$(exec_prefix),g' $(srcdir)/jtalk.in > jtalk
	chmod +x jtalk

package:src/navi
	rm -f agl/navigation.wgt
	mkdir -p agl
	cp src/.libs/navi agl/
	cp $(srcdir)/agl/config.xml agl/
	wgtpkg-pack -f -o navigation.wgt agl/
