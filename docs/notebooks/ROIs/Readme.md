# ROIs
(omero.rois)=

ROIs ([region of interest](https://en.wikipedia.org/wiki/Region_of_interest)) are OMERO's way of working with segmentation data. They are typically comprised of single or multiple polygons, unlike labels images, which many are probably more familiar with in the Python context. They come with the advantage of being very lightweight to use - but they need to converted into labels data to work with many other image analysis tools, such as scikit-image, for instance. This section explores the upload, download and conversion of ROIs from and to OMERO.

This section covers the following topics:

- [How to turn a segmentation in 2D into an OMERO ROI and upload it to OMERO](rois:saving_2d)
- [How to turn a segmentation in 3D into an OMERO ROI and upload it to OMERO](rois:saving_3d)
- [How to download an OMERO ROI and convert it into a segmentation in 2D](rois:loading_2d)
- [How to download an OMERO ROI and convert it into a segmentation in 3D](rois:loading_3d)