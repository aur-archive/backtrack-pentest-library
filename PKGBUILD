# Contributor: Thomas Mudrunka <harvie@@email..cz>
# Maintainer:  Sietse van der Molen <sietse@vdmolen.eu>

pkgname=backtrack-pentest-library
_imagename=BT5R3-GNOME-32
pkgver=5r3
pkgrel=5
pkgdesc='Pentesting scripts from Back-Track live-cd Linux distribution.'
arch=('any')
license=('many')
url="http://www.remote-exploit.org/backtrack.html"
makedepends=('squashfs-tools')
optdepends=(
'milw0rm-exploit-database: Exploits from milw0rm.com'
'metasploit: MetaSploit exploiting framework + exploits'
'nmap: Basic network scanner'
'nessus-core: Advanced security scanner'
'nessus-libraries: Advanced security scanner libraries'
'nessus-plugins: Advanced security scanner plugins'
'wine: To execute some of utilities from library'
'python: library contains lot of python scripts'
'perl: library contains lot of perl scripts'
)
options=('!strip') #strip doesn't work
source=("http://www.backtrack-linux.org/ajax/download_redirect.php?id=${_imagename}.iso")
md5sums=('aafff8ff5b71fdb6fccdded49a6541a0')

build() {
  _destdir='opt/backtrack'

  cd ${startdir}

  echo '==> Extracting pentest folder from squashfs dump'
  echo
  unsquashfs -d tmp/ src/casper/filesystem.squashfs -e pentest || return 1

  mkdir -p ${pkgdir}/${_destdir}
  echo '==> Copying temporary files to fakeroot'
  echo
  cp -rf tmp/pentest/* ${pkgdir}/${_destdir}/
  echo; echo;

  echo '==> Removing temporary files'
  echo
  rm -rf tmp/
  echo '==> Removing source files'
  echo
  chmod 777 -R src/ # Fix permission error while removing /src dir
  rm -rf src/

  echo '==> Setting permissions'
  echo
  chown root:root ${pkgdir}/${_destdir}
  chmod -R 655 ${pkgdir}/${_destdir}
}
