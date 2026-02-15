# Maintainer: Antisos Release Engineering <dev@antisos.org>
pkgname=as-inst
pkgver=2026.02.15
pkgrel=1
pkgdesc="AntisOS Bootstrap Installer - Pulls and builds the AntisOS ecosystem"
arch=('any')
url="https://github.com/your-username/antisos-pkgbuilds"
license=('GPL')
depends=('python' 'curl' 'git' 'base-devel')

source=("git+placeholder") # The Python script we've been refining
sha256sums=('SKIP')

package() {
    # Install the script into /usr/bin/
    install -Dm755 "${srcdir}/as-inst.py" "${pkgdir}/usr/bin/as-inst"
}