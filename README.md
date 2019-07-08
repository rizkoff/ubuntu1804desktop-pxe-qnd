# ubuntu1804desktop-pxe-qnd
u1804 desktop PXE install quick-and-dirty steps


[Configuring PXE Network Boot Server on Ubuntu 18.04 LTS](https://linuxhint.com/pxe_boot_ubuntu_server/)
```console
$ sudo apt install -y syslinux pxelinux
$ sudo cp -v /usr/lib/PXELINUX/pxelinux.0 /tftp/boot/
$ sudo cp -v /usr/lib/syslinux/modules/bios/{ldlinux.c32,libcom32.c32,libutil.c32,vesamenu.c32} /tftp/boot/

$ wget http://releases.ubuntu.com/18.04/ubuntu-18.04.2-desktop-amd64.iso
$ sudo mount -o loop ubuntu-18.04.2-desktop-amd64.iso /mnt
$ sudo mkdir -p /var/www/html/desktop/bionic
$ sudo cp -Rfv /mnt/* /var/www/html/desktop/bionic/
$ sudo cp /var/www/html/desktop/bionic/casper/{vmlinuz,initrd} /tftp/boot/casper/

echo "now set static ip:"
...
...
$ sudo apt update && sudo apt install -y dnsmasq
```

```console
$ huck /etc/dnsmasq.conf
$ sudo systemctl (restart | status) dnsmasq
```

```console
$ sudo apt install -y nfs-kernel-server

$ huck /etc/exports
$ sudo exportfs -a

$ sudo mkdir /tftp/boot/pxelinux.cfg
$ huck /tftp/boot/pxelinux.cfg/default
```
```console
$ sudo chmod -Rfv 777 /tftp
$ ls -AR /tftp
/tftp:
boot

/tftp/boot:
casper  ldlinux.c32  libcom32.c32  libutil.c32  pxelinux.0  pxelinux.cfg  vesamenu.c32

/tftp/boot/casper:
filesystem.manifest                 filesystem.manifest-remove  filesystem.squashfs      initrd
filesystem.manifest-minimal-remove  filesystem.size             filesystem.squashfs.gpg  vmlinuz

/tftp/boot/pxelinux.cfg:
default
```

[Ubuntu 18.04 – How to install Ubuntu 18.04 Server through PXE – Part I](http://c-nergy.be/blog/?p=13191)
```console
$ echo "instead of nfs..."
$ sudo apt-get install apache2
$ sudo systemctl {start,status} apache2 
```
[/tftp/boot/ubuntu-installer/amd64/boot-screens/txt.cfg & /boot/grub.cfg: Ubuntu 18.04 – install Desktop through PXE – Part II](http://c-nergy.be/blog/?p=13243)

[Hosting Ubuntu 16.04 Desktop Live Install ISO on a PXE netboot server (BIOS and UEFI simultaneously)](https://www.downtowndougbrown.com/2017/03/hosting-ubuntu-16-04-desktop-live-install-iso-on-a-pxe-netboot-server-bios-and-uefi-simultaneously/)



