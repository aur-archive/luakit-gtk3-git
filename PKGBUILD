# Contributor: J. W. Birdsong <jwbirdsong AT gmail DOT com>
# Maintainer: moebiuseye <möëbïüs döt ëÿë ät gmäïl döt cöm>
# Maintainer: tuftedocelot@fastmail.fm

_pkgname=luakit
pkgname=${_pkgname}-gtk3-git
pkgver=1568
pkgrel=1
pkgdesc="A fast, small, webkit-gtk based browser extensible by Lua - gtkwebkit3 version"
arch=('i686' 'x86_64')
url="http://mason-larobina.github.com/luakit/"
license=('GPL3')
depends=('webkitgtk' 'lua51-filesystem' 'libunique3' 'luajit' 'help2man')
makedepends=('git' 'lua51')
source=("git://github.com/tuftedocelot/luakit.git")
provides=(luakit)
conflicts=('luakit')
_gitname="webkit3"
md5sums=("SKIP")

prepare() {
    cd "$srcdir/$_pkgname"
    sed -i '1s,lua,luajit,' build-utils/gentokens.lua
}

pkgver() {
    cd "$srcdir/$_pkgname"
    git checkout $_gitname
    git rev-list --count HEAD
}

build() {
  cd "${srcdir}/$_pkgname"
  git checkout $_gitname

  make PREFIX=/usr USE_LUAJIT=1 USE_UNIQUE=1 USE_GTK3=1 all
}

package() {
  cd "${srcdir}/$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install

  chmod -x "$pkgdir"/usr/share/pixmaps/luakit.png
}
