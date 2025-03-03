---
autogenerated: true
title: 3D Mathematical Morphology
layout: page
categories: 
description: test description
---

3D Mathematical Morphology
--------------------------

Various algorithms for 3D Mathematical Morphology, as part of the [3D ImageJ Suite](3D_ImageJ_Suite).

Author
------

{% include person content='Tboudier' %}

Description
-----------

3D mathematical **operations** (erosion, dilation, ...) are available in [3D Filters](3D_Filters) using minimum and maximum filters.

A 3D **Fill Holes** is available, works the same way as in 2D but will not fill holes if it is not closed in the Z dimension.

A 3D **Euclidean Distance Map** (also called *EDT*) is available that takes into account the calibration of the image stack. A 3D normalized distance map (called Eroded Volume Fraction, or **EVF**) is also available.

<img src="/media/Groom-raw.png" width="200"/><img src="/media/Groom-bin.png" width="200"/>

Left, raw image of a lymph node ((c) J. Groom, WEHI). Right, binary thresholded image.

<img src="/media/Groom-edt.png" width="200"/><img src="/media/Groom-evf.png" width="200"/>

Left, EDT image . Right, EVF image.

In the case of labelled objects (as count masks) a **Binary Close Labels** is available, that permits to perform closing on individual objects, hence avoiding objects to touch during the dilation operation.

<img src="/media/Ollion-raw.png" width="200"/><img src="/media/Ollion-seg.png" width="200"/><img src="/media/Ollion-closeLabels.png" width="200"/>

Nuclear regions ((c) J. Ollion, MNHN) : raw image, segmented labelled image, close labels image.

Download
--------

For details go to the [3D ImageJ Suite](3D_ImageJ_Suite).

Citation
--------

When using the *3D Mathematical Morphology* plugins for publication, please refer to :

J. Ollion, J. Cochennec, F. Loll, C. Escudé, T. Boudier. (**2013**) TANGO: A Generic Tool for High-throughput 3D Image Analysis for Studying Nuclear Organization. *Bioinformatics* 2013 Jul 15;29(14):1840-1. [doi](http://dx.doi.org/10.1093/bioinformatics/btt276)

License
-------

GPL distribution (see [license](https://cecill.info/licences/Licence_CeCILL_V2.1-en.html)). Sources are available freely.

Changelog
---------

-   30/03/2016 V3.74: bug fixed in EDT
