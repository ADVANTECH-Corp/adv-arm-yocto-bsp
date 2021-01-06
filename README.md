Advantech BSP for NXP i.MX Series
==================================

imx-manifest manifest repository with Advantech layer

This repository is based on [imx-manifest](https://source.codeaurora.org/external/imx/imx-manifest), and add Advantech add-on features.
For details about original imx-manifest, you can check [README](https://source.codeaurora.org/external/imx/imx-manifest/tree/README?h=imx-linux-zeus) file.

Supported boards
----------------
i.MX8 Series
- ROM-7720 A1
- ROM-5720 A1
- ROM-5721 A1
- ROM-5620 A1
- ROM-3620 A1
- RSB-3720 A1


BSP Source
----------

Install the **repo** utility: (only need to do this once)
```
mkdir ~/bin
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo  > ~/bin/repo
chmod a+x ~/bin/repo
PATH=${PATH}:~/bin
```

Create your own BSP folder
```
mkdir <BSP folder>
cd <BSP folder>
```

Get the latest Yocto BSP
```
repo init -u git://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-linux-zeus -m imx-5.4.70-2.3.0.xml
```

Or, you can get the specific version of BSP
```
repo init -u git://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-linux-zeus -m imx8LBVA0001.xml
```

Finally, pull down the BSP
```
repo sync
```

Setup Environment
-----------------

MACHINE values can be:

- imx8qmrom7720a1
- imx8mqrom5720a1
- imx8mmrom5721a1
- imx8qxprom5620a1
- imx8qxprom3620a1
- imx8mprsb3720a1

DISTRO values can be:

- fsl-imx-xwayland 	Wayland with X11 support - default distro
- fsl-imx-wayland	Wayland
- fsl-imx-x11		(not supported for mx8)
- fsl-imx-fb		(not supported for mx8)

```
DISTRO=<distro> MACHINE=<machine> source ./imx-setup-release.sh -b build
```

By default, we adopt **fsl-imx-xwayland** DISTRO.

To continue one existed build environment
```
source ./setup-environment build
```

Images
------

NXP provides the following images. Currently, we adopt **imx-image-full** by default.
- imx-image-core - core image with basic graphics and no multimedia
- imx-image-multimedia - image with multimedia and graphics
- imx-image-full - image with multimedia and machine learning and Qt

To build the image, run
```
bitbake imx-image-full
```

To build kernel only, run
```
bitbake linux-imx
```

To build bootloader, run
```
bitbake u-boot-imx
```

