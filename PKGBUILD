# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Jan Alexander Steffens <jan.steffens@gmail.com>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=libgnome-control-center
pkgver=3.12.1
pkgrel=1
pkgdesc='The Control Center for GNOME - shared library'
license=('GPL')
arch=('i686' 'x86_64')
depends=("gnome-control-center=${pkgver}")
makedepends=('gnome-doc-utils' 'intltool' 'docbook-xsl' 'gnome-common' 'modemmanager')
groups=('gnome')
url='http://www.gnome.org'
options=('!emptydirs')
source=("http://download.gnome.org/sources/${pkgname#lib}/${pkgver:0:4}/${pkgname#lib}-${pkgver}.tar.xz"
        'revert-drop-library.patch')
sha256sums=('5297d448eff0ec58f6c0ad9fbd1b94bed0a850496df0ee65571c0622b49c1582'
            '80c964ecef5abf230fa274bb39fdff22c0f75cd082ad393211b3933a1bfa43b4')

prepare() {
  cd ${pkgname#lib}-${pkgver}

  patch -Np1 -i ../revert-drop-library.patch
}

build() {
  cd ${pkgname#lib}-${pkgver}

  export ACLOCAL='/usr/bin/aclocal'
  export AUTOMAKE='/usr/bin/automake'
  ./configure --prefix='/usr' --sysconfdir='/etc' --localstatedir='/var' --libexecdir="/usr/lib/${pkgname#lib}" --disable-{silent-rules,static}
  make -j1
}

package() {
  cd ${pkgname#lib}-${pkgver}

  make DESTDIR="${pkgdir}" install
  rm -rf "${pkgdir}"/usr/{bin,lib/${pkgname#lib},share}
}

# vim: ts=2 sw=2 et:
