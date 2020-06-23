I don't use this PKGBUILD anymore as linux-surface repo now provides builds for Arch. Take a look at [here](https://github.com/linux-surface/linux-surface/tree/master/pkg/arch) for linux-surface's PKGBUILD.

## linux-surface for Arch Linux lts419 kernel with personal patches

Note: linux-surface project now provides prebuilt kernel for Arch Linux (https://github.com/linux-surface/linux-surface/releases). \
This repo provides PKGBUILD with personal modifications.

- Based on Arch Linux linux-lts kernel 4.19.y
- Intended for **Surface Book 1 (especially, with Performance Base)** and **Surface 3**, but all patches (or equivalent) from [linux-surface repository](https://github.com/linux-surface/linux-surface) are applied
- I will apply my modifications on top of Arch Linux official commit.
- Patch files will be retrieved from my patches repository: [kitakar5525/linux-surface-patches](https://github.com/kitakar5525/linux-surface-patches)

See also:
- [kitakar5525/note-linux-on-surface-book-1: Notes to use Linux on Surface Book 1 with Performance Base](https://github.com/kitakar5525/note-linux-on-surface-book-1)
- [kitakar5525/note-linux-on-surface-3: Notes to use Linux on Surface 3](https://github.com/kitakar5525/note-linux-on-surface-3)



### How to build

```bash
git clone --depth 1 https://github.com/kitakar5525/arch-kernel-linux-surface
cd arch-kernel-linux-lts419-surface/trunk
makepkg -sC
```

### About branches
- master branch \
tracking Arch Linux packages/linux-lts branch \
(`git pull https://git.archlinux.org/svntogit/packages.git packages/linux-lts`)

- linux-surface branch \
where modifications will be made. I'll use "trunk" directory.
