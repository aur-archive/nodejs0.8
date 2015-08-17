pkgname=nodejs0.8
pkgver=0.8.0
pkgrel=2
pkgdesc='Evented I/O for V8 javascript - v0.8 package for impatient people'
arch=('i686' 'x86_64')
url='http://nodejs.org/'
license=('MIT')
depends=('python2')
checkdepends=('curl') # curl used for check()
optdepends=('openssl: TLS support')
options=('!emptydirs')
source=("http://nodejs.org/dist/v${pkgver}/node-v${pkgver}.tar.gz")
md5sums=('7efde00ad3292d4c56ad607ab676d935')
conflicts=('nodejs')
provides=('nodejs')

build() {
  ln -s $(which python2) ${srcdir}/python

  export PATH=${srcdir}:$PATH

  cd node-v${pkgver}

  ./configure --prefix=/usr/

  make
}

check() {
  cd node-v${pkgver}

  make test || true
}

package() {
  cd node-v${pkgver}

  make DESTDIR=${pkgdir} install || return 1
}
