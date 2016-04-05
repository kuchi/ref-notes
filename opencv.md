# OpenCV

- [Python tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_tutorials.html)
- [Python examples](https://github.com/Itseez/opencv/tree/master/samples/python2)
- [Learn OpenCV blog](http://www.learnopencv.com) Excellent tutorials


**Install OpenCV3:** This seems to work (default brew does not have python bindings but building this way does it). However, may just need to run last command on default brew install.

    brew update
    brew uninstall opencv
    brew install opencv3 --with-contrib --with-tbb --with-qt
    brew install opencv3 --HEAD --with-cuda --with-contrib --with-tbb --with-qt
    # Then it should tell you to run
    echo /usr/local/opt/opencv3/lib/python2.7/site-packages >> /usr/local/lib/python2.7/site-packages/opencv3.pth
    
- [Conda opencv3 on binstar](https://binstar.org/search?q=opencv&sort=ndownloads) menlo package has it for all platforms.
- [manual opencv3 install os x](http://www.learnopencv.com/install-opencv-3-on-yosemite-osx-10-10-x/)

## Aligning 2 images
- [image alignment findTransformECC opencv3](http://www.learnopencv.com/image-alignment-ecc-in-opencv-c-python/) great tutorial and good new algorithm 

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) Takes two images and will give a rigid transform. Or takes two sets of points. **This seems good**.
- [warpAffine](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html) Then use this function to apply the transform. Could also use this to take out camera shake since it would also do rotation, would need to compare with my sub pixel method which only does translation.

- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform) finds affine transform between points in two images.

## Augmente Reality
-[ARToolkit](http://www.artoolkit.org/)

## Color Maps

- [Colormaps](http://www.learnopencv.com/applycolormap-for-pseudocoloring-in-opencv-c-python/) in opencv


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
	- [SO discussion](http://stackoverflow.com/questions/12468426/opencv-uncalibrated-camera-rectification-for-3d-reconstruction)
	- [8 point algorithm](https://books.google.com/books?id=J9b_CH-NrycC&pg=PA115&lpg=PA115&dq=normalized+eight+point+algorithm+python&source=bl&ots=BZ67VUeKss&sig=bqbScNgArZAeSK0Ycg28kDhls0U&hl=en&sa=X&ei=amuiVZT4OojsoATQ1Z7oAw&ved=0CCMQ6AEwAg#v=onepage&q=normalized%20eight%20point%20algorithm%20python&f=false) From Computer Vision with Python book
	

## Contour Features

- [python tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_contours/py_contour_features/py_contour_features.html) covers moments, bounding boxes, areas, fitting line, fitting elite.
- moments / center of mass / area: See [this example](https://github.com/abidrahmank/OpenCV2-Python/blob/master/Official_Tutorial_Python_Codes/3_imgproc/moments.py). You can get area from the moments function `cv2.moments(cnt)[m00] ` or use `cv2.contourArea(cnt)`

## Dense optical flow

- [Dense optical flow python tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_lucas_kanade/py_lucas_kanade.html) See end of tutorial for dense.

## Geometric Image Transformations
- [python tutorial on transformation](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_geometric_transformations/py_geometric_transformations.html) scaling, rotation, affine, perspective

## GUI

You can have mouse picking, see this example (may need to change key it checks for):
-[OpenCV python mouse click coord](https://github.com/abidrahmank/OpenCV-Python/blob/master/Other_Examples/mouse_callback.py)
-[OpenCV select & move points](https://ajithsrikukan.wordpress.com/2011/09/20/select-and-move-objectspoints-using-opencv-drag-and-drop/)

## Projecting 3d to 2d points augmented reality

- main function `projectpoints`
- [opencv tutorial pose estimation](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_calib3d/py_pose/py_pose.html) Draws axss & cube on image. Good.
- [pose estimation from planes & markers](https://www.safaribooksonline.com/library/view/programming-computer-vision/9781449341916/ch04.html) From Programming Computer Vision w/ Python. **GOOD EXAMPLES**
	- Section 4.3. I have this book. Project a cube onto image.
  	- Section 4.4 talks about using pygame and opengl for augmented reality. They project a teapot onto the image with good detail. Might be a good way to do the 3d dic data.
  - Looks like best format is for 3d objects is the [obj](https://en.wikipedia.org/wiki/Wavefront_.obj_file) format for using with opengl & pygame.
- [augmented reality with sphere](http://www.jera.com/jbrewer/2014/01/computer-vision-challenge-1-augmented-reality.html)

- [ArUco](http://www.uco.es/investiga/grupos/ava/node/26) Augmented reality library with python bindings. Uses opencv.

## Reprojection Errors

- To calculate, I think you just triangulate the points, then retroject back to a 2d point and find the difference from the original 2d point position. This would be the reprojection error.



## Tracking  / Finding Objects  / Optical Flow

- [Meanshift & Camshift](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_meanshift/py_meanshift.html) Meanshift just moves a or with the object movement. Camshift also figures out the rotation and scaling as the object moves.
- [python tutorial on opencv feature matching](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_matcher/py_matcher.html)

### Finding Fiducials / Markers

- key point matching is probably the best way. This can be rotation and scale invariant.
- May be best to just pick the fiducially, then track. Track with [Camshift](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_meanshift/py_meanshift.html)
- [Python fiducial finding code](https://github.com/mattvenn/fiducial)
- [Try ORB detector](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_orb/py_orb.html)
- [Python feature detection tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_feature2d/py_table_of_contents_feature2d/py_table_of_contents_feature2d.html)
- [tips for finding markers](http://iplimage.com/blog/cv-img-tec-black-white-marker-detection/)
- [comparison of feature discriptors](http://computer-vision-talks.com/articles/2011-01-04-comparison-of-the-opencv-feature-detection-algorithms/)

<<<<<<< HEAD
## Rigid body transformation
- [estimateRigidTransform](http://docs.opencv.org/3.0-beta/modules/video/doc/motion_analysis_and_object_tracking.html#estimaterigidtransform): TODO: See how this compares to my implementation.

## Sharpening images

- (detailEnhance algorithm)[http://www.learnopencv.com/non-photorealistic-rendering-using-opencv-python-c/] Provides amazing results. Better than unsharp mask. `dst = cv2.detailEnhance(src, sigma_s=10, sigma_r=0.15)`

## Tracking

-[Blob detection](http://www.learnopencv.com/blob-detection-using-opencv-python-c/) Has a lot of nice filtering parameters for size, circularity, shape, inertia (elliptical vs circular), convexity
=======
### Optical Flow

- [python optical flow tutorial](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_video/py_lucas_kanade/py_lucas_kanade.html)



## Sharpening

-[detailEnhance OpenCV3](http://www.learnopencv.com/non-photorealistic-rendering-using-opencv-python-c/) Very nice sharpening.
>>>>>>> 60a6cc3dffe588323257487ad645b8981c6b91e3
