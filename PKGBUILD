# Maintainer: Pieter Joost van de Sande <pj@born2code.net>
pkgname=owncast
pkgver=0.0.12
pkgrel=1
pkgdesc='Take control over your live stream video by running it yourself. Streaming + chat out of the box.'
url='https://github.com/owncast/owncast'
arch=('any')
license=('MIT')
makedepends=('git' 'go')
depends=()
source=("${url}/archive/v${pkgver}.tar.gz")
sha256sums=('9a6742f08a0f83168733e3536241cbe5d26b520834712f5ca7e766720f8bb031')

build() {
  cd "${pkgname}-${pkgver}"
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build -o ${pkgname} -ldflags "-extldflags ${LDFLAGS} -s -w -X main.version=${pkgver}"
}

package() {
  cd "${pkgname}-${pkgver}"
  install -Dm755 $pkgname "$pkgdir"/usr/bin/$pkgname
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
# vim: ft=sh ts=2 sw=2 et
