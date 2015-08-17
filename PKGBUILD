# Maintainer: fuzzix <fuzzix@gmail.com>
# Contributor: David H. Bronke <whitelynx@gmail.com>
pkgname=sunvox-beta
_pkgname=sunvox
pkgver=1.7.3.beta2
pkgrel=2
pkgdesc="SunVox is a small, fast and powerful modular synthesizer with pattern based sequencer (tracker)"
arch=('i686' 'x86_64')
url="http://www.warmplace.ru/soft/sunvox/"
license=('custom')
depends=('alsa-lib' 'sdl')
changelog=changelog.txt
source=(http://www.warmplace.ru/soft/beta/${_pkgname}${pkgver}.zip sunvox.desktop sunvox.png)
md5sums=('85c45a5338afda9caf117dc87393877e'
         '38c832d4db1a291125b1f47684da871a'
         '8d059cce84b5565506aad73462f97abe')
provides=('sunvox')
conflicts=('sunvox')

build() {

  cd "${srcdir}"

  install -d ${pkgdir}/usr/{bin,share/{${_pkgname}/instruments/,${_pkgname}/examples/,${_pkgname}/docs/,applications/,icons/${_pkgname}}}
  # No license with this version...
  #install -Dm644 "${_pkgname}/docs/license.txt" "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"

  for _dir in instruments examples docs ; do
      cd "${srcdir}/${_dir}/"
      find . -type d -exec install -d "${pkgdir}/usr/share/${_pkgname}/${_dir}/"{} \;
      find . -type f -exec install -Dm644 {,"${pkgdir}/usr/share/${_pkgname}/${_dir}/"}{} \;
  done
  cd "${srcdir}"

  install -Dm644 "${_pkgname}.png" "${pkgdir}/usr/share/icons/${_pkgname}/"
  install -Dm644 "${_pkgname}.desktop" "${pkgdir}/usr/share/applications/"


  if [ "$CARCH" = "x86_64" ]; then
    _sunvox_bin="${_pkgname}/linux_x86_64/$_pkgname"
  else
    _sunvox_bin="${_pkgname}/linux_x86/$_pkgname"
    _sunvox_bin="${_pkgname}/linux_x86/${_pkgname}_lofi"
  fi

  install -Dm755 ${_sunvox_bin} "${pkgdir}/usr/bin/"

  mv "${pkgdir}/usr/share/${_pkgname}/docs" "${pkgdir}/usr/share/${_pkgname}/doc"

}

