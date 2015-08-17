# Contributor: Anibal Pacheco <apacheco.uy@gmail.com>
pkgname="scrapy-git"
pkgver=20110925
pkgrel=3
pkgdesc="A fast high-level scraping and web crawling framework - development version."
arch=('i686' 'x86_64')
license=('BSD')
url="http://scrapy.org"
depends=('python2>=2.5' 'twisted>=2.5' 'libxml2>=2.6.28', 'python2-w3lib-git')
makedepends=('git')
optdepends=("pyopenssl: for HTTPS support. Optional, but highly recommended")
provides=('scrapy')
conflicts=('scrapy')
options=(!emptydirs)

_gitroot=https://github.com/scrapy/scrapy.git
_gitrepo=scrapy

package() {
  cd ${srcdir}

  if [ -d ${_gitrepo} ]; then
    (cd ${_gitrepo} && git pull)
  else
    git clone ${_gitroot}
    cd ${_gitrepo}
  fi

  # installation
  cd $srcdir/$_gitrepo
  python2 setup.py install --root=$pkgdir || return 1

  # copying license information
  install -D -m644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE

  # copying readme information
  install -D -m644 docs/README $pkgdir/usr/share/doc/$pkgname/README
  install -D -m644 INSTALL $pkgdir/usr/share/doc/$pkgname/INSTALL
}
