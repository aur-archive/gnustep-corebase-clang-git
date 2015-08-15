# Maintainer: X0rg

pkgname=gnustep-corebase-clang-git
_gitname=gnustep-corebase
pkgver=370.b9be22c
pkgrel=3
pkgdesc="The GNUstep CoreBase Library is a library of general-purpose, non-graphical C objects, using Clang."
arch=('any')
url="http://www.gnustep.org/"
license=('GPL3' 'LGPL2.1')
groups=('gnustep-clang-git')
depends=('icu')
makedepends=('git' 'clang' 'gnustep-make-clang-git' 'gnustep-base-clang-git')
conflicts=('gnustep-corebase-git')
#source=('git://github.com/gnustep/gnustep-corebase.git') # The original GNUstep CoreBase Library
source=('git://github.com/LubosD/gnustep-corebase.git') # GNUstep CoreBase Library, designed for the Darling Project
md5sums=('SKIP')

pkgver() {
  cd $_gitname
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd $_gitname
  source /etc/profile.d/GNUstep.sh

  if [[ $(locale -a | grep french) == "french" ]];then msg2 "Exécute 'configure'..."
  else
    msg2 "Run 'configure'..."
  fi
  OBJCFLAGS=-fblocks CC=clang CXX=clang++ ./configure --prefix=/usr --sysconfdir=/etc/GNUstep

  if [[ $(locale -a | grep french) == "french" ]];then msg2 "Exécute 'make'..."
  else
    msg2 "Run 'make'..."
  fi
  make
}

# check() {
#   cd $_gitname
#   make check
# }

package() {
  cd $_gitname
  make DESTDIR="$pkgdir" install
}