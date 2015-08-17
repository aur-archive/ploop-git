# Maintainer:   Lucky <archlinux@builds.lucky.li>

pkgname=ploop-git
_pkgname="${pkgname%-*}"
pkgver=1.12
pkgrel=1
pkgdesc="OpenVZ containers in a file user-space library and tools"
url="http://wiki.openvz.org/Download/ploop"
license=("GPL")
arch=("i686" "x86_64")
depends=("libxml2")
makedepends=("git")
conflicts=("${_pkgname}")
provides=("${_pkgname}")
source=("git://git.openvz.org/pub/${_pkgname}")
md5sums=("SKIP")

pkgver() {
  cd "${_pkgname}"
  git describe --always | sed "s|^${_pkgname}-||g;s|-|.|g"
}

build() {
  cd "${srcdir}/${_pkgname}"

  make
}

package() {
  cd "${srcdir}/${_pkgname}"

  make DESTDIR="${pkgdir}" \
    SBINDIR="/usr/bin" \
    USRSBINDIR="/usr/bin" \
    LIBDIR="/usr/lib" \
    install

  find "${pkgdir}" -type d -name .git -exec rm -r '{}' +
}
