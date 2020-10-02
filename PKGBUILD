# Maintainer: Andrey Vihrov <andrey.vihrov at gmail.com>
# Contributor: Christian Hesse <mail@eworm.de>
# Contributor: Lex Black <autumn-wind at web dot de>
# Contributor: cute.tec@gmail.com

pkgname=xfwm4-git
pkgver=4.15.1+13+g5cce56d02
pkgrel=1
pkgdesc="Xfce window manager (git version)"
arch=('i686' 'x86_64')
url="https://gitlab.xfce.org/xfce/xfwm4"
license=('GPL2')
groups=('xfce4')
depends=('libxfce4ui' 'libwnck3' 'libxpresent')
makedepends=('git' 'xfce4-dev-tools' 'exo')
provides=('xfwm4')
conflicts=('xfwm4')
source=("git+https://gitlab.xfce.org/xfce/xfwm4.git" "xfwm4-no-smart-placement.patch")
sha256sums=('SKIP' '2601de1231e22baf999b347bfda6a3577285dc2e941926a10f689fa872acca67')

pkgver() {
  cd xfwm4
  git describe --long --match 'xfwm4-*' | sed 's/xfwm4-//;s/^\([[:digit:]]\)-/\1./;s/-/+/g'
}

build() {
  cd xfwm4

  ./autogen.sh \
    --prefix=/usr \
    --libexecdir=/usr/lib \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --disable-dependency-tracking \
    --disable-static \
    --enable-epoxy \
    --enable-startup-notification \
    --enable-xsync \
    --enable-render \
    --enable-randr \
    --enable-xpresent \
    --enable-compositor \
    --disable-debug
  make
}

package() {
  cd xfwm4

  make DESTDIR="${pkgdir}" install
}

prepare() {
  cd xfwm4

  patch --strip=1 --input="${srcdir}/xfwm4-no-smart-placement.patch"
}

# vim:set ts=2 sw=2 et:
