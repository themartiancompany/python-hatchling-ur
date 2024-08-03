# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Santiago Torres-Arias <santiago @ usualplace>
# Contributor: Kaizhao Zhang <zhangkaizhao@gmail.com>

_py="python"
_pkg=hatchling
_Pkg="hatch"
pkgname="${_py}-${_pkg}"
pkgver=1.21.0
pkgrel=1
pkgdesc="A modern project, package, and virtual env manager (backend)"
arch=(
  'any'
)
url="https://github.com"
_ns="pypa"
url="${http}/${_ns}/${_Pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}"
  "${_py}-packaging"
  "${_py}-pathspec"
  "${_py}-pluggy"
  "${_py}-editables"
  "${_py}-trove-classifiers"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools"
  "${_py}-wheel"
)
_name=${pkgname/python-/}
source=(
  "${url}/archive/refs/tags/${_pkg}-v${pkgver}.tar.gz"
)
sha256sums=(
  'eb30344c551972b2c6830d7afb032031840fa13bb2dcf5a6bcbaa69be5ed7022'
)

build() {
  cd \
    "${srcdir}/${_Pkg}-${_pkg}-v${pkgver}"
  "${_py}" \
    -m build \
    --wheel \
    --no-isolation \
    backend
}

package() {
  cd \
    "${srcdir}/${_Pkg}-${_pkg}-v${pkgver}"
  "${_py}" \
    -m installer \
    --destdir="${pkgdir}" \
    backend/dist/*.whl
  install \
    -Dm644 \
    README.md \
    "${pkgdir}/usr/share/doc/${pkgname}/README.md"
  install \
    -Dm644 \
    backend/LICENSE.txt \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.txt"
}

# vim: ft=sh syn=sh et
