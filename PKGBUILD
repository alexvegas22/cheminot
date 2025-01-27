# Maintainer: Alex Vegas <v34l at proton dot me>
pkgname=cheminot
pkgver=2022.01.04
pkgrel=1
pkgdesc="Application de gestion d'horaire de l'ETS (license unknown)"
arch=('any')
url="https://cheminotjws.etsmtl.ca/"
license=('custom')
depends=('icedtea-web' 'java-runtime')
source=(
    "https://cheminotjws.etsmtl.ca/chemiNot.jnlp"
    "https://www.etsmtl.ca/assets/img/ets.svg"
)
sha256sums=(
    'c0a998ec111672d5fc61de69f6f252432dc575807e92b1ffa6eccff9aee088cd' 
    'SKIP'
)

package() {
    # Install the .jnlp file
    install -Dm644 "$srcdir/chemiNot.jnlp" "$pkgdir/usr/share/java/$pkgname/chemiNot.jnlp"

    # Install the icon
    install -Dm644 "$srcdir/ets.svg" "$pkgdir/usr/share/pixmaps/$pkgname.svg"

    # Create a desktop entry
    install -Dm644 /dev/stdin "$pkgdir/usr/share/applications/$pkgname.desktop" <<EOF
[Desktop Entry]
Name=Cheminot
Comment=$pkgdesc
Exec=javaws /usr/share/java/$pkgname/chemiNot.jnlp
Terminal=false
Type=Application
Categories=Education;Utility;Application;Java
EOF
Icon=/usr/share/pixmaps/$pkgname.png

    # Create a launcher script
    install -Dm755 /dev/stdin "$pkgdir/usr/bin/$pkgname" <<EOF
#!/bin/bash
javaws /usr/share/java/$pkgname/chemiNot.jnlp
EOF
}
