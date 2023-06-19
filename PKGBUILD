# Maintainer: Giuliano Schneider <gs93@gmx.net>
pkgname=pakbak-bkmo
_gitname=pakbak-bkmo
pkgver=20230623
pkgrel=1
pkgdesc="Back up the local pacman database when it changes"
arch=('any')
url="https://github.com/bkmo/pakbak"
license=('GPL3')
depends=('bash' 'findutils' 'tar' 'systemd')
makedepends=('git')
backup=('etc/pakbak.conf')
source=("pakbak::git+https://github.com/bkmo/$_gitname" $_gitname.install)
install=$_gitname.install
md5sums=('SKIP' 'SKIP')
sha512sums=('SKIP' 'SKIP')

pkgver() {
    # using the last commit date
    cd "$_gitname"
    git log -1 --format="%cd" --date=short | tr -d '-'
}

package() {
    cd "$_gitname"

    mkdir -p "$pkgdir/usr/lib/systemd/scripts"
    install -Dm755 pakbak_script "$pkgdir/usr/lib/systemd/scripts/pakbak"

    mkdir -p "$pkgdir/etc"
    install -Dm644 pakbak.conf "$pkgdir/etc/pakbak.conf"

    mkdir -p "$pkgdir/usr/lib/systemd/system"
    install -Dm644 pakbak.service "$pkgdir/usr/lib/systemd/system/pakbak.service"
    install -Dm644 pakbak.path "$pkgdir/usr/lib/systemd/system/pakbak.path"
}
