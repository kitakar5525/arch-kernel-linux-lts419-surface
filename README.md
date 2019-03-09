# linux-surface for Arch Linux linux-lts kernel

- Currently based on Arch Linux linux-lts kernel 4.19.x

- Intended for **Surface Book 1 (especially, with Performance Base)** and **Surface 3**, but all patches (or equivalent) from [jakeday repository](https://github.com/jakeday/linux-surface) are applied

- PKGBUILD is from [core/linux-lts](https://git.archlinux.org/svntogit/packages.git/log/trunk?h=packages/linux-lts)
	- `linux.preset` is modified not to create fallback initramfs. If you need it, rename `linux.preset.orig` to `linux.preset`

- I may change some kernel configs. See [config.diff](config.diff)

See also:
- [kitakar5525/note-linux-on-surface-book-1: Notes to use Linux on Surface Book 1 with Performance Base](https://github.com/kitakar5525/note-linux-on-surface-book-1)
- [kitakar5525/note-linux-on-surface-3: Notes to use Linux on Surface 3](https://github.com/kitakar5525/note-linux-on-surface-3)



## How to build

```bash
git clone --depth 1 https://github.com/kitakar5525/arch-kernel-linux-lts419-surface
cd arch-kernel-linux-surface
makepkg -sC
```



## patch filename prefix

- 4416
	- Indicate that the patch is not from me (Hayataka@kitakar5525)
- 552?
	- Indicate that the patch is made by me
- 4416-*552?
	- Indicate that the patch is from another person and modified by me



## Status

Arch Linux PKGBUILD
- upgpkg: linux-lts 4.19.27-1: [svntogit/packages.git - Git clone of the 'packages' repository](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/linux-lts&id=76a4922e0236cd10eeed71a97cfe40930740eea7)

jakeday patches
- [updating patches · jakeday/linux-surface@e09d9e1](https://github.com/jakeday/linux-surface/commit/e09d9e11f58281aec3780849cdaf9336579a4169)

Improve s0ix
- 4416-s0ix-01-5525-ipu_patches-419.patch, [201579 – HP Elite x2 1013 G3 unable to enter S0ix](https://bugzilla.kernel.org/show_bug.cgi?id=201579)
- [[v3,0/5] ICL support and other enhancements for PMC Core - Patchwork](https://patchwork.kernel.org/cover/10812541/)

Improve s0ix on Cherry Trail on 4.19
- [platform/x86: Add Intel AtomISP2 dummy / power-management driver · torvalds/linux@49ad712](https://github.com/torvalds/linux/commit/49ad712afa88c502831d37f7089d98eac441fb80)
- [pwm: lpss: Add ACPI HID for second PWM controller on Cherry Trail dev… · torvalds/linux@1688c87](https://github.com/torvalds/linux/commit/1688c8717118f37191d824862a006c8373d261de)

Surface 3 sound fix for OEMB devices
- 5525-sound-add-dmi-match-OEMB-for-affected-surface-3.patch