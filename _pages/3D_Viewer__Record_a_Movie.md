---
autogenerated: true
title: 3D Viewer › Record a Movie
layout: page
categories: 
description: test description
---

(Return to the [Developer Documentation](3D_Viewer__Developer_Documentation) page)  
(Return to the main [3D\_Viewer](3D_Viewer) page)

How to animate the universe and create movies
---------------------------------------------

You can download example source code for this HowTo [here](3D_Viewer__Example_code).

It is very easy to animate the virtual universe and to record the animation, so that it can be stored as a video file and as such easily embedded into presentations.

The following lines show an easy example:

        // Add the image as a volume
        univ.addVoltex(imp);


        // animate the universe
        univ.startAnimation();


        // record a 360 degree rotation around the y-axis
        ImagePlus movie = univ.record360();
        movie.show();
        univ.pauseAnimation();

The call to the universe's `record()` method returns an `ImagePlus`, which consists of a stack of successive frames of a full 360 degree animation.

ImageJ provides methods to save such a stack for example as AVI file or as animated GIF.
