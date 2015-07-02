# OpenCV

## OpenCV 3

- [Install opencv3 w/python bindings brew](http://www.pyimagesearch.com/2015/06/15/install-opencv-3-0-and-python-2-7-on-osx/) Seems like python bindings for default brew install not yet working but this post shows how to do it with brew manually.

This command might work:

    brew install opencv3 --with-contrib --with-tbb

## projectpoints projecting 3d to 2d augmented reality

- [opencv tutorial pose estimation](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_calib3d/py_pose/py_pose.html) Draws axss & cube on image. Good.
- [pose estimation from planes & markers](https://www.safaribooksonline.com/library/view/programming-computer-vision/9781449341916/ch04.html) From Programming Computer Vision w/ Python. **GOOD EXAMPLES**
  - Section 4.3. I have this book. Project a cube onto image.
  - Section 4.4 talks about using pygame and opengl for augmented reality. They project a teapot onto the image with good detail. Might be a good way to do the 3d dic data.
  - Looks like best format for 3d objects is the [obj](https://en.wikipedia.org/wiki/Wavefront_.obj_file) format for using with opengl & pygame.
- [augmented reality with sphere](http://www.jera.com/jbrewer/2014/01/computer-vision-challenge-1-augmented-reality.html)

- [ArUco](http://www.uco.es/investiga/grupos/ava/node/26) Augmented reality library with python bindings. Uses opencv.

## Rigid body transform
- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform)

## Aligning 2 images

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) Takes two images and will give a rigid transform. Or takes two sets of points. **This seems good**.
- [warpAffine](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#void%20warpAffine(InputArray%20src,%20OutputArray%20dst,%20InputArray%20M,%20Size%20dsize,%20int%20flags,%20int%20borderMode,%20const%20Scalar&%20borderValue) Then use this function to apply the transform. Could also use this to take out camera shake since it would also do rotation, would need to compare with my sub pixel method which only does translation.

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) finds affine transform between points in two images.

## Dense optical flow

- [Dense optical flow python tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_lucas_kanade/py_lucas_kanade.html) See end of tutorial for dense.
