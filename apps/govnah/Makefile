NAME     = govnah
TITLE    = Govnah
APP_ID   = org.webosinternals.${NAME}
SIGNER   = org.webosinternals
BLDFLAGS = -p
VERSION  = 0.2.5
TYPE	 = Application
CATEGORY = System Utilities
HOMEPAGE = http://www.webos-internals.org/wiki/Application:Govnah
ICON	 = http://www.webos-internals.org/images/5/59/Icon_WebOSInternals_Govnah.png
DESCRIPTION = Govnah is an application for controlling your CPU performance characteristics.  It also displays and graphs the true internal CPU temperature if you are using a custom kernel (such as the WebOS Internals Uber-Kernel) that contains the internal CPU temperature sensor code.
CHANGELOG = \
0.2.5: Now only stores the latest 5 minutes of temperature data in memory<br>\
0.2.4: Graphing updates<br>\
0.2.3: Initial full-screen graphs<br>\
0.2.2: Major graphing overhaul<br>\
0.1.4: Fixed governor-specific controls, and added loadavg to the service<br>\
0.1.3: Initial version that is able to make changes<br>\
0.1.2: Update current governor on activate<br>\
0.1.1: Display of current governor and frequency<br>\
0.1.0: Fleshed out all the service methods<br>\
0.0.7: Better graphing<br>\
0.0.6: Added periodic updating when the app is open<br>\
0.0.5: First Public Release
SCREENSHOTS = [\
\"http://www.webos-internals.org/images/b/ba/Govnah_ss1.png\",\
\"http://www.webos-internals.org/images/f/fb/Govnah_ss2.png\",\
\"http://www.webos-internals.org/images/4/44/Govnah_ss3.png\"\
]
LICENSE  = GPL v2 Open Source

SRC_GIT = git://git.webos-internals.org/applications/govnah.git

.PHONY: package
package: ipkgs/${APP_ID}_${VERSION}_arm.ipk ipkgs/${APP_ID}_${VERSION}_i686.ipk
include ../../support/package.mk

include ../../support/download.mk

.PHONY: unpack
unpack: build/.unpacked

build/.unpacked: ${DL_DIR}/${NAME}-${VERSION}.tar.gz
	rm -rf build
	mkdir -p build/src
	tar -C build/src -xf ${DL_DIR}/${NAME}-${VERSION}.tar.gz
	touch $@

.PHONY: build
build: build/.built-${VERSION}

build/.built-${VERSION}: build/arm.built build/i686.built
	touch $@

include ../../support/cross-compile.mk

build/%.built: build/.unpacked
	rm -rf build/$*
	( cd build/src/src ; \
	  ${MAKE} STAGING_DIR=${STAGING_DIR_$*} CC=${CROSS_COMPILE_$*}gcc \
	  clobber ${NAME} \
	)
	mkdir -p build/$*/usr/palm/applications/${APP_ID}
	cp -r build/src/* build/$*/usr/palm/applications/${APP_ID}/
	rm -rf build/$*/usr/palm/applications/${APP_ID}/src
	mkdir -p build/$*/usr/palm/applications/${APP_ID}/bin
	install -m 755 build/src/src/${NAME} build/$*/usr/palm/applications/${APP_ID}/bin/${APP_ID}
	touch $@

build/%/CONTROL/postinst:
	rm -f $@
	mkdir -p build/$*/CONTROL
	install -m 0775 build/src/control/postinst build/$*/CONTROL
	chmod ugo+x $@

build/%/CONTROL/prerm:
	rm -f $@
	mkdir -p build/$*/CONTROL
	install -m 0775 build/src/control/prerm build/$*/CONTROL
	chmod ugo+x $@

clobber::
	rm -rf build