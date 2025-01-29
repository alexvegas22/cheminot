# Maintainer: Alex Vegas <v34l at proton dot me>
pkgname=cheminot
pkgver=2022.01.04
pkgrel=2
pkgdesc="Application de gestion d'horaire de l'ETS (license unknown)"
arch=('any')
url="https://cheminotjws.etsmtl.ca/"
license=('custom')
depends=('icedtea-web' 'java-runtime' 'jre8-openjdk')
source=(
    "https://cheminotjws.etsmtl.ca/chemiNot.jnlp"
    "https://www.etsmtl.ca/assets/img/ets.svg"
)
sha256sums=(
    'c0a998ec111672d5fc61de69f6f252432dc575807e92b1ffa6eccff9aee088cd' 
    '24852c64b03d85e2987a3944882d5a5d81a1229ad0a5a1dfffd009b6c505e099'
)

package() {
    install -Dm644 "$srcdir/chemiNot.jnlp" "$pkgdir/usr/share/java/$pkgname/chemiNot.jnlp"
    install -Dm644 "$srcdir/ets.svg" "$pkgdir/usr/share/pixmaps/$pkgname.svg"
    install -Dm644 /dev/stdin "$pkgdir/usr/share/applications/$pkgname.desktop" <<EOF
[Desktop Entry]
Name=Cheminot
Comment=$pkgdesc
Exec=/usr/bin/$pkgname
Terminal=false
Type=Application
Categories=Education;Utility;Application;Java
EOF
    Icon=/usr/share/pixmaps/$pkgname.svg

    install -Dm755 /dev/stdin "$pkgdir/usr/bin/$pkgname" <<EOF
#!/bin/bash
JAVA_HOME=/usr/lib/jvm/java-8-openjdk
exec \$JAVA_HOME/bin/javaws /usr/share/java/$pkgname/chemiNot.jnlp
EOF
}
