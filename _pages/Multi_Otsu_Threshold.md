---
autogenerated: true
title: Multi Otsu Threshold
layout: page
categories: Plugins,Segmentation
description: test description
---

{% include info-box software='ImageJ' name='Multi Otsu Threshold' author='Yasunari Tosa' filename='Multi\_OtsuThreshold.class' source=' [Multi\_OtsuThreshold.java](https://imagej.net/plugins/download/Multi_OtsuThreshold.java)' released='14 April 2006' status='stable' category='[Segmentation](Category_Segmentation)' website='https://imagej.net/plugins/multi-otsu-threshold.html' %}

Purpose
-------

This plugin segments the image in classes by thresholding. It uses the same algorithm found in [Otsu Thresholding](Otsu_Thresholding), but was adapted to output more than 2 classes out of the process.

Documentation
-------------

This plugin implements an algorithm described in the following paper {% include citation last='Liao' first='P-S.' last2='Chen' first2='T-S.' last2='Chung' first2='P-C.' title='A fast algorithm for multilevel thresholding' journal='Journal of Information Science and Engineering' volume='17' issue='5' pages='713-727' date='September 2001' url='http://www.iis.sinica.edu.tw/page/jise/2001/200109\_01.pdf' %}

A thresholding algorithm will typically classify pixels in two classes (or two set of objects): the one that have their intensity lower than a certain threshold (generally, the background), and the other (the interesting features). This plugin is based on the [Otsu Thresholding](Otsu_Thresholding) technique, adapted to generate *multiple* thresholds and *multiple* classes from one single image.

For example, by setting the desired number of classes to 3 (the algorithm then needs to find 2 thresholds), one can get background pixels, bright pixels and intermediate pixels. This might be of interest for images where there is such a pixel populations. In the example depicted below, based on the blob image, one could get the background, the blobs center and the blob edges out of it.


{% capture content%}

{% endcapture %}
{% include gallery content=content%}


 
