# Maintainer: Snehit Sah <snehitsah@protonmail.com>
# Maintainer: Panda <rippanda.smail@gmail.com>
pkgname=lsb-release
pkgver=2.5
pkgrel=2
pkgdesc="Add Bred Branding!"
arch=('any')
url="https://bred.snehit.dev/"
license=('GPL2')
depends=('bash')
install=lsb-release.install
source=(https://downloads.sourceforge.net/lsb/lsb-release-1.4.tar.gz
        lsb_release_description.patch
        lsb_release_make_man_page_reproducible.patch)
sha512sums=('84f6f8794380463587005043f601b7a40190cd9e3409abff7f5ce7658cf029a14346eff87838296d90307192bdeff68cc00480c5c04814da7acdb3e220640fde'
            '145ef64f90f5e6cc59075679e640cf7c1ad02617c12eff17f10b05c1cc219591fdba1b27be2b2c8480742aed24ce81d6a7badcbaca6772faea4ebc6a55695b62'
            'ab64a1d236d00a30a48e3af2c5bdfa0aad0183ebe0df4f2b0c6af58530c2a1fdac1b0a5cdd8a1800d5f8405f44562603cddf28eb318b5badaabd49a82e0b7e83')

prepare() {
  cd "$srcdir/lsb-release-1.4"

  patch -Np0 < "$srcdir/lsb_release_description.patch"
  patch -Np1 < "$srcdir/lsb_release_make_man_page_reproducible.patch"
}


build() {
  cd "$srcdir/lsb-release-1.4"

  make
}

package() {
  cd "$srcdir/lsb-release-1.4"

  install -dm755 "$pkgdir/etc"
  echo "LSB_VERSION=1.4" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_ID=BredOS" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_RELEASE=rolling" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_DESCRIPTION=\"BredOS\"" >> "$pkgdir/etc/lsb-release"

  install -Dm 644 lsb_release.1.gz "$pkgdir/usr/share/man/man1/lsb_release.1.gz"
  install -Dm 755 lsb_release "$pkgdir/usr/bin/lsb_release"
}
