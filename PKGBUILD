# Maintainer: Michael R. Shannon <mrshannon.aerospace@gmail.com>
# Contributor: Michael R. Shannon <mrshannon.aerospace@gmail.com>

pkgname=mavtables-git
pkgver=r554.6744ac1
pkgrel=1
pkgdesc="A MAVLink router and firewall."
arch=('any')
url="https://github.com/shamuproject/mavtables"
license=('GPL')
depends=('boost')
makedepends=('git')
provides=("${pkgname%-*}")
conflicts=("${pkgname%-*}")
backup=('etc/mavtables.conf')
source=('mavtables::git+http://github.com/shamuproject/mavtables/#branch=master')
md5sums=('SKIP')

pkgver() {
  cd "${pkgname%-*}"
  ( set -o pipefail
    git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

build() {
  cd "${pkgname%-*}"
  make PREFIX=""
}

package() {
  cd "${pkgname%-*}"
  make PREFIX="" DESTDIR="$pkgdir" install
  install -Dm644 LICENSE.md "$pkgdir"/usr/share/licenses/${pkgname%-*}/LICENSE.md
}

# vim:set ts=2 sw=2 et:
