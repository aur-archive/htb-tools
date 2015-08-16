# Maintainer: kfgz <kfgz at interia dot pl>
# Contributor: Catalin Stoian <unixlust[at]unixlust.ath.cx>

pkgname=htb-tools
pkgver=0.3.0a
pkgrel=2
pkgdesc="a tool to help simplify the difficult process of bandwidth allocation"
arch=('i686' 'x86_64')
license=('GPL2')
url="http://htb-tools.skydevel.ro/"
backup=('etc/htb/eth0-qos.cfg')
makedepends=('flex')
#source=(http://htb-tools.skydevel.ro/HTB-tools-${pkgver}.tar.gz
source=(http://kfgz.mydevil.net/HTB-tools-${pkgver}.tar.gz
        http://unixlust.googlepages.com/bitops.h)
md5sums=('21ab90029ae491b05d5fa45eabaa1a4e'
         '962daca65477787ec8fd8c805aca0c70')
         
build() {
  cd "${srcdir}"/HTB-tools-${pkgver}
  mkdir -p "${srcdir}"/HTB-tools-${pkgver}/include/asm
  install -m644 "${srcdir}"/bitops.h "${srcdir}"/HTB-tools-${pkgver}/include/asm/bitops.h
  make
}

package() {
  cd "${srcdir}"/HTB-tools-${pkgver}
  install -dm755 "${pkgdir}"/{sbin,/usr/share/{doc/htb,man/man8},etc/{rc.d,htb}}
  install -m644 cfg/eth0-qos.cfg "${pkgdir}"/etc/htb
  install -m644 docs/HowTo/HTB-tools-howto.txt "${pkgdir}"/usr/share/doc/htb
  install -m644 INSTALL "${pkgdir}"/usr/share/doc/htb
  install -m755 sys/scripts/rc.htb "${pkgdir}"/etc/rc.d/htbd
  make OUT_DIR="${pkgdir}"/sbin MAN_DIR="${pkgdir}"/usr/share/man install
}