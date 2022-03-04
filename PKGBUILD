# Maintainer: Antoine Stevan
pkgname=st-a2ns-git
pkgver=5.0.r1176.8ceca6f
pkgrel=1
epoch=
pkgdesc="A heavily patched build of st."
arch=(x86_64)
url="https://github.com/a2n-s/st.git"
license=('GNU')
groups=()
depends=(nerd-fonts-mononoki)
makedepends=(git)
checkdepends=()
optdepends=()
provides=(st)
conflicts=(st)
replaces=()
backup=()
options=()
install=
changelog=
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
	cd "${_pkgname}"
  printf "5.0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd st
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd st
    mkdir -p ${pkgdir}/opt/${pkgname}
    cp -rf * ${pkgdir}/opt/${pkgname}
    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
