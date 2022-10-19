# vim:ts=4:sw=4:expandtab
# Maintainer: milaq <micha.laqua@gmail.com>
pkgname=dmenu-mlq
pkgver=5.2
pkgrel=1
pkgdesc="Generic menu for X, with user patches for milaq"
arch=('x86_64')
url="http://tools.suckless.org/dmenu/"
license=('MIT')
provides=('dmenu')
depends=('sh' 'libxinerama' 'libxft' 'freetype2')
conflicts=('dmenu')
source=("https://dl.suckless.org/tools/dmenu-$pkgver.tar.gz"
        "dmenu-lineheight.diff"
        "dmenu-hotkeys.diff")
sha256sums=('d4d4ca77b59140f272272db537e05bb91a5914f56802652dc57e61a773d43792'
            'SKIP'
            'SKIP')
prepare() {
    cd "$srcdir/dmenu-$pkgver"
    patch -p1 -i "$srcdir/dmenu-lineheight.diff"
    patch -p1 -i "$srcdir/dmenu-hotkeys.diff"
}

build() {
    cd "$srcdir/dmenu-$pkgver"
    make
}

package() {
    cd "$srcdir/dmenu-$pkgver"
    make DESTDIR="$pkgdir" PREFIX=/usr install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
