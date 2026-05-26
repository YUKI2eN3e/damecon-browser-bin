#https://github.com/planetarian/damecon-browser/releases/download/v0.11.0-beta/damecon-browser-linux-x64-0.11.0.zip
_pkgname="damecon-browser"
pkgname="${_pkgname}-bin"
pkgver=0.11.3
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
_hook='clear_damecon_gpucache_on_update.hook'
source=(
    "${_pkgname}.desktop"
    "${_hook}"
)
source_x86_64=("${_pkgname}-linux-x64-${pkgver}.zip::${url}/releases/download/v${pkgver}-beta/${_pkgname}-linux-x64-${pkgver}.zip")
sha256sums=(
    'df12c5b2a66432fcd8ff2f87ee98d6b2293d9a264cbd599c5d407f6a7aa6cff8'
    '145fddea696b5cef0e6032da93254b7ba3f7bd98c663d0540db858be5718b011'
)
sha256sums_x86_64=('8eb34c6056918a56de81d98b3771033db7a53f046b93cb6bb513b11fe6e590e6')

package() {
    # install damecon
    install -dm777 "${pkgdir}/opt/${_pkgname}-linux-x64"
    unzip "${srcdir}/${_pkgname}-linux-x64-${pkgver}.zip" -d "${pkgdir}/opt"
    chmod 777 "/opt/${_pkgname}-linux-x64"
    install -d "${pkgdir}/usr/bin"
    ln -sf "/opt/${_pkgname}-linux-x64/${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
    # install the desktop entry (startmenu entry)
    install -Dm644 "${srcdir}/${_pkgname}-linux-x64/resources/ui/damecon_icon_48.png" "${pkgdir}/usr/share/icons/hicolor/48x48/apps/damecon.png"
    install -Dm755 "${srcdir}/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    # install the pacman hook
    install -Dm644 "${srcdir}/${_hook}" "${pkgdir}/usr/share/libalpm/hooks/${_hook}"
}
