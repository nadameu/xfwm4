# Maintainer: Paulo R. Maurici Jr. <paulo at nadameu dot com dot br>
# Fork of https://aur.archlinux.org/packages/xfwm4-git 

pkgname=xfwm4-git-no-firefox-placement
pkgver=4.16.1+55+gaf609085b
pkgrel=1
pkgdesc="Xfce window manager (git version - patched to disable Firefox windows placement)"
arch=('i686' 'x86_64')
url="https://gitlab.xfce.org/xfce/xfwm4"
license=('GPL2')
groups=('xfce4')
depends=('libxfce4ui' 'libwnck3' 'libxpresent')
makedepends=('git' 'xfce4-dev-tools' 'exo')
provides=('xfwm4')
conflicts=('xfwm4')
source=("git+https://gitlab.xfce.org/xfce/xfwm4.git" "xfwm4-no-change-position-for-firefox.patch")
sha256sums=('SKIP' '6c0094b163a7aee307ef566b17779dafbe576cc6cce8392f3a14e5ef5d1f8741')

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

  patch --strip=1 --input="${srcdir}/xfwm4-no-change-position-for-firefox.patch"
}

# vim:set ts=2 sw=2 et:
