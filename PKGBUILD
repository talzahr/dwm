# Maintainer: Talzahr <echo 'a3JvemFyZXFAZ21haWwuY29tCg==' | base64 -d>
pkgname=dwm-talzahr
pkgver=6.2.r15.aac8ba9
pkgrel=2
pkgdesc="Talzahr's custom patched DWM by Suckless.org"
arch=('x86_64')
url="https://github.com/talzahr/dwm"
license=('MIT')
depends=('libx11' 'libxinerama' 'libxft')
makedepends=('git' 'awk')
conflicts=('dwm')
source=('config.def.h'
        'config.mk'
        'drw.c'
        'drw.h'
        'dwm.1'
        'dwm.c'
        'LICENSE'
        'Makefile'
        'transient.c'
        'util.c'
        'util.h')
sha256sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')
_pkgname=dwm

pkgver() {
   cd "${srcdir}"
   local _dwmver=$(awk '/VERSION =/ {print $3}' < config.mk)
   echo "${_dwmver}.r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

build() {
   cd "${srcdir}"
   make clean
}

package() {
   cd "${srcdir}"
   make DESTDIR="${pkgdir}" PREFIX=/usr install
   install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
