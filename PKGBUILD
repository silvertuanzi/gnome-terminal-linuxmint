# Maintainer: Silver Tuanzi

pkgname=gnome-terminal-linuxmint
_pkgname=gnome-terminal
pkgver=3.56.2
_mintver=mint1+gigi
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
  cairo
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
b2sums=('6ec3753b8c0d2ed3e13e0f13732662cff568e7053adac8af6533a902181a35b6a49a313c5c026ca143590a62982f308843b7933077c5e43cf32eba76cc82b9c4')

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

