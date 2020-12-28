# Maintainer: KeithSPG <ys3al35l@gmail.com>

extname=dbus
pkgname="php-$extname"
_pkgname="pecl-dbus"
pkgver=0.r85.315d175
pkgrel=1
pkgdesc='PHP PECL extension providing interface to dbus'
arch=('x86_64' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/derickr/pecl-dbus.git"
license=('PHP')
depends=('php>=7.0','libdbus')
source=("git+https://github.com/derickr/pecl-dbus.git")
sha256sums=('SKIP')

pkgver() {
   cd "$_pkgname"
   printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd "$srcdir/$_pkgname"
    phpize
    ./configure \
    --prefix=/usr
    make
}

package() {
    pushd "$srcdir/$_pkgname"
    make INSTALL_ROOT="$pkgdir" install
    mkdir -p "$pkgdir/etc/php/conf.d"
    touch "$pkgdir/etc/php/conf.d/$extname.ini"
    echo "extension=$extname" > "$pkgdir/etc/php/conf.d/$extname.ini"
    popd
}
