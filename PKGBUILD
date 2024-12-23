# Maintainer: Rodlan Isagani E. Bernabe <rodlanisagani@gmail.com>
pkgname=vktablet
pkgver=3.5.7
pkgrel=9
pkgdesc="Veikk tablet driver retrieved from official veikk website"
arch=('x86_64')
license=('GPL-3.0')
source=("https://veikk.com/image/catalog/Software/vktablet-${pkgver}-${pkgrel}.${CARCH}.tar.gz")
sha256sums=('b53d51557915ec9d043059f36d5eb87d3bcddc6e44e930048a69547570d75f66')

package() {
    tar -xzf "$srcdir/vktablet-${pkgver}-${pkgrel}.${CARCH}.tar.gz" -C "$srcdir"
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
