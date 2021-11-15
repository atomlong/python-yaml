# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Michal Bozon <michal.bozon__at__gmail.com>

pkgname=python-yaml
pkgver=6.0
pkgrel=1
pkgdesc='Python bindings for YAML, using fast libYAML library'
url='https://pyyaml.org/wiki/PyYAML'
arch=('x86_64' 'i686' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('MIT')
depends=('python' 'libyaml')
makedepends=('python-setuptools' 'libyaml' 'cython')
source=(pyyaml-${pkgver}.tar.gz::https://github.com/yaml/pyyaml/archive/${pkgver}.tar.gz)
sha512sums=('cbcacc3560a035e2082867e93a9733f8660ea4c7f60573d07642f33a5453dcdc88d67299c3bcb97c27b843202a45d40de7444eb5e815bd4955129c9fc8ae04ad')

build() {
  (
    cd pyyaml-$pkgver
    python setup.py --with-libyaml build
  )
}

check() {
  (
    cd pyyaml-$pkgver
    python -B setup.py test
  )
}

package() {
  cd pyyaml-$pkgver
  python setup.py  --with-libyaml install --prefix=/usr --root="${pkgdir}" -O1 --skip-build
  install -Dm 644 LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}
  install -Dm 644 CHANGES README.md -t "${pkgdir}"/usr/share/doc/${pkgname}
}

# vim: ts=2 sw=2 et:
