# Maintainer: TheCrabeuh <clement.dallasenn@outlook.fr>
pkgname=rdice # '-bzr', '-git', '-hg' or '-svn'
pkgver=1
pkgrel=1
pkgdesc="a command that generate a random number between the ones you gave him"
arch=('x86_64')
url="https://github.com/TheCrabevariable/rdice.git"
makedepends=(git) # 'bzr', 'git', 'mercurial' or 'subversion'
options=()
install=
source=("git+$url")
noextract=()
sha256sums=('SKIP')

build() {
	cd "$srcdir/${pkgname%-VCS}"
	cargo build --release --locked
}

package() {
	cd "$srcdir/${pkgname%-VCS}"
	install -Dm755 target/release/rdice "$pkgdir/usr/bin/rdice"
}
