# Maintainer: franiekidos <dev@antisos.org>
pkgname=as-inst
pkgver=2026.02.15
pkgrel=2
pkgdesc="AntisOS Forwarding Port - Compiled on Stable Toolchain"
arch=('x86_64')
url="https://github.com/franiekidos/as-inst"
license=('GPL')

# Runtime needs
depends=('curl' 'git' 'gnupg' 'base-devel')
# We need the specific python version and pip to install pyinstaller
makedepends=('python312' 'python-pip' 'git')

source=("git+https://github.com/franiekidos/as-inst.git")
sha256sums=('SKIP')

build() {
    cd "$srcdir/as-inst"

    # Create venv using the STABLE python
    python3.12 -m venv build_env
    source build_env/bin/activate

    # Install pyinstaller here - it will now compile its bootloader
    # because it finally sees a Python version it supports (3.12)
    pip install pyinstaller

    pyinstaller --onefile --strip --clean --name "as-inst" "as-inst"
    deactivate
}

package() {
    cd "$srcdir/as-inst"
    install -Dm755 "dist/as-inst" "${pkgdir}/usr/bin/as-inst"
}