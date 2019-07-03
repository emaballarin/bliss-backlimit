# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Repackager: Emanuele Ballarin <emanuele@ballarin.cc>

pkgname=bliss
pkgver=0.73
pkgrel=2
pkgdesc="A library for computing automorphism groups and canonical forms of graphs"
arch=(x86_64)
url="http://www.tcs.tkk.fi/Software/bliss/index.html"
license=(GPL3)
depends=(gcc-libs)
conflicts=(bliss-graphs)
provides=(bliss-graphs)
replaces=(bliss-graphs)
source=("http://www.tcs.hut.fi/Software/bliss/bliss-$pkgver.zip" 'digraph_heuristic.patch' 'bliss-0.73.patch')
sha256sums=('f57bf32804140cad58b1240b804e0dbd68f7e6bf67eba8e0c0fa3a62fd7f0f84'
            '2f7a238347aa977b1ce1c0e9e1e955b8c213cc3a89522b586a1b8c596c88c7a5'
            'SKIP')

prepare() {
  cd bliss-$pkgver
# Fix splitting heuristics for digraphs
  patch -p1 -i ../digraph_heuristic.patch
  patch -p1 -i ../bliss-0.73.patch
}

build() {
  cd bliss-$pkgver

  make
}

package() {
  cd bliss-$pkgver

  mkdir -p "$pkgdir"/usr/{include/bliss,lib,bin}
  cp *.hh "$pkgdir"/usr/include/bliss/
  cp libbliss.a "$pkgdir"/usr/lib/
  cp bliss "$pkgdir"/usr/bin/
}
