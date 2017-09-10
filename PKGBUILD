# Maintainer: Alad Wenter <alad@archlinux.info>
# Contributor: Daniel Landau <daniel+aur@landau.fi>
# Contributor: sekret, mail=$(echo c2VrcmV0QHBvc3Rlby5zZQo= | base64 -d)
# Contributor: mmm
# Contributor: bslackr <brendan at vastactive dot com>
# Contributor: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Thomas Dziedzic < gostrc at gmail >
pkgname=lightspark-git
pkgver=0.8.0.r45.g06d58822
pkgrel=1
pkgdesc="An open source flash player implementation"
arch=('i686' 'x86_64')
url="http://lightspark.sourceforge.net"
license=('LGPL3')
depends=('gtk2' 'boost-libs' 'glew' 'ffmpeg' 'rtmpdump' 'sdl2_mixer' 'glibmm')
makedepends=('git' 'cmake' 'nasm' 'llvm' 'boost')
optdepends=('gnash-gtk: Gnash fallback support')
provides=('lightspark')
conflicts=('lightspark')
source=("$pkgname::git+https://github.com/lightspark/lightspark.git")
md5sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --long --tags | sed -r 's/^lightspark-//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$pkgname"
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCOMPILE_PLUGIN=1 \
    -DCMAKE_BUILD_TYPE=Release \
    -DGNASH_EXE_PATH=/usr/bin/gtk-gnash \
    -DAUDIO_BACKEND="pulseaudio sdl"
  make
}

package() {
  cd "$pkgname"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
