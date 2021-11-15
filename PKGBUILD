# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Michal Bozon <michal.bozon__at__gmail.com>

pkgbase=python-yaml
pkgname=(python-yaml python2-yaml)
pkgver=5.4.1.1
pkgrel=1
pkgdesc='Python bindings for YAML, using fast libYAML library'
url='https://pyyaml.org/wiki/PyYAML'
arch=('x86_64' 'i686' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('MIT')
makedepends=('python-setuptools' 'python2-setuptools' 'libyaml' 'cython' 'cython2')
source=(pyyaml-${pkgver}.tar.gz::https://github.com/yaml/pyyaml/archive/${pkgver}.tar.gz)
sha512sums=('bcbe911fbef7e6e8ef8a76293593d4d792dbbf0931a2d031cdeacddf7064b69f958484217bc60d1b7614dcc83ef56cd5c0cd48a0339ab9add623ef70cb2d0a20')

prepare() {
  cp -a pyyaml-$pkgver{,-py2}
}

build() {
  (
    cd pyyaml-$pkgver
    python setup.py --with-libyaml build
  )
  (
    cd pyyaml-$pkgver-py2
    python2 setup.py --with-libyaml build
  )
}

check() {
  (
    cd pyyaml-$pkgver
    python -B setup.py test
  )
  (
    cd pyyaml-$pkgver-py2
    python2 -B setup.py test
  )
}

package_python-yaml() {
  depends=('python' 'libyaml')

  cd pyyaml-$pkgver
  python setup.py  --with-libyaml install --prefix=/usr --root="${pkgdir}" -O1 --skip-build
  install -Dm 644 LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}
  install -Dm 644 CHANGES README -t "${pkgdir}"/usr/share/doc/${pkgname}
}

package_python2-yaml() {
  depends=('python2' 'libyaml')

  cd pyyaml-$pkgver-py2
  python2 setup.py --with-libyaml install --prefix=/usr --root="${pkgdir}" -O1 --skip-build
  install -Dm 644 LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}
  install -Dm 644 CHANGES README -t "${pkgdir}"/usr/share/doc/${pkgname}
}

# vim: ts=2 sw=2 et:
