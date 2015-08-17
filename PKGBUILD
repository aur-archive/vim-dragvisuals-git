# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-dragvisuals-git
pkgver=20140320
pkgrel=1
pkgdesc="Vim global plugin for dragging virtual blocks, by Damien Conway"
arch=('any')
depends=('vim' 'vim-vis-git')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/atweiden/vim-dragvisuals"
license=('custom:vim')
source=(git+https://github.com/atweiden/vim-dragvisuals)
sha256sums=('SKIP')
provides=('vim-dragvisuals')
conflicts=('vim-dragvisuals')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-dragvisuals/README.md"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in plugin; do
    cp -R $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
