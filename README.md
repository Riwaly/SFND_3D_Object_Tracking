# SFND_3D_Object_Tracking
Detect and classify objects using YOLOv3, cluster Lidar point cloud, detect and match Camera keypoint descriptors and track 3D object.
Lidar and image fusion

FinalProject_Camera.cpp
- Line 39, imgStepWidth is to decrease the frame rate(currently 10 images per second). We can skip every alternate image or so to have considerable changes in keypoints between frames. Currently, with imgStepWidth = 1, we are going through every image. This should be played with.
- Line 75, Set bVis to true only wherever required otherwise it will vizualize everything and will be messy
- Line 89, note that the images are not converted to gray scale. The color images are directly pushed into dataBuffer. This is because YOLO is trained on color images. The image is converted to grayscale at line 148 before detecting keypoints
- Line 101 and 102, Play with confThreshold and nmsThreshold
- Line 117, Here the focus is only on ego lane, mainly by maxY
- Line 233 to 251, gives two pointers to matched bounding boxes

TO DO
- Line 155, Add more keypoint detectors.
- Line 188, Add more algo to find keypoint descriptors.
- Line 206, matchDescriptors should be extended

ASSIGNMENT
- Line 221, matchBoundingBoxes takes previous data buffer, current data buffer and outputs a map, bbBestMatches, which contains the index numbers of matching bounding boxes between two time steps
- Line 259, computeTTCLidar, takes lidar points associated to current and previous matched bounding boxes and outputs TTC
- Line 266, clusterKptMatchesWithROI, associates key point matches to current bounding box. For calculating TTC, we need keypoints which are enclosed by a bounding box
