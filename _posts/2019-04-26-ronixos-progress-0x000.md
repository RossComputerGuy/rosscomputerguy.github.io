---
title: RonixOS Progress 0x000
layout: post
project: true
tags: ["RonixOS","Linux"]
excerpt: "On April 20th, I started working on a Linux distro designed from scratch. RonixOS right now doesn’t do much and isn’t bootable. I wrote 3 development tools..."
---

On April 20th, I started working on a Linux distro designed from scratch. RonixOS right now doesn't do much and isn't bootable. I wrote 3 development tools called `rxbuildpkg`, `rxbuildrepo`, and `rxstrap`. These commands allow me to compile packages, build a software repository, and generate a root filesystem which can be chroot'ed into. My current goal is to work my way up through all of the dependencies to get the Linux kernel usable and to have a bootable operating system using the GRUB 2 bootloader. So far, I've gotten about 40 packages compiled which includes bash, glibc, openssl, and a ton other packages. Today, I'll work on getting closer to have systemd working. For anyone who doesn't know what systemd is, it's an init daemon and an init daemon handles booting services and getting the operating system fully booted. For packages, I use a special file called `RXPKG` which contains variables and functions which tells `rxbuildpkg` how it should compile a package for the repository. Here's an example package:

```sh
pkgname=example
version=0.1.0
arch=x86_64
license="GPL-3.0"
maintainer="Someone"

build() {
  # Compile the package
}

package() {
  # Copy the files to $pkgdir
}
```
