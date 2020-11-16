# Maintainer: Daan van Vugt <dvanvugt@ignitioncomputing.com>
pkgname=MDSplus
pkgver=7.96.14
pkgrel=1
pkgdesc="The MDSplus data management system (alpha from github)"
arch=('i686' 'x86_64')
url="https://github.com/MDSplus/mdsplus"
license=('MIT')
groups=()
depends=()
makedepends=('autoconf')
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
	../configure --prefix="$pkgdir/"
	make clean
	make
}

package() {
	cd "$srcdir/mdsplus-stable_release-${pkgver//[.]/-}"
	cd build
	make DESTDIR="$pkgdir/" install
	# remove a lot of superfluous stuff
	rm -Rf ChangeLog desktop epics etc home idl java local matlab MDSplus* nodejs php pixmaps pydevices python setup.csh setup.sh tdi trees xml
}
