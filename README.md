# 3D-Reconstruction
Implementation of stereo-reconstruction algorithm. Reprojects points in relative 3D space using triangulation and stereo-matching from a pair of calibrated images.

## Algorithm
**Given:** Stereo-rectified pair of images, given camera intrinsics (K<sub>1</sub>, K<sub>2</sub>), point correspondences between left and right images, also given a set of 'identified features' (x<sub>1</sub>, y<sub>1</sub>) coordinate pairs corresponding to image1. 
A high-level overview of the algorithm is given below -
- Estimate Fundamental Matrix (F) using given point correspondences.
- Construct Essential Matrix (E) using F, K<sub>1</sub>, and K<sub>2</sub>.
- Implement stereo-matching to find features (x<sub>2</sub>, y<sub>2</sub>) in image2 that correspond to the same features in image1 by searching along the epi-line.
- Implement DLT triangulation using (x<sub>1</sub>, y<sub>1</sub>) and (x<sub>2</sub>, y<sub>2</sub>) to return the set of points which has the least reprojective errors.
- Constructing final camera matrices (which are used in DLT) C<sub>1</sub>, C<sub>2</sub> using intrinsics (K<sub>1</sub>, K<sub>2</sub>) and projective camera matrices (M<sub>1</sub>, M<sub>2</sub>).
  - M<sub>1</sub> and M<sub>2</sub> are [I | 0] and [R | t] respectively.
  - C<sub>1</sub> is fixed, since it is obtained using just M<sub>1</sub> and K<sub>1</sub>
  - Find all possible M<sub>2</sub>
  - Find best M<sub>2</sub> that gives the least triangulation error. 
- Triangulate points using best C<sub>2</sub> and plot.
      


## Results