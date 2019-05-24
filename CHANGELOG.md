2019-11-12

Yocto 2.7 (warrior)

TBC

2019-05-22

Yocto 2.6 (thud)

meta-resin:
* Create /etc/resin-supervisor directory so the corresponding bind rule succeeds
* initrdscripts: Adapt to support non-ext4 filesytems for resin-state
* image_types_resin: Generalize RESIN_HOSTAPP_IMG extension

poky:
* Use olddefconfig as oldnoconfig has been removed from the v4.20 kernel

meta-resin:
* Create /etc/resin-supervisor directory so the corresponding bind rule succeeds
* initrdscripts: Adapt to support non-ext4 filesytems for resin-state
* image_types_resin: Generalize RESIN_HOSTAPP_IMG extension

meta-balena-digi:
* Add skeleton structure following documentation and meta-resin-raspberrypi
* Modify u-boot-digi for BalenaOS
* Clean packagegroup-resin of uneeded ext4/msdos packages
* Initialize state and data partitions if needed
* Add udev rules to mount state and data partitions
* Add a image_types_resin_ubifs class to create UBIFS images

meta-freescale-3rdparty:
* image_types_bbclass: Add resin boot images
* images_types_digi: boot.ubifs: Allow for initramfs bundled kernels
* image_types_digi: Add a boot.ubifs dependency on resin-image-initramfs
* layer.conf: Allow to use in thud

meta-freescale:
* Allow to use in thud
