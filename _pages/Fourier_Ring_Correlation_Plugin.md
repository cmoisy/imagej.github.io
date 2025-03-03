---
autogenerated: true
title: Fourier Ring Correlation Plugin
layout: page
categories: Plugins
description: test description
---

{% include info-box name='Fourier Ring Correlation' software='Fiji' author='Olivier Burri, Alex Herbert' maintainer='Olivier Burri' filename='FRC\_-1.0.2.jar' released='September 2016' latest-version='July 2018' source=' [github page](https://github.com/BIOP/ijp-frc)' status='stable' website=' [BIOP Staff Page](http://biop.epfl.ch/INFO_Facility.html#staff)' %}

Updates
=======

### January 2018

The plugin was moved to a new location, to help sort our plugins.

### July 2018

Following information kindly provided by Alex Herbert and Miguel Lermo, we have proceeded to correct the following bugs

1.  FRC\_ Plugin was added to package ch.epfl.biop.frc (instead of no package)
2.  POM was updated to use latest pom-scijava version
3.  FIRE number is now computed correctly by checking image size
4.  Images are ensured to be a multiple of two by adding one pixel of padding as needed
5.  Angles are converted to radians, ensuring a better radial sampling

These bugs were present in the first FRC code we had adapted for this plugin, and were recently brought to our attention. In case your images are not powers of two, check the value of the FIRE number as it might not be correct with the previous version of the code.

If you are using FRC to compare different images or conditions, and your images do not change size, then the relative differences are still perfectly valid, but absolute values might be off.

### June 2019

A remark from Brian Patton, University of Strathclyde, Glasgow says that the original computation for the numerator was wrong, namely: `code|numerator[i] = dataA1[i] * dataA2[i] + dataB1[i] * dataB2[i];` And should be instead: `abs((FFT(Image1)*Complex_Conj(FFT(Image2)))`

Purpose
=======

Making use of the Fourier Ring Correlation Implementation by Alex Herbert which is itself adapted from the FIRE (Fourier Image REsolution) plugin produced as part of the paper **Niewenhuizen, et al (2013). Measuring image resolution in optical nanoscopy. Nature Methods, 10, 557** [1]

Details
=======

Threshold Methods
-----------------

There are three threshold methods currently implemented

1.  **Fixed 1/7**: Finds the FIRE number when the FRC curve reaches a correlation value of 1/7.
2.  **Half-bit**: Threshold method where the intersection of the threshold curve with the FRC defines the point where there is 1/2 bit of information per pixel.
3.  **Three sigma**: The intersection of the FRC curve with this threshold defines the value where the FRC begins primarily representing high frequency noise.

Please see the publication **van Hell and Schatz, Fourier shell correlation threshold criteria, Journal of Structural Biology 151, 2005**[2] for more information on the calculation of these criteria.

Image Calibration
-----------------

We recommend you use a calibrated image so that your results are in calibrated units (microns, millimeters, etc..) directly. The plugin will always return both the non calibrated values and the calibrated ones as separate columns.

Installation
============

This plugin is available from the {% include list-of-update-sites content='PTBIOP Update Site' %} This places it in a "BIOP" Folder in the plugins directory of Fiji/ImageJ

Use
===

Direct Use
----------

<figure><img src="/media/Frc-dialog-std.png" title="Plugin Dialog choices Standard Use" width="500" alt="Plugin Dialog choices Standard Use" /><figcaption aria-hidden="true">Plugin Dialog choices Standard Use</figcaption></figure>

Call up the plugin using *Plugins-&gt;BIOP-&gt;Image Analysis-&gt;FRC-&gt;FRC Calculation...*.

You need two images open to perform the FRC.

Batch Mode
----------

<figure><img src="/media/Frc-dialog-batch.png" title="Plugin Dialog choices in Batch mode" width="500" alt="Plugin Dialog choices in Batch mode" /><figcaption aria-hidden="true">Plugin Dialog choices in Batch mode</figcaption></figure>

There is also a Batch Option under *Plugins-&gt;BIOP-&gt;Image Analysis-&gt;FRC-&gt;FRC Calculation (Batch)...*

This dialog needs two folders. The plugin will open one folder, and perform the FRC for each image that has an image in the second folder **with the same name**.

Results
=======

The plugin writes the FIRE (Fourier Image REsolution) number on a Results Table that gets appended as the plugin gets used. The column name reflects the calibration of the image and the threshold method selected.

<figure><img src="/media/Frc-results.png" title="Results Table example from FRC Calculation" width="500" alt="Results Table example from FRC Calculation" /><figcaption aria-hidden="true">Results Table example from FRC Calculation</figcaption></figure>

Plots
-----

The Plugin can display a plot of the FRC curve, along with the LOESS smoothed version of the curve. Finally it displays the threshold method used and the intersection of the FRC with the threshold, providing the FIRE number. The X dimension is in the frequency domain and represents pixels<sup>-1</sup>

<figure><img src="/media/Frc-results-curve.png" title="FRC Curve example using 1/7 Threshold condition" width="500" alt="FRC Curve example using 1/7 Threshold condition" /><figcaption aria-hidden="true">FRC Curve example using 1/7 Threshold condition</figcaption></figure>

In the case of batch processing, if *Save Plot* is checked, the plugin creates a new folder in the parent directory called "Graphs" and saves an over-sampled plot with the name of the image and threshold method.

Macro Recordable
================

Making use of the GenericDialog class, the plugin is macro-recordable. An example is shown below

    run("FRC Calculation...", "image_1=[first_image.tif] image_2=[second_image.tif] resolution=[Fixed 1/7] display");

    //Example with batch
    run("FRC Calculation (Batch)...", "first=[D:\\FRC Tests\\A] second=[D:\\FRC Tests\\B] resolution=[Fixed 1/7] save");

Running from a Plugin
=====================

If you would like to use the FRC class in your own plugin, you can either use the one from Alex Herbert on [GitHub](https://github.com/aherbert/GDSC-SMLM) if you're already using his excellent SMLM plugins. Otherwise you can use the one that was re-purposed here through the following import

    import ch.epfl.biop.frc.FRC;

And then use the FRC Class


    FRC frc = new FRC();

    // Get FIRE Number, assumes you have access to the two image processors.
    double fire = frc.calculateFireNumber(ip1, ip2, FRC.FIXED_1_OVER_7);

There are other methods to get the FRC curve, see the [FRC.java file](https://c4science.ch/diffusion/988/browse/master/src/main/java/ch/epfl/biop/frc/FRC.java), which was very well documented.

Notes
=====

References
----------



[1] {% include cite content='journal' issn='1548-7091' volume='10' issue='6' pages='557–562' last1='Nieuwenhuizen' first1='Robert P J' last2='Lidke' first2='Keith A' last3='Bates' first3='Mark' last4='Puig' first4='Daniela Leyton' last5='Grunwald' first5='David' last6='Stallinga' first6='Sjoerd' last7='Rieger' first7='Bernd' title='Measuring image resolution in optical nanoscopy' journal='Nat Meth' date='2013-06' %}

[2] {% include cite content='journal' doi='10.1016/j.jsb.2005.05.009' issn='1047-8477' volume='151' issue='3' pages='250–262' last1='van Heel' first1='Marin' last2='Schatz' first2='Michael' title='Fourier shell correlation threshold criteria' journal='Journal of Structural Biology' date='2005-09' %}
