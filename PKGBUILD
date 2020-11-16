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
install=()
source=("https://github.com/MDSplus/mdsplus/archive/stable_release-${pkgver//[.]/-}.tar.gz")
md5sums=('1add0a67f4380c6bbee35124dc3baf6a')

build() {
	cd "$srcdir/mdsplus-stable_release-${pkgver//[.]/-}"
	mkdir -p build
	cd build
	../configure --prefix="$pkgdir/"
	#autoreconf -fi -I m4
	#./configure --prefix="$pkgdir/"
	CFLAGS="-march=native -O2 -pipe -fcommon"
	CXXFLAGS="${CFLAGS}"
	make
}

package() {
	cd "$srcdir/mdsplus-stable_release-${pkgver//[.]/-}"
	make DESTDIR="$pkgdir/" install
	install -D "$pkgdir/include" include
}
