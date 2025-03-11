# Maintainer: Silver Tuanzi

pkgname=gnome-terminal-linuxmint
_pkgname=gnome-terminal
pkgver=3.52.0
_mintver=mint1+wilma
pkgrel=1
pkgdesc="The GNOME Terminal Emulator"
url="https://wiki.gnome.org/Apps/Terminal"
arch=(x86_64)
provides=(
    ${_pkgname}
)
conflicts=(
    ${_pkgname}
)
license=(
  # Program
  GPL-3.0-or-later

  # Documentation
  CC-BY-SA-3.0
  GPL-3.0-only

  # Appstream-data
  GFDL-1.3-only
)
depends=(
  dconf
  gcc-libs
  glib2
  glibc
  gsettings-desktop-schemas
  gtk3
  hicolor-icon-theme
  libhandy
  libx11
  pango
  util-linux-libs
  vte3
)
makedepends=(
  docbook-xsl
  git
  glib2-devel
  meson
  yelp-tools
  libnautilus-extension
)
optdepends=(
  "libnautilus-extension: Nautilus integration"
)
source=("http://packages.linuxmint.com/pool/upstream/g/gnome-terminal/gnome-terminal_${pkgver}+${_mintver}.tar.xz")
#source=("https://mirrors.cernet.edu.cn/linuxmint/pool/upstream/g/gnome-terminal/gnome-terminal_${pkgver}+${_mintver}.tar.xz")
b2sums=('d38e519e6386d56566a48d8432da8e6b9bb9b3b238b6b987bc51a178231b3ffffb7a7947ed9f2713198d465b472340e71de6040468d0e3eafcf73dcc6604f651')

prepare() {
  cd $_pkgname
}

build() {
  local meson_options=(
    -D b_lto=false
  )

  arch-meson $_pkgname build "${meson_options[@]}"
  meson compile -C build
}

check() {
  meson test -C build --print-errorlogs
}

package() {
  meson install -C build --destdir "$pkgdir"
}

