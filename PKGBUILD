# Contributer: giacomogiorgianni@gmail.com
 
pkgname=kateinclude-helper-plugin
_name=KateCppHelperPlugin
pkgver=1.0.1
pkgrel=1
pkgdesc="Kate C++ Helper plugin"
arch=('any')
url="https://github.com/zaufi/kate-cpp-helper-plugin"
license=('GPL-2')
categories=()
depends=('kdebase-katepart' 'boost' 'kdesdk-kate' 'clang>=3.1' 'xapian-core')
makedepends=()
options=(!emptydirs)
source=("http://kde-apps.org/CONTENT/content-files/148606-${_name}-${pkgver}.tar.bz2")
md5sums=('f355c453515817b504a2be77fae326a1')
 
build()
{
  if [ -d ${srcdir}/${_name}-${pkgver}/build ] ; then
    rm -rf ${srcdir}/${_name}-${pkgver}/build  
  fi
  mkdir ${srcdir}/${_name}-${pkgver}/build  && cd ${srcdir}/${_name}-${pkgver}/build
  cmake -DQT_QMAKE_EXECUTABLE=/usr/bin/qmake-qt4 \
        -DBUILD_TESTING=OFF -DNO_DOXY_DOCS=ON\
        -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` \
        ..
  make -j5 || return 1
}
 
package()
{
  cd ${srcdir}/${_name}-${pkgver}/build
  make DESTDIR="${pkgdir}" install || return 1
}
