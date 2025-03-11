# Maintainer: Silver Tuanzi

pkgname=gnome-terminal-linuxmint
_pkgname=gnome-terminal
pkgver=3.52.0
_mintver=mint2+xia
pkgrel=2
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
b2sums=('80c2ca7d097742b710a3a76f2f4e4bebc67645a581d8a95d43d521cc4c36af839053ae0cfc2c7019fc1ba7b5b31c0ea1f58a4a867574a1863e127c8e9ce9a5b6')

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

