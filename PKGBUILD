# $Id: PKGBUILD 158103 2012-05-02 23:12:45Z foutrelis $
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>
# Contributor: Corrado Primier <bardo@aur.archlinux.org>

pkgname=xfce4-settings-reverse-multitap
_pkgname=xfce4-settings
pkgver=4.10.0
pkgrel=3
pkgdesc="Settings manager for xfce - With two-tap middle-click patch"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL2')
groups=('xfce4')
conflicts=('xfce4-settings')
depends=('exo' 'garcon' 'libxfce4ui' 'libnotify' 'libxklavier'
         'gnome-icon-theme' 'gtk-engines')
makedepends=('intltool')
optdepends=('libcanberra: for sound control')
source=(http://archive.xfce.org/src/xfce/$_pkgname/4.10/$_pkgname-$pkgver.tar.bz2
        xfce4-settings-xml-4.10.0.patch
        xfce4-settings-mouse-reverse-multitap-4.10.0.patch)
sha256sums=('0843f09ba9673f1d1b5df8dce4a17b63c183a9ba3be75fb6ef99a67fc8c1f77e'
            '78e68ef2cbf19760707ba24f3d57dd59fbf40a540d50d20e7cc62ba02196aaaa'
            '133233e53c0fa4ff90da0f675d451eeba24ef0bb35246934eb39828984b50bb3')

build() {
  cd "$srcdir/$_pkgname-$pkgver"

  patch -Np1 -i "$srcdir/xfce4-settings-mouse-reverse-multitap-4.10.0.patch"

  # enable gnome icon theme, clearlooks theme and font hinting by default
  # (taken from Fedora)
  patch -Np1 -i "$srcdir/xfce4-settings-xml-4.10.0.patch"

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --disable-static \
    --enable-xrandr \
    --enable-xcursor \
    --enable-libnotify \
    --enable-libxklavier \
    --enable-pluggable-dialogs \
    --enable-sound-settings \
    --disable-debug
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
