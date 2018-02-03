# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Joseph Murphy <air.jmurph@gmail.com>
pkgname=arm-linux-musleabihf
pkgver=0.1
pkgrel=1
epoch=0
pkgdesc="arm muslhf cross compiler"
arch=("x86_64")
url="https://github.com/richfelker/musl-cross-make"
license=("GPL")
groups=()
depends=()
makedepends=('wget>=1.19.3')
checkdepends=()
optdepends=()
provides=("arm-linux-musleabihf")
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
_gitcommit="030b83f3a808c0c969bd18d3d8f8e430df33e766"
_gitcommit_short="030b83f3"
source=("https://github.com/richfelker/musl-cross-make/archive/${_gitcommit}.zip")
noextract=()
md5sums=()
validpgpkeys=()
BUILDENV+=('!check')
MAKEFLAGS="-j$(nproc)"
CPPFLAGS=""
CFLAGS=""
CXXFLAGS=""

prepare() {
	cd "$srcdir"
	mv "musl-cross-make-$_gitcommit" "musl-cross-make-$_gitcommit_short"
}

build() {
	cd "$srcdir/musl-cross-make-${_gitcommit_short}"
  cp config.mak.dist config.mak
	TARGET=arm-linux-musleabihf make
}

check() {
	cd "$srcdir/musl-cross-make-${_gitcommit_short}"
	make -k check
}

package() {
	cd "$srcdir/musl-cross-make-${_gitcommit_short}"
  mkdir $pkgdir/usr
  mkdir $pkgdir/usr/bin
  mkdir $pkgdir/usr/lib
  mkdir $pkgdir/usr/include

	TARGET=arm-linux-musleabihf OUTPUT="/usr" make install
  cp $srcdir/musl-cross-make-$_gitcommit_short/output/usr $pkgdir/usr
}
md5sums=('b0f2cc1c42edde04a70c293c00d38be6')
