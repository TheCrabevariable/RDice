# Maintainer: TheCrabeuh <clement.dallasenn@outlook.fr>
pkgname=rdice # '-bzr', '-git', '-hg' or '-svn'
pkgver=1
pkgrel=1
pkgdesc="a command that generate a random number between the ones you gave him"
arch=('x86_64')
url="https://github.com/TheCrabevariable/RDice.git"
makedepends=(git) # 'bzr', 'git', 'mercurial' or 'subversion'
options=()
install=
source=("git+$url")
noextract=()
sha256sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${pkgname%-VCS}"

# The examples below are not absolute and need to be adapted to each repo. The
# primary goal is to generate version numbers that will increase according to
# pacman's version comparisons with later commits to the repo. The format
# VERSION='VER_NUM.rREV_NUM.HASH', or a relevant subset in case VER_NUM or HASH
# are not available, is recommended.

# Bazaar
	printf "r%s" "$(bzr revno)"

# Git, tags available
	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"

# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"

# Mercurial
	printf "r%s.%s" "$(hg identify -n)" "$(hg identify -i)"

# Subversion
	printf "r%s" "$(svnversion | tr -d 'A-z')"
}

prepare() {
	cd "$srcdir/${pkgname%-VCS}"
	patch -p1 -i "$srcdir/${pkgname%-VCS}.patch"
}

build() {
	cd "$srcdir/${pkgname%-VCS}"
	./autogen.sh
	./configure --prefix=/usr
	make
}

check() {
	cd "$srcdir/${pkgname%-VCS}"
	make -k check
}

package() {
	cd "$srcdir/${pkgname%-VCS}"
	make DESTDIR="$pkgdir/" install
}
