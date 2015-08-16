# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kio
pkgver=4.99.0
pkgrel=1
pkgdesc='KIO'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kio'
license=('LGPL')
depends=('krb5' 'solid' 'knotifications' 'kjobwidgets' 'kbookmarks'
         'qt5-script' 'libxslt' 'kwallet')
makedepends=('extra-cmake-modules' 'kdoctools')
groups=('kf5')
install=kio.install
source=("http://download.kde.org/unstable/frameworks/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('7eafc35cc0bcfb247b7871dce93c8b63')

prepare() {
  mkdir -p build
}

build() {
  export XDG_DATA_DIRS="/opt/kf5/share:$XDG_DATA_DIRS"

  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
#    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
