# Maintainer: wszqkzqk <wszqkzqk@gmail.com>

pkgname=deepin-tim-for-arch
pkgver=1.1.5
deepintimver=1.0.4deepin4
pkgrel=0
pkgdesc="Latest Tencent TIM (com.qq.office) on Deepin Wine For Archlinux"
arch=("x86_64")
url="http://tim.qq.com/"
license=('custom')
depends=('p7zip' 'wine' 'xorg-xwininfo' 'xdotool')
_mirror="https://mirrors.ustc.edu.cn/deepin"
source=("$_mirror/pool/non-free/d/deepin.com.qq.office/deepin.com.qq.office_${deepintimver}_i386.deb"
  "http://dldir1.qq.com/qqfile/qq/TIM${pkgver}/21175/TIM${pkgver}.exe"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/run.sh"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/system.reg"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/update.policy"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/user.reg"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/userdef.reg"
  "https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/wqy-microhei.ttc")
md5sums=('24de53e74f6917dad0693b57e1e6ba4b'
  '4d63de9d589c2d60bb36107849fc87e2'
  'SKIP'
  'SKIP'
  'SKIP'
  'SKIP'
  'SKIP'
  '966af48e02884546677a2f762f6725b9')

build() {
  pushd ${srcdir}
  msg "Extracting DPKG package ..."
  mkdir dpkgdir
  tar -xvf data.tar.xz -C dpkgdir
  msg "Extracting Deepin Wine TIM archive ..."
  7z x dpkgdir/opt/deepinwine/apps/Deepin-TIM/files.7z -odeepintimdir
  msg "Removing original outdated TIM directory ..."
  rm -r deepintimdir/drive_c/Program\ Files/Tencent/TIM
  msg "Repackaging app archive ..."
  cp ../userdef.reg deepintimdir/userdef.reg
  cp ../system.reg deepintimdir/system.reg
  cp ../update.policy deepintimdir/update.policy
  cp ../user.reg deepintimdir/user.reg
  pushd deepintimdir
  7z a -t7z -r ../files.7z *
  popd
  popd
}

package() {
  pushd ${pkgdir}
  msg "Preparing icons ..."
  mkdir -p usr/share
  mv ${srcdir}/dpkgdir/usr/local/share/* usr/share/
  msg "Copying TIM to /opt/deepinwine/apps/Deepin-TIM ..."
  mkdir -p opt/deepinwine/apps/Deepin-TIM
  cp ${srcdir}/{files.7z,run.sh,TIM$pkgver.exe} -i opt/deepinwine/apps/Deepin-TIM/
  chmod +x opt/deepinwine/apps/Deepin-TIM/run.sh
  popd
}
