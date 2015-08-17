pkgname=python-needles-git
pkgver=20121117
pkgrel=1
pkgdesc="needles are small tools for fast and comfortable usage LaTeX."
arch=('i686' 'x86_64')
url="https://github.com/citrux/needles"
license=('MIT')
depends=('python' 'python-matplotlib')
conflicts=('needles-git')
provides=('needles-git')
replaces=('needles-git')
makedepends=('git')

_gitroot="git://github.com/citrux/needles.git"
_gitname="needles"

build() {
  cd "$srcdir"
  msg "Connecting to git server"
  if [ -d $_gitname ] ; then
    cd "$_gitname" && git pull
    msg "Local files are updated"
  else
    git clone "$_gitroot"
  fi
  msg "Git checkout done or server timeout"
  cd "$srcdir"
  cp -r "$_gitname" "$_gitname-build"
  msg2 "Building..."
  cd "$_gitname-build"
  python setup.py build
}

package() {
  msg2 "Packaging..."
  cd "$_gitname-build"
  python setup.py install --prefix=/usr --root="$pkgdir"
}
