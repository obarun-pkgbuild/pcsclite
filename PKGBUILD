# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/tree/trunk?h=packages/pcsclite
# 						Maintainer: Giovanni Scafora <giovanni@archlinux.org>
# 						Contributor: Daniel Plaza <daniel.plaza.espi@gmail.com>

pkgname=pcsclite
pkgver=1.8.23
_dlid=4235
pkgrel=3
pkgdesc="PC/SC Architecture smartcard middleware library"
arch=(x86_64)
url="https://alioth.debian.org/projects/pcsclite/"
license=('BSD')
depends=('python')
makedepends=('pkg-config')
options=('!docs')
source=("https://alioth.debian.org/frs/download.php/file/${_dlid}/pcsc-lite-${pkgver}.tar.bz2")
sha256sums=('5a27262586eff39cfd5c19aadc8891dd71c0818d3d629539bd631b958be689c9')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal


build() {
  cd "${srcdir}/pcsc-lite-${pkgver}"


  ./configure --prefix=/usr \
              --sbindir=/usr/bin \
              --sysconfdir=/etc \
              --enable-filter \
              --enable-ipcdir=/run/pcscd \
              --enable-libudev \
              --enable-usbdropdir=/usr/lib/pcsc/drivers \
              --with-systemdsystemunitdir=no \
              --disable-libsystemd

  make
}

package() {
  cd "${srcdir}/pcsc-lite-${pkgver}"

  make DESTDIR="${pkgdir}" install

  install -D -m644 ${srcdir}/pcsc-lite-${pkgver}/COPYING ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  install -d ${pkgdir}/usr/lib/pcsc/drivers
}
