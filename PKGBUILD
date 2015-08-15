# Maintainer: crazyelf5

pkgname=cinnamon-settings-git
pkgver=20120116
pkgrel=1
pkgdesc="Cinnamon configuration tool"
arch=('any')
url="https://github.com/linuxmint/cinnamon-settings"
license=('GPL')
depends=('cinnamon-git' 'python2' 'python2-gconf' 'python2-gobject2' 'python2-gobject' 'librsvg' 'pygtk')
makedepends=('git')

_gitroot=git://github.com/linuxmint/cinnamon-settings.git
_gitname=cinnamon-settings

build() {
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  cp -rf "$srcdir/cinnamon-settings/usr" "$pkgdir/"
  cd "$pkgdir/"

  # Sed for Python2
  sed -e "s_env python_&2_;s_bin/python_&2_" \
      -i `egrep -rl "(env python|bin/python)" .`
}

# vim:set ts=2 sw=2 et:
