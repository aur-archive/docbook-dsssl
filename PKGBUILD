# Contributor: Andreas B. Wagner <AndreasBWagner@pointfree.net>
# Contributor: Suat SARIALP <muhendis.suat@gmail.com>
pkgname=docbook-dsssl
pkgver=1.79
pkgrel=5
pkgdesc="DSSSL Stylesheets for DocBook"
arch=('i686' 'x86_64')
url="http://docbook.sourceforge.net/projects/dsssl/index.html"
license=(as-is)
depends=('sgml-common')
install=docbook-dsssl.install
makedepends=()
source=("http://download.sourceforge.net/project/docbook/$pkgname/$pkgver/$pkgname-$pkgver.tar.gz" "docbook-dsssl-stylesheets.Makefile")
md5sums=('8459913bbd8a5724a6fe4b9ed5bab5af'
         'aa413b2500a9fa5f6ac08e657d0958d5')

package() {
  cd $srcdir/$pkgname-$pkgver
  cp $srcdir/docbook-dsssl-stylesheets.Makefile Makefile
  make BINDIR="$pkgdir/usr/bin" DESTDIR="$pkgdir/usr/share/sgml/docbook/dsssl-stylesheets-${pkgver}"
  mkdir -p $pkgdir/usr/share/sgml/stylesheets/dsssl/
  if [ -d /usr/share/sgml/stylesheets/dsssl/docbook ] &&
		[ ! -L /usr/share/sgml/stylesheets/dsssl/docbook ]
	then
		msg "Not linking /usr/share/sgml/stylesheets/dsssl/docbook to"
		msg "/usr/share/sgml/docbook/dsssl-stylesheets-${PV}"
		msg "as directory already exists there.  Will assume you know"
		msg "what you're doing."
		exit 1
	fi

  ln -sf "/usr/share/sgml/docbook/dsssl-stylesheets-$pkgver" "$pkgdir/usr/share/sgml/stylesheets/dsssl/docbook"
}

