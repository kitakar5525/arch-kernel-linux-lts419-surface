# Maintainer: Andreas Radke <andyrtr@archlinux.org>

#pkgbase=linux-lts
pkgbase=linux-lts419-surface
_srcname=linux-4.19
pkgver=4.19.25
pkgrel=1
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=('xmlto' 'kmod' 'inetutils' 'bc' 'libelf')
options=('!strip')
source=(https://www.kernel.org/pub/linux/kernel/v4.x/${_srcname}.tar.{gz,sign}
        https://www.kernel.org/pub/linux/kernel/v4.x/patch-${pkgver}.xz
        'config'         # the main kernel config file
        '60-linux.hook'  # pacman hook for depmod
        '90-linux.hook'  # pacman hook for initramfs regeneration
        'linux-lts.preset'   # standard config files for mkinitcpio ramdisk
        0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
        4416-00-jakeday-0001-surface-acpi.patch
        4416-00-jakeday-0002-suspend.patch
        4416-00-jakeday-0003-buttons.patch
        4416-00-jakeday-0004-cameras.patch
        4416-00-jakeday-0005-ipts.patch
        4416-00-jakeday-0006-hid.patch
        4416-00-jakeday-0007-sdcard-reader.patch
        4416-00-jakeday-0008-wifi.patch
        4416-00-jakeday-0009-surface3-power.patch
        4416-00-jakeday-0010-surface-dock.patch
        4416-00-jakeday-0011-mwlwifi.patch
        4416-s0ix-01-5525-ipu_patches-419.patch
        4416-s0ix-02-5525-ICL-support-and-other-enhancements-for-PMC-Core-added-SB1.patch.patch
        4416-s0ix-Cherry-Trail-platform-x86:-Add-Intel-AtomISP2-dummy-driver-for-power-management-419.patch
        4416-s0ix-Cherry-Trail-pwm:-lpss:-Add-ACPI-HID-for-second-PWM-controller-on-Cherry-Trail-devices-419.patch
        5525-hid-add-Surface-3-JP-Type-Cover-and-Surface-Book-JP-.patch
        5525-mwifiex-change-parameters-permission.patch
        5525-sound-add-dmi-match-OEMB-for-affected-surface-3.patch
        5526-debug-intel_pmc_core-debug-quirk_xtal_ignore.patch
        5526-debug-ipts-add-module-params-for-debugging.patch
        5527-modToJake-ipts-change-default-value-of-enable_guc-to-auto.patch
        5529-gccWarn-ipts-remove-unused-variables.patch
        5529-gccWarn-ipts-uncomment-downstream_hpd_needs_d0.patch
        5529-gccWarn-mwlwifi-fix-gcc-warning.patch
)
validpgpkeys=('ABAF11C65A2970B130ABE3C479BE3E4300411886' # Linus Torvalds <torvalds@linux-foundation.org>
              '647F28654894E3BD457199BE38DBBDC86092693E' # Greg Kroah-Hartman (Linux kernel stable release signing key) <greg@kroah.com>
             )
# https://www.kernel.org/pub/linux/kernel/v4.x/sha256sums.asc
sha256sums=('SKIP' # linux kernel source file
            'SKIP' # .tar.sign
            'SKIP' # upstream patch
            'SKIP' # config
            'ae2e95db94ef7176207c690224169594d49445e04249d2499e9d2fbc117a0b21' # .hook
            '75f99f5239e03238f88d1a834c50043ec32b1dc568f2cc291b07d04718483919' # .hook
            'SKIP' # .preset
            '36b1118c8dedadc4851150ddd4eb07b1c58ac5bbf3022cc2501a27c2b476da98' # 0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
)

_kernelname=${pkgbase#linux}

prepare() {
  cd ${_srcname}

  # add upstream patch
  patch -p1 -i ../patch-${pkgver}
  chmod +x tools/objtool/sync-check.sh  # GNU patch doesn't support git-style file mode

  # security patches

  # add latest fixes from stable queue, if needed
  # http://git.kernel.org/?p=linux/kernel/git/stable/stable-queue.git

  # disable USER_NS for non-root users by default
  patch -Np1 -i ../0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
  
  # [5525]Patches
  patch -p1 -i ../4416-00-jakeday-0001-surface-acpi.patch
  patch -p1 -i ../4416-00-jakeday-0002-suspend.patch
  patch -p1 -i ../4416-00-jakeday-0003-buttons.patch
  patch -p1 -i ../4416-00-jakeday-0004-cameras.patch
  patch -p1 -i ../4416-00-jakeday-0005-ipts.patch
  patch -p1 -i ../4416-00-jakeday-0006-hid.patch
  patch -p1 -i ../4416-00-jakeday-0007-sdcard-reader.patch
  patch -p1 -i ../4416-00-jakeday-0008-wifi.patch
  patch -p1 -i ../4416-00-jakeday-0009-surface3-power.patch
  patch -p1 -i ../4416-00-jakeday-0010-surface-dock.patch
  patch -p1 -i ../4416-00-jakeday-0011-mwlwifi.patch
  patch -p1 -i ../4416-s0ix-01-5525-ipu_patches-419.patch
  patch -p1 -i ../4416-s0ix-02-5525-ICL-support-and-other-enhancements-for-PMC-Core-added-SB1.patch.patch
  patch -p1 -i ../4416-s0ix-Cherry-Trail-platform-x86:-Add-Intel-AtomISP2-dummy-driver-for-power-management-419.patch
  patch -p1 -i ../4416-s0ix-Cherry-Trail-pwm:-lpss:-Add-ACPI-HID-for-second-PWM-controller-on-Cherry-Trail-devices-419.patch
  patch -p1 -i ../5525-hid-add-Surface-3-JP-Type-Cover-and-Surface-Book-JP-.patch
  patch -p1 -i ../5525-mwifiex-change-parameters-permission.patch
  patch -p1 -i ../5525-sound-add-dmi-match-OEMB-for-affected-surface-3.patch
  patch -p1 -i ../5526-debug-intel_pmc_core-debug-quirk_xtal_ignore.patch
  patch -p1 -i ../5526-debug-ipts-add-module-params-for-debugging.patch
  patch -p1 -i ../5527-modToJake-ipts-change-default-value-of-enable_guc-to-auto.patch
  patch -p1 -i ../5529-gccWarn-ipts-remove-unused-variables.patch
  patch -p1 -i ../5529-gccWarn-ipts-uncomment-downstream_hpd_needs_d0.patch
  patch -p1 -i ../5529-gccWarn-mwlwifi-fix-gcc-warning.patch

  cp -Tf ../config .config

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  # set extraversion to pkgrel
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  # don't run depmod on 'make install'. We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  # get kernel version
  make prepare

  # load configuration
  # Configure the kernel. Replace the line below with one of your choice.
  #make menuconfig # CLI menu for configuration
  #make nconfig # new CLI menu for configuration
  #make xconfig # X-based configuration
  #make oldconfig # using old config from previous kernel version
  # ... or manually edit .config

  # rewrite configuration
  yes "" | make config >/dev/null
}

build() {
  cd ${_srcname}

  make ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

_package() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  [ "${pkgbase}" = "linux" ] && groups=('base')
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=0.7')
  optdepends=('crda: to set the correct wireless channels of your country')
  backup=("etc/mkinitcpio.d/${pkgbase}.preset")
  install=linux-lts.install

  cd ${_srcname}

  # get kernel version
  _kernver="$(make LOCALVERSION= kernelrelease)"
  _basekernel=${_kernver%%-*}
  _basekernel=${_basekernel%.*}

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  make LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}/usr" modules_install
  cp arch/x86/boot/bzImage "${pkgdir}/boot/vmlinuz-${pkgbase}"

  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  ln -sr "${pkgdir}/boot/vmlinuz-${pkgbase}" "${pkgdir}/usr/lib/modules/${_kernver}/vmlinuz"

  # make room for external modules
  local _extramodules="extramodules-${_basekernel}${_kernelname:--lts}"
  ln -s "../${_extramodules}" "${pkgdir}/usr/lib/modules/${_kernver}/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/{source,build}

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"

  # add vmlinux
  install -Dt "${pkgdir}/usr/lib/modules/${_kernver}/build" -m644 vmlinux

  # sed expression for following substitutions
  local _subst="
    s|%PKGBASE%|${pkgbase}|g
    s|%KERNVER%|${_kernver}|g
    s|%EXTRAMODULES%|${_extramodules}|g
  "

  # hack to allow specifying an initially nonexisting install file
  sed "${_subst}" "${startdir}/${install}" > "${startdir}/${install}.pkg"
  true && install=${install}.pkg

  # install mkinitcpio preset file
  sed "${_subst}" ../linux-lts.preset |
    install -Dm644 /dev/stdin "${pkgdir}/etc/mkinitcpio.d/${pkgbase}.preset"

  # install pacman hooks
  sed "${_subst}" ../60-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/60-${pkgbase}.hook"
  sed "${_subst}" ../90-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/90-${pkgbase}.hook"
}

_package-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"

  cd ${_srcname}
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile

  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/x86" -m644 arch/x86/Makefile
  install -Dt "${_builddir}/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  cp -t "${_builddir}/arch/x86" -a arch/x86/include

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  # copy in Kconfig files
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "${_builddir}/tools/objtool" tools/objtool/objtool

  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */x86/ ]] && continue
    rm -r "${_arch}"
  done

  # remove files already in linux-docs package
  rm -r "${_builddir}/Documentation"

  # remove now broken symlinks
  find -L "${_builddir}" -type l -printf 'Removing %P\n' -delete

  # Fix permissions
  chmod -R u=rwX,go=rX "${_builddir}"

  # strip scripts directory
  local _binary _strip
  while read -rd '' _binary; do
    case "$(file -bi "${_binary}")" in
      *application/x-sharedlib*)  _strip="${STRIP_SHARED}"   ;; # Libraries (.so)
      *application/x-archive*)    _strip="${STRIP_STATIC}"   ;; # Libraries (.a)
      *application/x-executable*) _strip="${STRIP_BINARIES}" ;; # Binaries
      *) continue ;;
    esac
    /usr/bin/strip ${_strip} "${_binary}"
  done < <(find "${_builddir}/scripts" -type f -perm -u+w -print0 2>/dev/null)
}

_package-docs() {
  pkgdesc="Kernel hackers manual - HTML documentation that comes with the ${pkgbase/linux/Linux} kernel"

  cd ${_srcname}
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  mkdir -p "${_builddir}"
  cp -t "${_builddir}" -a Documentation

  # Fix permissions
  chmod -R u=rwX,go=rX "${_builddir}"
}

pkgname=("${pkgbase}" "${pkgbase}-headers" "${pkgbase}-docs")
for _p in ${pkgname[@]}; do
  eval "package_${_p}() {
    $(declare -f "_package${_p#${pkgbase}}")
    _package${_p#${pkgbase}}
  }"
done
