#https://github.com/planetarian/damecon-browser/releases/download/v0.11.0-beta/damecon-browser-linux-x64-0.11.0.zip
pkgname="damecon-browser-bin"
_pkgname="${pkgname%-bin}"
pkgver=0.11.0
pkgrel=1
pkgdesc='A minimal browser designed for playing Kantai Collection via KC3Kai'
arch=(
    'x86_64'
)
url='https://github.com/planetarian/damecon-browser'
licence=('GPL-3.0-only')
provides=(
    "${_pkgname}=${pkgver}"
)
makedepends=(unzip)
depends=()
provides=("${_pkgname}")
source=("${_pkgname}.desktop")
source_x86_64=("${_pkgname}-linux-x64-${pkgver}.zip::${url}/releases/download/v${pkgver}-beta/${_pkgname}-linux-x64-${pkgver}.zip")
sha256sums=('df12c5b2a66432fcd8ff2f87ee98d6b2293d9a264cbd599c5d407f6a7aa6cff8')
sha256sums_x86_64=('145a71c99d62fef305e7f4b3bd62812865af8f48472c473482d0d63c3b430e2d')

package() {
    install -d "${pkgdir}/opt/${_pkgname}-linux-x64"
    unzip "${srcdir}/${_pkgname}-linux-x64-${pkgver}.zip" -d "${pkgdir}/opt"
    install -d "${pkgdir}/usr/bin"
    ln -sf "${pkgdir}/opt/${_pkgname}-linux-x64/${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
    install -Dm644 "${srcdir}/${_pkgname}-linux-x64/resources/ui/damecon_icon_48.png" "${pkgdir}/usr/share/icons/hicolor/48x48/apps/damecon.png"
    install -Dm755 "${srcdir}/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
}
