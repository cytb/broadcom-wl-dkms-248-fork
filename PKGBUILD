# Maintainer: Andrey Vihrov <andrey.vihrov at gmail.com>
# Contributor: Frank Vanderham <twelve.eighty (at) gmail.>
# Contributor: yafengabc <yafengabc (at) gmail.>

pkgname=broadcom-wl-dkms-248
pkgver=6.30.223.248
pkgrel=1
pkgdesc="Broadcom 802.11 Linux STA wireless driver Old version for some bcm card kernel crash"
arch=('i686' 'x86_64')
url="https://www.broadcom.com/support/?gid=1"
license=('custom')
depends=('dkms')
optdepends=('linux-headers: build modules against Arch kernel'
            'linux-lts-headers: build modules against LTS Arch kernel')
conflicts=('broadcom-wl' 'broadcom-wl-dkms')
backup=('etc/modprobe.d/broadcom-wl-dkms.conf')
install=broadcom-wl-dkms.install
source=('broadcom-wl-dkms.conf'
        'dkms.conf'
        'linux-4.7.patch'
        )

# source_i686=("https://www.broadcom.com/docs/linux_sta/hybrid-v35-nodebug-pcoem-${pkgver//./_}.tar.gz")
# source_x86_64=("https://www.broadcom.com/docs/linux_sta/hybrid-v35_64-nodebug-pcoem-${pkgver//./_}.tar.gz")
source_i686=("https://pkgs.rpmfusion.org/repo/pkgs/nonfree/broadcom-wl/hybrid-v35-nodebug-pcoem-6_30_223_248.tar.gz/e048154b3f4c7ad6bee36cab5b37486d/hybrid-v35-nodebug-pcoem-6_30_223_248.tar.gz")
source_x86_64=("https://pkgs.rpmfusion.org/repo/pkgs/nonfree/broadcom-wl/hybrid-v35_64-nodebug-pcoem-6_30_223_248.tar.gz/0237917f75d121589ec16a44eac5f5b0/hybrid-v35_64-nodebug-pcoem-6_30_223_248.tar.gz")
sha256sums=('b97bc588420d1542f73279e71975ccb5d81d75e534e7b5717e01d6e6adf6a283'
            '2ff32beee3478da027f7bd6ef8333f441c42a0f89ae175105f11e12ba2b1e018'
            '220fea898bd9c96560c7b89881ba1f8faa9f23afd109d2a57bf8e7ddc9ecda34')
sha256sums_i686=('b196543a429c22b2b8d75d0c1d9e6e7ff212c3d3e1f42cc6fd9e4858f01da1ad')
sha256sums_x86_64=('3d994cc6c05198f4b6f07a213ac1e9e45a45159899e6c4a7feca5e6c395c3022')

prepare() {
  cd "${srcdir}"
  patch -p1 -i linux-4.7.patch
}

package() {
  cd "${srcdir}"

  local dest="${pkgdir}/usr/src/${pkgname/-dkms/}-${pkgver}"

  mkdir -p "${dest}"
  cp -RL src lib Makefile dkms.conf "${dest}"
  chmod a-x "${dest}/lib/LICENSE.txt" # Ships with executable bits set

  mkdir -p "${pkgdir}/usr/share/licenses/${pkgname}"
  ln -rs "${dest}/lib/LICENSE.txt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  install -D -m 644 broadcom-wl-dkms.conf "${pkgdir}/etc/modprobe.d/broadcom-wl-dkms.conf"
}

# vim:set ts=2 sw=2 et:

