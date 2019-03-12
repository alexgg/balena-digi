#  balena-digi-connectcore repository

## Clone/Initialize the repository

There are two ways of initializing this repository:
* Clone this repository with:

    git clone --recursive

or

* Run

    git clone

and then

    git submodule update --init --recursive

This will bring in all the needed dependencies.

## Build information

### Build flags

* Consult layers/meta-resin/README.md for info on various build flags (setting
up serial console support for example) and build prerequisites. Build flags can
be set by using the build script (barys) or by manually modifying `local.conf`.

See below for using the build script.

### Build this repository

* Run the build script:
  `./balena-yocto-scripts/build/barys`

For a development image with a console, use the "-d" flag as in:

  `./balena-yocto-scripts/build/barys -d`

* You can also run barys with the -h switch to inspect the available options

### Custom build using this repository

* Run the build script in dry run mode to setup an empty `build` directory
    `./balena-yocto-scripts/build/barys --remove-build --dry-run`

* Edit the `local.conf` in the `build/conf` directory

* Prepare build's shell environment
    `source layers/poky/oe-init-build-env`

* Run "MACHINE=<machine_name> bitbake resin-image" (see message outputted when you sourced above for examples)

## Programming the images at manufacturing

    `nand erase.chip`
    `update uboot tftp u-boot-<machine>.imx`
    `reset`
    `env default -a`
    `env set serverip <serverip_addr>`
    `env set ipaddr <target_ipaddr>`
    `env save`
    `update resin-boot tftp resin-image-<machine>.boot.ubifs`
    `nand erase.part resin-rootA`
    `ubi part resin-rootA`
    `ubi createvol resin-rootA`
    `update resin-rootA tftp resin-image-<machine>.hostapp-ubifs`
    `boot`

## Contributing

### Issues

For issues we use an aggregated github repository available [here](https://github.com/balena-os/meta-balena/issues). When you creaste issue make sure you select the right labels.

### Pull requests

To contribute send github pull requests targeting this repository.

Please refer to: [Yocto Contribution Guidelines](https://wiki.yoctoproject.org/wiki/Contribution_Guidelines#General_Information)
