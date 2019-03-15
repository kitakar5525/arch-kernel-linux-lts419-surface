# linux-surface for Arch Linux linux-lts kernel

- Currently based on Arch Linux linux-lts kernel 4.19.x

- Intended for **Surface Book 1 (especially, with Performance Base)** and **Surface 3**, but all patches (or equivalent) from [jakeday repository](https://github.com/jakeday/linux-surface) are applied

- PKGBUILD is from [core/linux-lts](https://git.archlinux.org/svntogit/packages.git/log/trunk?h=packages/linux-lts)
	- `linux.preset` is modified not to create fallback initramfs. If you need it, rename `linux.preset.orig` to `linux.preset`

- Patch files will be retrieved from my patches repository: [kitakar5525/linux-surface-patches](https://github.com/kitakar5525/linux-surface-patches)

- I may change some kernel configs. See [config.diff](config.diff)

See also:
- [kitakar5525/note-linux-on-surface-book-1: Notes to use Linux on Surface Book 1 with Performance Base](https://github.com/kitakar5525/note-linux-on-surface-book-1)
- [kitakar5525/note-linux-on-surface-3: Notes to use Linux on Surface 3](https://github.com/kitakar5525/note-linux-on-surface-3)



## How to build

```bash
git clone --depth 1 https://github.com/kitakar5525/arch-kernel-linux-lts419-surface
cd arch-kernel-linux-lts419-surface
makepkg -sC
```



## Status

Arch Linux linux-lts version
- upgpkg: linux-lts 4.19.29-1: [svntogit/packages.git - Git clone of the 'packages' repository](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/linux-lts&id=a7a513e585262b4611f87fccf81b611320e54b3b)

kitakar5525/linux-surface-patches version
- [Release v1.1 · kitakar5525/linux-surface-patches](https://github.com/kitakar5525/linux-surface-patches/releases/tag/v1.1)