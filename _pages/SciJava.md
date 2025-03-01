---
autogenerated: true
title: SciJava
layout: page
categories: 
description: test description
---

{% include project content='SciJava' %}
{% capture maintainer%}
{% include person content='Rueden' %}
{% endcapture %}
{% include info-box name='SciJava' software='SciJava' logo='<img src="/media/Scijava-logo.png" width="128"/>' author=' [SciJava consortium](https://scijava.org/)' maintainer=maintainer source=' [on GitHub](https://github.com/scijava)' status='Active' website='https://scijava.org/' %}SciJava is a collaboration of projects providing software for scientific computing—an effort to cooperate and reuse code when feasible.

The SciJava component collection
--------------------------------

The following component layers are part of the **[SciJava component collection](Architecture)**:

-   **SciJava** - foundational layer unspecific to image processing, including the [SciJava Common](SciJava_Common) shared library with powerful plugin framework and application container, and plugins built on it.
-   [ImgLib2](ImgLib2) - core libraries for N-dimensional image processing.
-   [SCIFIO](SCIFIO) - core libraries for N-dimensional image I/O.
-   [ImageJ2](ImageJ2) - core libraries and application for N-dimensional image processing.
-   [Fiji](Fiji) - "batteries-included" distribution of ImageJ, bundling a lot of plugins which facilitate scientific image analysis.
-   [BigDataViewer](BigDataViewer) - re-slicing browser and Fiji plugin for terabyte-sized multi-view image sequences
-   [TrakEM2](TrakEM2) - Fiji plugin suite for morphological data mining, three-dimensional modeling and image stitching, registration, editing and annotation.
-   [Bio-Formats](Bio-Formats) - libraries and ImageJ plugins for life sciences image format I/O.

All components in this collection are managed by SciJava's [Bill of Materials](Bill_of_Materials) to make it easier for downstream components to use them without version conflicts.

The SciJava pledge
------------------

The following projects are part of the **[SciJava pledge](Category_SciJava)** to work together, reuse code and synergize wherever possible:

<table><tbody><tr class="odd"><td style="text-align: center; vertical-align: middle"><p> {% include logo content='ImageJ2' %}</p></td><td style="text-align: center; vertical-align: middle"><p> <a href="CellProfiler"><img src="/media/Cellprofiler-logo.png" height="64px"/></a></p></td><td style="text-align: center; vertical-align: middle"><p><a href="KNIME"><img src="/media/Knime-logo.jpg" height="54px"/></a></p></td><td></td><td><p> <a href="OMERO"><img src="/media/Omero-logo.png" height="32px"/></a></p></td><td style="text-align: center; vertical-align: middle"><p><a href="https://github.com/scenerygraphics/scenery"><img src="/media/Scenery-logo.png" height="72px"/></a></p></td><td></td></tr><tr class="even"><td><p> {% include logo content='Fiji' %}</p></td><td style="text-align: center; vertical-align: middle"><p> <a href="Icy"><img src="/media/Icy-logo.png" height="48px"/></a></p></td><td style="text-align: center; vertical-align: middle"><p> {% include logo content='Micro-Manager' size='48px' %}</p></td><td style="text-align: center; vertical-align: middle"><p> {% include logo content='VCell' size='48px' %}</p></td><td style="text-align: center; vertical-align: middle"><p> <a href="Bio-Formats"><img src="/media/Bio-formats-logo.png" height="28px"/></a></p></td><td style="text-align: center; vertical-align: middle"><p> {% include logo content='Alida' size='48px' %}</p></td><td style="text-align: center; vertical-align: middle"><p> {% include logo content='MiToBo' size='48px' %}</p></td></tr></tbody></table>

See the [Architecture](Architecture) and [Governance](Governance) pages, as well as the [SciJava web site](https://scijava.org/), for further details.
