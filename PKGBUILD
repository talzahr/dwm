# Maintainer: Talzahr <echo 'a3JvemFyZXFAZ21haWwuY29tCg==' | base64 -d>
pkgname=dwm-talzahr
pkgver=6.2.r17.35ca59a
pkgrel=1
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
        'util.h'
        'README')
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
   make
}

check() {
   if [[ -e /usr/local/bin/dwm ]]; then
     cat <<EOF

Fatal: file 'dwm' already exists in /usr/local/bin!
       Remove or rename it to avoid conflict with the binary to be installed in /usr/bin.
       This was likely caused by a manual installation of dwm. Exiting.
EOF
      exit 1
   fi
}

package() {
   cd "${srcdir}"
   make DESTDIR="${pkgdir}" PREFIX="/usr" install
   install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
   install -Dm644 README "${pkgdir}/usr/share/doc/${_pkgname}/README"
   make clean
}
