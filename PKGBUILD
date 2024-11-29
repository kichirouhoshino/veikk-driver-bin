# Maintainer: Rodlan Isagani E. Bernabe <rodlanisagani@gmail.com>
pkgname=vktablet
pkgver=3.5.6
pkgrel=2
pkgdesc="Veikk tablet driver retrieved from official veikk website"
arch=('x86_64')
license=('GPL-3.0')
source=("https://veikk.com/image/catalog/Software/vktablet-${pkgver}-${pkgrel}.${CARCH}.tar-1.gz")
sha256sums=('a54670d517ad6a81f15c95f13f24ebfde427e267987d8f27b30e886d727c1e84')

package() {
    tar -xzf "$srcdir/vktablet-${pkgver}-${pkgrel}.${CARCH}.tar-1.gz" -C "$srcdir"
    cd "$srcdir/vktablet-${pkgver}-${pkgrel}.${CARCH}"
    app=vktablet
    appdir="$pkgdir/usr/lib/vktablet"
    mkdir -p "$appdir"
    cp ./usr/lib/vktablet/* $appdir -R
    find etc -type f | while IFS= read -r relpath; do
        install -Dm644 "$relpath" "$pkgdir/$relpath"
    done
    find lib -type f | while IFS= read -r relpath; do
        install -Dm644 "$relpath" "$pkgdir/usr/$relpath"
    done
    find usr/share -type f | while IFS= read -r relpath; do
        install -Dm644 "$relpath" "$pkgdir/$relpath"
    done
    chmod 777 `find $appdir/conf -type d`
    chmod 666 `find $appdir/conf -type f`
    chmod +x $appdir/$app
    mkdir -p "$pkgdir/usr/bin"
    ln -s $appdir/$app "$pkgdir/usr/bin/$app"
}
