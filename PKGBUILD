# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Michal Bozon <michal.bozon__at__gmail.com>

pkgbase=python-yaml
pkgname=(python-yaml python2-yaml)
pkgver=5.4.1
pkgrel=1
pkgdesc='Python bindings for YAML, using fast libYAML library'
url='https://pyyaml.org/wiki/PyYAML'
arch=('x86_64' 'i686' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('MIT')
makedepends=('python' 'python2' 'libyaml' 'cython' 'cython2')
source=(PyYAML-${pkgver}.tar.gz::https://github.com/yaml/pyyaml/archive/${pkgver}.tar.gz)
sha512sums=('691e54fd9ca01fdc0dcb7de03ddd1970614d92a716c2437032999f9001f90a2ebbcc195a49bfdbe54da0f7a63178c83b02b05b18b5b1024127013f004d1f5997')

prepare() {
  # Force cython rebuild
  rm PyYAML-$pkgver/ext/_yaml.c

  cp -a PyYAML-$pkgver{,-py2}
}

build() {
  (
    cd PyYAML-$pkgver
    python setup.py --with-libyaml build
  )
  (
    cd PyYAML-$pkgver-py2
    python2 setup.py --with-libyaml build
  )
}

check() {
  (
    cd PyYAML-$pkgver
    python -B setup.py test
  )
  (
    cd PyYAML-$pkgver-py2
    python2 -B setup.py test
  )
}

package_python-yaml() {
  depends=('python' 'libyaml')

  cd PyYAML-$pkgver
  python setup.py  --with-libyaml install --prefix=/usr --root="${pkgdir}" -O1 --skip-build
  install -Dm 644 LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}
  install -Dm 644 CHANGES README -t "${pkgdir}"/usr/share/doc/${pkgname}
}

package_python2-yaml() {
  depends=('python2' 'libyaml')

  cd PyYAML-$pkgver-py2
  python2 setup.py --with-libyaml install --prefix=/usr --root="${pkgdir}" -O1 --skip-build
  install -Dm 644 LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}
  install -Dm 644 CHANGES README -t "${pkgdir}"/usr/share/doc/${pkgname}
}

# vim: ts=2 sw=2 et:
