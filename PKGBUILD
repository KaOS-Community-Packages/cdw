pkgname=cdw
pkgver=0.8.1
pkgrel=1
pkgdesc="Ncurses based cd/dvd burning utility"
arch=('x86_64')
url="http://cdw.sourceforge.net/"
license=('GPL')
depends=('cdrtools' 'udftools' 'ncurses' 'libburn' 'libisoburn' 'libcdio' 'glibc' 'dvd+rw-tools' 'rsync')
source=("${pkgname}-${pkgver}.tar.gz::http://sourceforge.net/projects/${pkgname}/files/${pkgname}/${pkgname}%20${pkgver}/${pkgname}-${pkgver}.tar.gz/download"
        'cdw.png'
        'cdw.desktop')
md5sums=('9e6b5c2bbe54e8f1dc0d20e3cb966e5c'
         '7b8d628d6fceec8ba4e4b93794eb8f78'
         'add9eb1d21604e6d8b0075b59e2a8fbe')

build() {
  cd "${srcdir}"/${pkgname}-${pkgver}
  ./configure --prefix=/usr
  make
}

check() {
	cd "${srcdir}"/${pkgname}-${pkgver}
	make -k check
}

package() {
  cd "${srcdir}"/${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}/" install
  install -dm755 "${pkgdir}"/usr/share/doc/cdw
  install -dm755 "${pkgdir}"/usr/share/applications
  install -dm755 "${pkgdir}"/usr/share/icons/hicolor/32x32/apps
  install -m644 cdw.conf "${pkgdir}"/usr/share/doc/cdw
  install -m644 cdw.colors "${pkgdir}"/usr/share/doc/cdw
  install -m644 ../../cdw.desktop "${pkgdir}"/usr/share/applications
  install -m644 ../../cdw.png "${pkgdir}"/usr/share/icons/hicolor/32x32/apps
}
