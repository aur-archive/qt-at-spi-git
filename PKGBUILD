# Maintainer: Kyle <kyle@gmx.ca>
pkgname=qt-at-spi-git
_gitname="qtatspi"
pkgver=0.0 # determined from git origin
pkgrel=2
pkgdesc="A Qt plugin that bridges the QAccessible API’s to the AT-SPI 2 protocol, giving blind and visually impaired users access to qt applications"
arch=('i686' 'x86_64')
url="http://projects.kde.org/qtatspi"
license=('LGPL')
groups=()
depends=('at-spi2-core' 'qt4>=4.8' 'kdelibs>=4.8')
makedepends=('git' 'cmake' 'automoc4')
options=('!libtool')
install=
source=('git://anongit.kde.org/qtatspi'
  'qt-accessibility.sh')
md5sums=('SKIP'
  'f0c8551ed54f5d4e5daf7ddac9189aaa')

pkgver() {
  cd $_gitname
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd $_gitname
  cmake .
  make
}

package() {
  cd $_gitname
  make DESTDIR="$pkgdir/" install
  install -D -m755 "$srcdir/qt-accessibility.sh" "$pkgdir/etc/profile.d/qt-accessibility.sh"
} 
