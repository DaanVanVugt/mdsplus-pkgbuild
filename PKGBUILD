# Maintainer: Daan van Vugt <dvanvugt@ignitioncomputing.com>
pkgname=MDSplus
pkgver=7.96.14
pkgrel=1
pkgdesc="The MDSplus data management system (stable from github)"
arch=('i686' 'x86_64')
url="https://github.com/MDSplus/mdsplus"
license=('MIT')
groups=()
depends=()
makedepends=('autoconf' 'jdk11-openjdk')
backup=()
options=()
install=
source=("https://github.com/MDSplus/mdsplus/archive/stable_release-${pkgver//[.]/-}.tar.gz")
md5sums=('1add0a67f4380c6bbee35124dc3baf6a')

build() {
	cd "$srcdir/mdsplus-stable_release-${pkgver//[.]/-}"
	mkdir -p build
	cd build
	export CFLAGS="-O2 -march=native -fcommon"
	export CXXFLAGS="${CFLAGS}"
	export FFLAGS='-fallow-argument-mismatch -fallow-invalid-boz'
	# TODO: switch to jdk11 with paths, jdk14 doesn't work yet
	../configure --prefix="$pkgdir/usr/"
	make clean
	make all
	make java/jtraverser
}

package() {
	cd "$srcdir/mdsplus-stable_release-${pkgver//[.]/-}"
	cd build
	make DESTDIR="$pkgdir/usr/" install
	# remove a lot of superfluous stuff
	# does not copy jtraverser and other tools
	install -D java/jtraverser/jTraverser.jar "$pkgdir/usr/java/classes/jTraverser.jar"
	cd "$pkgdir/usr"
	rm -Rf ChangeLog desktop epics etc home idl local matlab MDSplus* nodejs php pixmaps pydevices python setup.csh setup.sh tdi trees xml
}
