Advantech BSP for NXP i.MX Series
==================================

imx-manifest manifest repository with Advantech layer

This repository is based on [imx-manifest](https://source.codeaurora.org/external/imx/imx-manifest), and add Advantech add-on features.
For details about original imx-manifest, you can check [README](https://source.codeaurora.org/external/imx/imx-manifest/tree/README?h=imx-linux-sumo) file.

Supported boards
----------------
i.MX8 Series
- ROM-7720 A1
- ROM-5720 A1
- ROM-5620 A1

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
repo init -u git://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-linux-sumo -m imx-4.14.98-2.0.0_ga.xml
```

Or, you can get the specific version of BSP
```
repo init -u git://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-linux-sumo -m imx8LBV90001.xml
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
- imx8qxprom5620a1

DISTRO values can be:

- fsl-imx-xwayland
- fsl-imx-wayland
- fsl-imx-x11	(not supported for mx8)
- fsl-imx-fb	(not supported for mx8)

```
DISTRO=<distro> MACHINE=<machine> source ./fsl-setup-release.sh -b build
```

By default, we adopt **fsl-imx-xwayland** DISTRO.

To continue one existed build environment
```
source ./setup-environment build
```

Images
------

NXP provides the following images. Currently, we adopt **fsl-image-validation-imx** by default.
- fsl-image-machine-test
- fsl-image-validation-imx
- fsl-image-qt5-validation-imx

To build the image, run
```
bitbake fsl-image-validation-imx
```

To build kernel only, run
```
bitbake linux-imx
```

To build bootloader, run
```
bitbake u-boot-imx
```

