# Contributor:
# Maintainer:
pkgname=hping
pkgver=0.r13.3547c7691742c6eaa31f8402e0ccbb81387c1b99
pkgrel=1
pkgdesc="network tool able to send custom TCP/IP packets and to display target replies"
url="https://github.com/antirez/$pkgname"
arch="all"
license="GPL2"
depends="tcl libpcap"
depends_dev=""
makedepends="tcl-dev libpcap-dev"
install=""
subpackages="$pkgname-doc"
source="http://dev.alpinelinux.org/archive/$pkgname/$pkgname-$pkgver.tar.gz
        10-add_tcl_version.patch
        20-pass_CFLAGS_to_gcc.patch
        30-fix_bpf_include.patch"

_builddir="$srcdir"/hping
prepare() {
	local i
	cd "$_builddir"
	echo $source
	for i in $source; do
		case $i in
		*.patch) msg $i; patch -p1 -i "$srcdir"/$i || return 1;;
		esac
	done
}

snapshot() {
        abuild clean
	mkdir -p $srcdir
	cd $srcdir
	msg "Checking out hping master branch"
	git clone $url || return 1
	tar zcf $pkgname-$pkgver.tar.gz hping || return 1
}

build() {
	cd "$_builddir"
	./configure --prefix=/usr
	make
	make strip
}

package() {
	cd "$_builddir"
	install -D -m 755 hping3 $pkgdir/usr/sbin/hping3
	ln -s $pkgdir/usr/sbin/hpin3 $pkgdir/usr/sbin/hping
	ln -s $pkgdir/usr/sbin/hpin3 $pkgdir/usr/sbin/hping2
}

doc() {
    default_doc
    cd "$_builddir"/docs

    gzip -c hping2.8 > hping2.8.gz
    install -D -m 0644 hping2.8.gz $subpkgdir/usr/share/man/man8/hping2.8.gz

    gzip -c hping3.8 > hping3.8.gz
    install -D -m 0644 hping3.8.gz $subpkgdir/usr/share/man/man8/hping3.8.gz
}
md5sums="1918c30a3626b60062414b4e2ad70d08  hping-0.r13.3547c7691742c6eaa31f8402e0ccbb81387c1b99.tar.gz
b5b43469b3bc5451870c9214c178e380  10-add_tcl_version.patch
05161223c57de36a3d07f7f6544cdcde  20-pass_CFLAGS_to_gcc.patch
bc7819f6f76360b38f43447124f2e4d3  30-fix_bpf_include.patch"
sha256sums="1bad382752be2b322dbad8687489ab969d3342bdcf7fa3dcc22e7726ce61fe51  hping-0.r13.3547c7691742c6eaa31f8402e0ccbb81387c1b99.tar.gz
4b2ba6a21a7d14f6251bf7d186efceeef1dcf6261cab8429fe0e8b402dc4739e  10-add_tcl_version.patch
dd33970382773f0cd0944ee2fc90d1e10a79c8a67e922662b7cb0f0491dee816  20-pass_CFLAGS_to_gcc.patch
7dda17a55ca2e4ecb3003dfb84d804b30d3f030a1fcdf4ebdda65fa8a6fec410  30-fix_bpf_include.patch"
sha512sums="44e908442099067c419e929cdfad7227a1ba924a6fc4495630a7fdd169cc42c24b4727d8f60ca29f32704689eba9596f294b696805592aaf55e8fbcfc90b1748  hping-0.r13.3547c7691742c6eaa31f8402e0ccbb81387c1b99.tar.gz
3d7629a77ddbed4231172c6702b0f3a6929e19a303c5629ecb014ab4cd593763a3573507c9cb2f45fc5ad2032d7f95410bea9ef8a68a6508695d77dfd8e00e9b  10-add_tcl_version.patch
09b2b04bb9a6788a29da546c07c6301973757dbd67bd00a4e71dde2c762f9b39ad5c9e464a89c92569af762fd3fcecbcc01749f0f8bb4f416ab75ed95e0cae67  20-pass_CFLAGS_to_gcc.patch
660a434837e8d0afeac9b3a1ca301ca8b8585bf02dcba79fa24b4d9b479336fc774a7c9b0e19e63b6782535a9c0c0a1ddb077735e0d0bb1ed7a41e77b581ac89  30-fix_bpf_include.patch"
