# Contributor: Jinx <Jinxware[at]gmail[dot]com>

pkgname=exploitdb-svn
pkgver=10
pkgrel=2
pkgdesc="Exploits Database by Offensive Security"
arch=('i686' 'x86_64')
url="http://www.exploit-db.com"
license=('custom: Various Licenses')
makedepends=('subversion')
conflicts=('exploit-db')
install="post.install"

_svntrunk="svn://www.exploit-db.com/exploitdb"
_svnmod="exploitdb"

build() {
  cd "$srcdir"

  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi

  msg "SVN checkout done or server timeout"
  msg "Starting to build package..."
}

package() {
	rm -rf `find "$srcdir/$_svnmod" -type d -name .svn`
	install -d -m 755 "$pkgdir/usr/src"
	mv "$srcdir/$_svnmod" "$pkgdir/usr/src"
}
