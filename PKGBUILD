# Maintainer: Steven Terry <https://github.com/stkterry>

_pkgname=brightctl
pkgname=$_pkgname-git
pkgver=0.9.0
pkgrel=1
pkgdesc="Device brightness control for systemd"
arch=('x86_64')
url=https://github.com/stkterry/$_pkgname
license=('MIT')
depends=('systemd-libs')
makedepends=('git' 'rust')
source=($_pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz)
provides=($_pkgname)
conflicts=($_pkgname)
md5sums=('SKIP')
options=(!strip)

prepare() {
	export RUSTUP_TOOLCHAIN=stable
	cd $_pkgname-$pkgver
	cargo fetch --locked --manifest-path ./Cargo.toml
}

build() {
	export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
	cd $_pkgname-$pkgver
	cargo build --frozen --locked --manifest-path ./Cargo.toml --release
}

# check() {
	# cd $pkgname
	# cargo test --locked --manifest-path Cargo.toml
# }

package() {
	cd $_pkgname-$pkgver
	install -Dm755 ./target/release/$_pkgname $pkgdir/usr/bin/$_pkgname
	install -Dm644 ./LICENSE $pkgdir/usr/share/licenses/$_pkgname/LICENSE
}
