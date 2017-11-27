Freescale's Community Yocto BSP
===============================

Freescale's Community Yocto manifest repository with Advantech layer

This repository is based on [ADVANTECH-Corp/adv-arm-yocto-bsp](https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp/tree/imx-4.1-krogoth), and add additional EdgeSense feature.

BSP Source
----------

Create your own BSP folder first.
```
mkdir <BSP folder>
cd <BSP folder>
```

To get the latest version of Advantech meta layers, you can get without specific XML.
```
repo init -u https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-4.1-krogoth-EdgeSense
```

To get an official release version, you can assign the corresponding XML, e.g. imx6LBV8401.xml.
```
repo init -u https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git -b imx-4.1-krogoth-EdgeSense -m imx6LBV8401.xml
```

Finally, pull down the BSP by running
```
repo sync
```

