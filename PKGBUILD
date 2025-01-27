# Maintainer: Your Name <your.email@example.com>
pkgname=chemiNot
pkgver=1.0
pkgrel=1
pkgdesc="Application de gestion d'horaire de l'ETS"
arch=('any')
url="https://cheminotjws.etsmtl.ca/"
license=('custom')  # Replace with the appropriate license
depends=('icedtea-web' 'java-runtime')  # Dependencies for running javaws
source=(
    "https://cheminotjws.etsmtl.ca/"
    "https://www.etsmtl.ca/assets/img/ets.svg"  # Optional: Application icon
)
sha256sums=(
    'SKIP'  # Replace with the actual checksum for your .jnlp file
    'SKIP'  # Replace with the actual checksum for your icon file
)

package() {
    # Install the .jnlp file
    install -Dm644 "$srcdir/chemiNot.jnlp" "$pkgdir/usr/share/java/$pkgname/chemiNot.jnlp"

    # Install the icon (optional)
    install -Dm644 "$srcdir/chemiNot.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"

    # Create a desktop entry
    install -Dm644 /dev/stdin "$pkgdir/usr/share/applications/$pkgname.desktop" <<EOF
[Desktop Entry]
Name=Cheminot
Comment=$pkgdesc
Exec=javaws /usr/share/java/$pkgname/chemiNot.jnlp
Icon=/usr/share/pixmaps/$pkgname.png
Terminal=false
Type=Application
Categories=Education;Utility;Application;Java
EOF

    # Create a launcher script (optional)
    install -Dm755 /dev/stdin "$pkgdir/usr/bin/$pkgname" <<EOF
#!/bin/bash
javaws /usr/share/java/$pkgname/chemiNot.jnlp
EOF
}
