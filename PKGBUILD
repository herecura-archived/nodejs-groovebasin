# Maintainer: Jeremy "Ichimonji10" Audet <ichimonji10 at gmail dot com>
# Contributor: Andrew Kelley <superjoe30@gmail.com>
# Contributor: superjoe <superjoe30@gmail.com>
#
# makepkg warns "Package contains reference to $pkgdir". This is OK. See:
# https://github.com/andrewrk/groovebasin/issues/214

pkgname=nodejs-groovebasin
_pkgname="${pkgname#nodejs-}"
pkgver=1.1.0
pkgrel=1
pkgdesc='Music player server with a web-based user interface inspired by Amarok 1.4'
arch=(any)
url='http://groovebasin.com/'
license=(MIT)
depends=('nodejs' 'libgroove')
makedepends=('python2')
source=("https://github.com/andrewrk/groovebasin/archive/${pkgver}.tar.gz"
        groovebasin)

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  npm run build
}

package() {
  # install application
  local _npmdir="${pkgdir}/usr/lib/node_modules/"
  mkdir -p "${srcdir}/${_npmdir}"
  cd "${srcdir}/${_npmdir}"
  npm install --user root --global --prefix "${pkgdir}/usr" "${_pkgname}@${pkgver}"

  # install executable
  install -Dm755 "${srcdir}/groovebasin" "${pkgdir}/usr/bin/${_pkgname}"

  # install license
  install -Dm 644 "${srcdir}/${_pkgname}-${pkgver}/LICENSE" \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
sha256sums=('d1e0e207495b20cfc792d4748af2146043230bcaa8db8042a8a1684242a5f42d'
            'b121429dc1c6ed132a02f66c8b49424c46bf9a1e358d9fe91cf4b8093eaa4e28')
