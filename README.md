# ubuntu1804desktop-pxe-qnd
u1804 desktop PXE install quick-and-dirty steps

* ===================================
* ls -AR /tftp
* /tftp:
* boot

* /tftp/boot:
* casper  ldlinux.c32  libcom32.c32  libutil.c32  pxelinux.0  pxelinux.cfg  vesamenu.c32

* /tftp/boot/casper:
* filesystem.manifest                 filesystem.manifest-remove  filesystem.squashfs      initrd
* filesystem.manifest-minimal-remove  filesystem.size             filesystem.squashfs.gpg  vmlinuz

* /tftp/boot/pxelinux.cfg:
* default
* ===================================
