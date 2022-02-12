# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=plasma-firewall-git
pkgver=5.23.80_r546.gbe91b2b
pkgrel=1
pkgdesc='Control Panel for your system firewall'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(GPL LGPL)
depends=(systemsettings-git python)
makedepends=(extra-cmake-modules-git)
optdepends=('iproute2: netstat backend'
            'firewalld: firewalld backend'
            'ufw: ufw backend')
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DLIBEXEC_INSTALL_DIR=lib
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
