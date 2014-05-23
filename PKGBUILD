# $Id: PKGBUILD 89670 2013-05-02 09:31:25Z lcarlier $
# Maintainer: Ionut Biru <ibiru@archlinux.org>
# Contributor: Pierre Schmitz <pierre@archlinux.de>

_pkgbasename=zlib
pkgname=lib32-$_pkgbasename
pkgver=1.2.8
pkgrel=1
pkgdesc='Compression library implementing the deflate compression method found in gzip and PKZIP (32-bit)'
arch=('x86_64')
license=('custom')
url="http://www.zlib.net/"
depends=('lib32-glibc' "$_pkgbasename")
makedepends=('gcc-multilib')
source=("http://zlib.net/current/zlib-${pkgver}.tar.gz")
md5sums=('44d667c142d7cda120332623eab69f40')

build() {
	export CC="gcc -m32"
	export CXX="g++ -m32"
	export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

	cd ${srcdir}/zlib-$pkgver
	./configure --prefix=/usr \
		--libdir=/usr/lib32
	make
}

check() {
	cd ${srcdir}/zlib-$pkgver
	make test
}

package() {
	cd ${srcdir}/zlib-$pkgver
	make install DESTDIR=${pkgdir}

	rm -rf "${pkgdir}"/usr/{include,share,bin}
	mkdir -p "$pkgdir/usr/share/licenses"
	ln -s $_pkgbasename "$pkgdir/usr/share/licenses/$pkgname"
}
