2019-03-20

Yocto 2.5 (sumo). Changes were needed in poky, meta-freescale andi
meta-freescale-3rdparty that will be removed once 2.6 (Thud) support is
available in meta-balena.

meta-freescale:
* Add v4.20 kernel recipe
* Add dtc-1.4.5 needed for u-boot

poky:
* Upgrade to dtc 1.4.6 (needed by v4.20 kernel in meta-freescale-3rdparty)
* Use olddefconfig as oldnoconfig has been removed from the v4.20 kernel

meta-rust:
* Workaround a strange build error that only happens with BalenaOS.

meta-resin:
* Fix kernel-module-headers compilation
* Create /etc/resin-supervisor directory so the corresponding bind rule succeeds
* initrdscripts: Adapt to support non-ext4 filesytems for resin-state
* image_types_resin: Generalize RESIN_HOSTAPP_IMG extension

meta-freescale-3rdparty:
* Add resin boot images to ubifs boot image [REVIEW].

meta-resin-digi-connectcore:
* Add skeleton structure following documentation and meta-resin-raspberrypi
* Modify u-boot-digi for BalenaOS
* Clean packagegroup-resin of uneeded ext4/msdos packages
* Initialize state and data partitions if needed
* Add udev rules to mount state and data partitions
* Add a image_types_resin_ubifs class to create UBIFS images

