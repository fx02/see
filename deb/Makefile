#
#  LIVE see library
#
#  Created by Zvonimir Bužanić.
#  2024-11-11
#
# after building see copy this Makefile and debian directory to see-3.1.1424/deb/
# cd see-3.1.1424/deb/ then run "make deb"

VERSION=3.1
RELEASE=1424+1

NAME=see
ME=${NAME}-${VERSION}.${RELEASE}
ARCH:=${shell uname -m}
prefix?=/usr/local
libdir=${prefix}/lib
incdir=${prefix}/include
INSTALL?=install -c
INSTALL_DATA=${INSTALL} -m 644
LIBLIVEINCL=-I..
COMMENT=Live see library.

deb:
	rm -rf ${ME}
	mkdir -p ${ME}/${libdir}/pkgconfig/ ${ME}/${incdir}/see/ ${ME}/DEBIAN/
	${INSTALL} -m 775 debian/* ${ME}/DEBIAN/
	sed -i -e "s/%%VERSION%%/${VERSION}.${RELEASE}/g" ${ME}/DEBIAN/control
	${INSTALL} -m 755 ../include/see/*.* ${ME}/${incdir}/see/
	${INSTALL} -m 755 ../libsee/.libs/libsee.so.1.1.1 ${ME}/${libdir}/libsee.so.1.1.1
	${INSTALL} -m 755 ../libsee/.libs/libsee.so.1.1.1 ${ME}/${libdir}/libsee.so
	ln -s ${ME}/${libdir}/libsee.so ${ME}/${libdir}/libsee.so.1
	${INSTALL} -m 755 ../libsee/see.pc ${ME}/${libdir}/pkgconfig/see.pc
	dpkg-deb --build ${ME}

clean:
	rm -rf ${ME} ${ME}.deb
