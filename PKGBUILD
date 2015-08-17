# Contributor: Giovanni Cucca <giovanni.cucca@gmail.com>
# Maintainer: Dany Martineau <dany.luc.martineau gmail.com>

pkgname=trackballs
pkgver=1.1.4
pkgrel=5
pkgdesc="Simple game similar to the classical game Marble Madness on the Amiga in the 80's"
arch=('i686' 'x86_64')
license=('GPL')
url="http://trackballs.sourceforge.net/"
depends=('guile>=1.8.1' 'sdl_ttf' 'sdl_image' 'sdl_mixer' 'mesa')
source=(http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.gz \
        http://downloads.sourceforge.net/sourceforge/$pkgname/SixLevels.tar.gz \
		trackballs.desktop trackballs.patch)
md5sums=('84e2e8bb68842a636da91673751279a0' '2bb730894a85334a681cfd9f40fe075e' \
         '831053e0375b14c905b6cb534ea134a4' '3c383cf4b88330e6b14dea8881667ab9' )

build() {
  cd ${srcdir}/$pkgname-$pkgver
  patch -p1 < ../trackballs.patch
  ./configure --prefix=/usr --with-sdl-prefix=/usr --disable-sdltest --with-highscores="~"
  make || return 1
  make DESTDIR=${startdir}/pkg install
  install -m644 ${srcdir}/*.map ${pkgdir}/usr/share/trackballs/levels
  install -m644 ${srcdir}/*.scm ${pkgdir}/usr/share/trackballs/levels
  install -m644 ${srcdir}/*.jpg ${pkgdir}/usr/share/trackballs/levels
  install -m644 ${srcdir}/*.set ${pkgdir}/usr/share/trackballs/levels
  
  mkdir -p ${pkgdir}/usr/share/applications
  install -m644 ${srcdir}/trackballs.desktop \
                ${pkgdir}/usr/share/applications/
}
