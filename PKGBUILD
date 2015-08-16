# Maintainer: hbdee <hbdee.arch@gmail.com>

pkgname=('mlock' 'mlock-gui')
pkgbase='mlock'
pkgver=0.7
pkgrel=1
pkgdesc="A fast native implementation of the minilock file format that can read and write encrypted miniLock files."
arch=('i686' 'x86_64')
url="http://andre-simon.de/doku/mlock/en/mlock.php"
license=('GPL3')
depends=('libsodium')
makedepends=('cmake' 'libsodium' 'qt5-quickcontrols') # You can remove 'qt5-quickcontrols' if you're not building the gui
install="mlock-gui.install"
source=(http://andre-simon.de/zip/$pkgbase-$pkgver.tar.bz2{,.asc}
	'mlock-gui.desktop')
sha256sums=('2a4b594d93868e74a7cb32efb5fd52ba3aa36fbeeba7d81efe39caac92d83d81'
            'SKIP'
	    '2c4f59a7b84762bcc0f479d7726fdd3d479e7e18e0f4ecb005cb11a5a9fcb3b1')
validpgpkeys=('B8C55574187F49180EDC763750FE0279D805A7C7')

build() {
  cd "$pkgbase-$pkgver"
  
  make
  make gui
}

package_mlock() {
  provides=('mlock')

  cd "$pkgbase-$pkgver"
  make DESTDIR="$pkgdir" install
}

package_mlock-gui() {
  pkgdesc="Qt5 GUI for mlock"
  depends=('mlock' 'qt5-quickcontrols')
  install="mlock-gui.install"
  provides=('mlock-gui')

  mkdir -p -m 755 ${pkgdir}/usr/share/applications/
  install -Dm644 mlock-gui.desktop ${pkgdir}/usr/share/applications/

  cd "$pkgbase-$pkgver"
  mkdir -p -m 755 ${pkgdir}/usr/bin
  make DESTDIR="$pkgdir" install-gui
}

# vim:set ts=2 sw=2 et:
