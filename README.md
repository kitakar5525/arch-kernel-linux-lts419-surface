# linux-surface for Arch Linux linux-lts kernel

- Currently based on Arch Linux linux-lts kernel 4.19.x

- Intended for **Surface Book 1 (especially, with Performance Base)** and **Surface 3**, but all patches (or equivalent) from [jakeday repository](https://github.com/jakeday/linux-surface) are applied

- PKGBUILD is from [core/linux-lts](https://git.archlinux.org/svntogit/packages.git/log/trunk?h=packages/linux-lts)
	- `linux.preset` is modified not to create fallback initramfs. If you need it, rename `linux.preset.orig` to `linux.preset`

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



## Changelog

2019-03-05 4.19.26-2-lts419-surface
- Add 5527-modToJake-ipts-revert-suspend-resume-mechanism.patch

2019-03-02 4.19.26-1-lts419-surface
- upgpkg: linux-lts 4.19.26-1: [svntogit/packages.git - Git clone of the 'packages' repository](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/linux-lts&id=a77b05c2b536a4e35c1cd7926fa7854923b37fd6)

2019-02-26 4.19.25-1-lts419-surface
- [updating 4.19 patches and config · jakeday/linux-surface@5d21cc8](https://github.com/jakeday/linux-surface/commit/5d21cc824c9b41e65f92fdebcbcccd2181b9393f)
- upstream update 4.19.25: [svntogit/packages.git - Git clone of the 'packages' repository](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/linux-lts&id=500ebf44cec6f575182b95ca75c32954f1e7231a)

Merged into jakeday repository:
- prevent-nvme-from-entering-D3.patch
- nvme-add-quirk-to-not-call-disable-function-when-suspending-for-powersaving.patch
- v3-platform-x86-surface3_power-MSHW0011-rev-eng-implementation.patch
- mwifiex-disable-dump-and-reset.patch

2019-02-18 4.19.23-2-lts419-surface
- [updating 4.19 patches · jakeday/linux-surface@2f1570d](https://github.com/jakeday/linux-surface/commit/2f1570d509eb7de8330ad4bc01b725c501ab9a8c)

2019-02-16 4.19.23-1-lts419-surface
- Arch Linux linux-lts: [upgpkg: linux-lts 4.19.23-1](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/linux-lts&id=41b1b5ca2b5460cf1e1793c4bf9b8a4267a6f794)
-  jakeday patchset: [updating 4.19 patches · jakeday/linux-surface@5b7dd5a](https://github.com/jakeday/linux-surface/commit/5b7dd5a7a9967c34f04c7108f5c7fbe326e261e2)
