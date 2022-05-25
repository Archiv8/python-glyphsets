#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-glyphsets/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-glyphsets/discussions>

_langname="python"
_relname="glyphsets"

pkgname="${_langname}-${_relname}"
pkgver=0.3.1
pkgrel=1
pkgdesc="An API with data about glyph sets for many different scripts and languages"
arch=(
  any
)
url="https://github.com/googlefonts/glyphsets"
license=(
  "Apache"
)
depends=(
  "python"
  "python-defcon"
  "python-fonttools"
  "python-fs" # for fonttools[ufo]
  "python-glyphslib"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools"
  "python-wheel"
)
_tarname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_tarname}.tar.gz"
)
sha512sums=(
  "71a3ddea07878f81b72d485ce3342d338183b0f5780866917d757a26b40981a9d51734781f2dd6287d8f69bb77dabb3ffd5bca05f8b99974773e707a8f384c8c"
)

prepare() {
  cd "${_tarname}"
  # Upstream requires outdated setuptools_scm, work around
  sed -i -e '/_scm/d' setup.py

  echo "version = '${pkgver}'" > Lib/glyphsets/_version
}

build() {

  cd "${_tarname}"

  python -m build -wn
}

package() {

  cd "${_tarname}"

  python -m installer -d "$pkgdir" dist/*.whl
}
