_pkgname="python2-pymavlink"
pkgname="$_pkgname-git"
pkgver=r2277.5f31f68
pkgrel=2
pkgdesc="Python bindings for MAVLink micro air vehicle marshalling / communication library."
arch=('any')
license=('GPL3')
url='http://qgroundcontrol.org/mavlink/start'
depends=('python2-pyserial' 'python2-future' 'python2-lxml')
makedepends=('git' 'python2-setuptools')
provides=($_pkgname)
conflicts=($_pkgname)
source=("git+https://github.com/mavlink/mavlink.git")
sha256sums=('SKIP')

prepare() {
  cd "mavlink"
  git submodule init
  git submodule update
}

pkgver() {
  cd "mavlink/pymavlink"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "mavlink/pymavlink"
  python2 setup.py build
}

package() {
  cd "mavlink/pymavlink"
  python2 setup.py install --root="$pkgdir" --optimize=1
}
