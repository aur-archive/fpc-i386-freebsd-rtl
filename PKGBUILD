pkgname=fpc-i386-freebsd-rtl
pkgver=2.6.0
pkgrel=2
pkgdesc="Free Pascal runtime library for FreeBSD i386."
arch=('any')
url="http://www.freepascal.org/"
license=('GPL' 'LGPL' 'custom')
depends=('fpc=2.6.0' 'i386-freebsd-binutils' 'ppcross386')
makedepends=(i386-freebsd-binutils ppcross386)
source=("ftp://ftp.freepascal.org/pub/fpc/dist/$pkgver/source/fpcbuild-$pkgver.tar.gz")
md5sums=('17375e665a4e1311f85812fe2754f609')

build() {
  cd "${srcdir}/fpcbuild-$pkgver/fpcsrc/compiler"
  fpcmake -Tall
  cd ../..
  make NOGDB=1 build OS_TARGET=freebsd CPU_TARGET=i386
}

package() {
  cd "${srcdir}/fpcbuild-$pkgver"
  make NOGDB=1 PREFIX="${pkgdir}/usr" crossinstall OS_TARGET=freebsd CPU_TARGET=i386
  rm -rf "${pkgdir}/usr/bin"
  rm "$pkgdir/usr/lib/fpc/$pkgver/ppcross386"
  
  cat << 'EOM'
  ==> PLEASE NOTE:
  ==> Please be sure to copy fpcbuild-x.x.x.tar.gz to the extracted package folders
  ==> of any RTLs or other FPC cross compilers you intend to build, as Free Pascal's 
  ==> FTP server is very low bandwidth. Thanks!    
EOM
}