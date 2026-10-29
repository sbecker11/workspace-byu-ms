# Interactive Morphometrics from Three-Dimensional Surface Images

Research by Shawn C. Becker with William A. Barrett, Department of Computer Science, Brigham Young University, 1989–1990. Two papers from that work are in this repository. The first measures anatomy directly on rendered 3-D surfaces. The second segments myocardial tissue in Cine CT.

**Skills:** 3D Medical Imaging · Scientific Visualization · Surface Rendering · Volume Visualization · Depth Buffers · Interactive Morphometrics · Surface Extraction · Cine CT · Probabilistic Segmentation · Deterministic Relaxation · Bayesian Labeling · Medical Image Segmentation

Source: [scholarsarchive.byu.edu/facpub/733](https://scholarsarchive.byu.edu/facpub/733)

## Surface images

A surface image is a rendered view of a surface inside a 3-D image volume. The pipeline has four steps: format the volume as a cubic voxel array, segment object from background, track the object surface, and render one or more views. The surface description stores the position and orientation of each voxel face on the boundary. Density-gradient shading then builds the displayed intensity on that description, so the picture can show detail finer than the discrete surface itself.

Rendering is too slow for the interaction rate the tools need, so a matrix of tilts and spins is rendered ahead of time. The user picks a view from that set. Each view keeps a depth buffer and the inverse of its view transform, which turns a pixel back into a world coordinate on the surface.

## Interactive morphometric tools

Points, linear probes, curves, planes, and volumes are placed on or through the surface and composited with the depth buffer. A click deposits a surface point. Dragging moves it along the surface. The point stays attached to the anatomy when the view changes, because its world coordinate is stored and sent back through that view's transform. Beads, drawn with their own depth, make the points visible against the anatomy.

World coordinates can be reported in voxels or centimeters. A surface normal can be taken from the depth-buffer gradient, from the surface description, or by resampling neighboring voxels. When a finer position is needed, a convolution over the gray values of neighboring voxels locates the boundary inside the voxel column. The same tools measure surface dimensions and partial volumes, and they can section the surface so anatomy is seen in context.

## Myocardial segmentation

Jerome A. Broekhuijsen, Shawn C. Becker, and William A. Barrett adapted a probabilistic segmentation model from abdominal CT to myocardial tissue in Cine CT. The method is deterministic relaxation. For each pixel it combines a density term with a label term that depends on neighboring labels, then assigns the pixel to the class with the highest probability and repeats until the labeling settles.

Six classes are used: myocardium, blood, bone, interstitial tissue, miscellaneous tissue, and lung. Initial priors for position and density come from hand-painted training images. A new segmentation can be added back into that training set. Density is normalized between lung and bone. Scans are aligned to the spinal canal and the top of the heart wall, and scaled by subsampling so the normalization does not invent new densities.

**Skills:** Cine CT · Myocardial Segmentation · Deterministic Relaxation · Bayesian Labeling · Position and Density Priors · Neighborhood Interaction · Six-class Tissue Labeling · CT Density Normalization · Landmark Alignment · Training-set Construction

## Papers

- Shawn C. Becker and William A. Barrett, *Interactive Morphometrics from Three-Dimensional Surface Images*, IEEE Proceedings of the First Conference on Visualization in Biomedical Computing, pp. 418–425, May 1990. A local copy is `interactive-morphometrics.pdf`. [ScholarsArchive](https://scholarsarchive.byu.edu/facpub/733).
- Jerome A. Broekhuijsen, Shawn C. Becker, and William A. Barrett, *Probabilistic Segmentation of Myocardial Tissue by Deterministic Relaxation*, IEEE Proceedings of Computers in Cardiology, Jerusalem, September 1989. The local file `myocardial-segmentation-scholarsarchive.pdf` is the ScholarsArchive record. [ScholarsArchive](https://scholarsarchive.byu.edu/facpub/738).

## Keywords

3-D medical imaging, scientific visualization, surface rendering, volume rendering, voxel arrays, segmentation, surface tracking, density gradient shading, depth buffer, z-buffer compositing, interactive morphometrics, surface points, linear probes, view transforms, sub-voxel localization, surface normals, partial volumes, Cine CT, myocardial tissue, deterministic relaxation, Bayesian labeling, probabilistic segmentation.
