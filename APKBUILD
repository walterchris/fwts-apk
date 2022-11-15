# Contributor:
# Maintainer:
pkgname=fwts
pkgver=0.1
pkgrel=0
pkgdesc="FWTS Port for Alpine Linux"
url="https://github.com/walterchris/fwts/"
arch="all"
license="LGPL-2.1-or-later"
depends="
	libbsd-dev
	glib-dev
	libexecinfo-dev"
makedepends="
	autoconf
	automake
	libtool
	flex
	bison
	libbsd-dev
	g++
	glib-dev
	make
	libexecinfo-dev
"
checkdepends=""
install=""
options="!tracedeps"
subpackages="$pkgname-doc"
source="https://github.com/walterchris/fwts/archive/refs/heads/feature/alpine.zip"
builddir="$srcdir/"

build() {
	echo "$pkgdir"
	cd fwts-feature-alpine
	pwd
	echo "We need to do some hot patching here.."
	sudo sed -i '/#warning/d' /usr/include/sys/cdefs.h
	autoreconf -ivf
	./configure
	make
	:
}

check() {
	# Replace with proper check command(s)
	:
}

package() {
	cd fwts-feature-alpine
	sudo make DESTDIR="$pkgdir" install
	cd ../..
	sudo chown -R build:abuild pkg
	mv pkg/fwts/usr/local/bin pkg/fwts/usr/bin
	mv pkg/fwts/usr/local/share pkg/fwts/usr/share
	mkdir pkg/fwts/usr/lib
	cp -R pkg/fwts/usr/local/lib/fwts/* pkg/fwts/usr/lib/.
	rm -R pkg/fwts/usr/local
	:
}

sha512sums="
84d61bdd253373d164c1412236843915d806f85e10555e2f82e8643a4c39ef9f9f375b999001cd44ab6eb7b24dfd25c19b325044e3c5dbc90617c3a357509c58  alpine.zip
"
