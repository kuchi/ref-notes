# OpenCV

- [Python tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_tutorials.html)
- [Python examples](https://github.com/Itseez/opencv/tree/master/samples/python2)

**Install OpenCV3:** This seems to work (default brew does not have python bindings but building this way does it). However, may just need to run last command on default brew install.

    brew update
    brew install opencv3 --with-contrib --with-tbb
    # Then it should tell you to run
    echo /usr/local/opt/opencv3/lib/python2.7/site-packages >> /usr/local/lib/python2.7/site-packages/opencv3.pth
    
- [manual opencv3 install os x](http://www.learnopencv.com/install-opencv-3-on-yosemite-osx-10-10-x/)

## Aligning 2 images

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) Takes two images and will give a rigid transform. Or takes two sets of points. **This seems good**.
- [warpAffine](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html) Then use this function to apply the transform. Could also use this to take out camera shake since it would also do rotation, would need to compare with my sub pixel method which only does translation.

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) finds affine transform between points in two images.


## Camera Calibration

- [Python camera calibration tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_calib3d/py_table_of_contents_calib3d/py_table_of_contents_calib3d.html)

- The object points spacing can be arbitrary or they can be in the physical units you want. See [this tutorial](http://www.aishack.in/tutorials/calibrating-undistorting-with-opencv-in-c-oh-yeah/) for info on the calibration and object units.

- You should do an undistored image using `undistort` to see if the calibration looks correct. If the chess board / image looks distorted you know something is wrong.

- Get undistorted points with `undistortPoints` or an undistorted image with `undistort`. 

- Calibration Tips
	- [good notes here](https://mackiemathew.wordpress.com/tag/opencv/) 

- Camera pose estimation from matching points
	- [python matching with epipolar lines and essential matrix](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_calib3d/py_epipolar_geometry/py_epipolar_geometry.html#epipolar-geometry) great example
	- [Python tutorial of matching that may be useful](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_matcher/py_matcher.html#matcher) and [this tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_feature_homography/py_feature_homography.html#feature-homography)
	- [Python example of stereo matching](https://github.com/Itseez/opencv/blob/master/samples/python2/stereo_match.py) 
	- [SO discussion](http://stackoverflow.com/questions/8197107/opencv-camera-pose-estimation) Helpful links
	- [opencv discussion](http://answers.opencv.org/question/8179/feature-points-stereo-matching/)
	- [SO disussion](http://stackoverflow.com/questions/9026567/3d-reconstruction-from-2-images-without-info-about-the-camera)
	

## Contour Features

- [python tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_contours/py_contour_features/py_contour_features.html) covers moments, bounding boxes, areas, fitting line, fitting elite.
- moments / center of mass / area: See [this example](https://github.com/abidrahmank/OpenCV2-Python/blob/master/Official_Tutorial_Python_Codes/3_imgproc/moments.py). You can get area from the moments function `cv2.moments(cnt)[m00] ` or use `cv2.contourArea(cnt)`

## Dense optical flow

- [Dense optical flow python tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_lucas_kanade/py_lucas_kanade.html) See end of tutorial for dense.

## Projecting 3d to 2d points augmented reality

- main function `projectpoints`
- [opencv tutorial pose estimation](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_calib3d/py_pose/py_pose.html) Draws axss & cube on image. Good.
- [pose estimation from planes & markers](https://www.safaribooksonline.com/library/view/programming-computer-vision/9781449341916/ch04.html) From Programming Computer Vision w/ Python. **GOOD EXAMPLES**
	- Section 4.3. I have this book. Project a cube onto image.
  	- Section 4.4 talks about using pygame and opengl for augmented reality. They project a teapot onto the image with good detail. Might be a good way to do the 3d dic data.
  - Looks like best format is for 3d objects is the [obj](https://en.wikipedia.org/wiki/Wavefront_.obj_file) format for using with opengl & pygame.
- [augmented reality with sphere](http://www.jera.com/jbrewer/2014/01/computer-vision-challenge-1-augmented-reality.html)

- [ArUco](http://www.uco.es/investiga/grupos/ava/node/26) Augmented reality library with python bindings. Uses opencv.


## Rigid body transformation
- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform): TODO: See how this compares to my implementation.

## Finding Fiducials / Markers

- key point matching is probably the best way. This can be rotation and scale invariant.

- [Python fiducial finding code](https://github.com/mattvenn/fiducial)
- [Try ORB detector](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_orb/py_orb.html)
- [Python feature detection tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_table_of_contents_feature2d/py_table_of_contents_feature2d.html)
- [tips for finding markers](http://iplimage.com/blog/cv-img-tec-black-white-marker-detection/)
- [comparison of feature discriptors](http://computer-vision-talks.com/articles/2011-01-04-comparison-of-the-opencv-feature-detection-algorithms/)