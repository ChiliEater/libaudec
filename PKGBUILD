# Maintainer: Sefa Eyeoglu <contact@scrumplex.net>

pkgname=libaudec
pkgver=0.3.4
pkgrel=1
pkgdesc="A library for reading and resampling audio files"
arch=('x86_64' 'i686')
url="https://git.sr.ht/~alextee/libaudec"
license=('AGPL3')
depends=("libsamplerate" "libsndfile")
makedepends=("meson" "ninja" "cmake")
source=("$pkgname-v$pkgver::https://github.com/zrythm/libaudec/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('9a53eb292804818ddd8b19f749f64257ca586b54672494daf138092858935115')

prepare() {
	cd "$pkgname-v$pkgver"

    rm -r subprojects
}

build() {
	cd "$pkgname-v$pkgver"

    meson build --buildtype=release --prefix=/usr \
      -Dtests=true
    ninja -C build
}

check() {
	cd "$pkgname-v$pkgver"

    ninja -C build test
}

package() {
	cd "$pkgname-v$pkgver"

    install -vDm 644 CHANGELOG.md README.md \
      -t "${pkgdir}/usr/share/doc/${pkgname}/"

    DESTDIR="${pkgdir}/" ninja -C build install
}
