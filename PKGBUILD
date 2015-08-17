# Maintainer: Antonio Rojas
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Nick B <Shirakawasuna at gmail _dot_com>

pkgname=partitionmanager
pkgver=1.1.0
pkgrel=1
pkgdesc="A KDE utility that allows you to manage disks, partitions, and file systems"
arch=('i686' 'x86_64')
url="http://kde.org/applications/system/kdepartitionmanager/"
license=('GPL2')
depends=('kdebase-runtime' 'parted')
makedepends=('cmake' 'automoc4')
optdepends=('e2fsprogs: ext2/3/4 support'
	    'xfsprogs: XFS support'
	    'jfsutils: JFS support'
	    'reiserfsprogs: Reiser support'
	    'ntfsprogs: NTFS support'
	    'dosfstools: FAT32 support')
install=$pkgname.install
source=("http://download.kde.org/stable/$pkgname/$pkgver/src/$pkgname-$pkgver.tar.xz")
md5sums=('4a752c250fc5c98e22aba1d2ea309bec')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DENABLE_UDISKS2=ON \
    -DQT_QMAKE_EXECUTABLE=qmake-qt4
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
