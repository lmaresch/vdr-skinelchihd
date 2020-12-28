# This PKGBUILD could be part of the VDR4Arch project [https://github.com/vdr4arch]

pkgname=vdr-skinelchihd
pkgver=0.5.0
_vdrapi=2.4.6
pkgrel=3
pkgdesc="Das Elchi HD Skin ist die Weiterentwicklung des skinElchi-Plguins um dem VDR ein frischeres Design zu geben und die Möglichkeiten neuerer VDR-Versionen auszunutzen. U.a. unterstützt der Skin jetzt TrueColor und SVG-Kanal-Logos und ist Multithreading-fähig für Hintergrundtasks wie Scrolling oder Einlesen der EPG-Bilder."
url="http://firefly.vdr-developer.org/skinelchihd/index.html"
arch=('x86_64' 'i686' 'arm' 'armv6h' 'armv7h')
license=('AGPL3')
depends=("vdr-api=${_vdrapi}")
optdepends=('ttf-vdrsymbols')
_plugname=${pkgname//vdr-/}
source=("vdr-plugin-${_plugname}::http://firefly.vdr-developer.org/skinelchihd/vdr-${plugname}-${pkgver}.tar.bz2"
        "50-$_plugname.conf")
backup=("etc/vdr/conf.avail/50-$_plugname.conf")
sha512sums=('e7d701db812ec1da026ebc98cc2c8f7db2288022574346a41e3582198a1fd0ba607911a16d0f1c7d725ce316e6be960be3520919f213a71b2f69a5990ae2f5d9'
         '9a7252ba5b1fb0d013d70cbd14652ecd3b68fb78680e93525d35643ad0a34c480e11943e7812191fe5fe3b665056ee480b8df4ae62e27b35f0e67dc15d24714f')

build() {
    cd "${srcdir}/${_plugname}-${pkgver}"
    make
}

package() {
    cd "${srcdir}/${_plugname}-${pkgver}"
    make DESTDIR="${pkgdir}" install

    install -Dm644 "$srcdir/50-$_plugname.conf" "$pkgdir/etc/vdr/conf.avail/50-$_plugname.conf"
}
