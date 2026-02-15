# Maintainer: Antisos Release Engineering <dev@antisos.org>
pkgname=as-inst
pkgver=2026.02.15
pkgrel=1
pkgdesc="AntisOS Bootstrap Installer - Standalone Binary"
arch=('x86_64')
url="https://github.com/franiekidos/as-inst"
license=('GPL')

# Runtime dependencies for the apps as-inst will eventually pull
depends=('curl' 'git' 'base-devel')

# Build dependencies - using the Arch repo pyinstaller
makedepends=('pyinstaller' 'git')

source=("git+https://github.com/franiekidos/as-inst.git")
sha256sums=('SKIP')

build() {
    cd "$srcdir/${pkgname}"

    echo "==> Starting PyInstaller Binary Build..."
    
    # --onefile: Packages everything into a single ELF binary
    # --strip: Removes debug symbols for a smaller 'No-Dox' binary
    # --clean: Cleans PyInstaller cache before building
    # Assuming your entry point script is named as-inst.py
    pyinstaller \
        --onefile \
        --strip \
        --clean \
        --name "as-inst" \
        "as-inst"

    if [ $? -ne 0 ]; then
        echo ":: ERROR: PyInstaller failed to create the executable."
        exit 1
    fi
}

package() {
    cd "$srcdir/${pkgname}"

    # Install the standalone binary to /usr/bin
    install -Dm755 "dist/as-inst" "${pkgdir}/usr/bin/as-inst"
}