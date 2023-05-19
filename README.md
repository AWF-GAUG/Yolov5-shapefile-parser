# Yolov5-shapefile-parser
This is a shapefile parser for the creation of yolov5 readable textfiles.

## Setup environment
1. Create conda environment.
2. Activate environment.
3. Run: conda install pip
4. Go to project environment and run pip install -r requirements.txt

## Set up
### Files
This parser uses jpg-images and polygons stored as ArcGIS shapefiles (.shp). Make sure that there is one shapefile for each image containing the boundaries of all objects within the image as polygons. 
In order to run this parser the file names must be set in the following way (see examples below). The coordinates of the extend of the images are stored in the image names. The code expects these coordinates in millimeter. Consequently, multiply original coordinates by 1000 beforehand. 
The first position in the image- and the corresponding shape file names must be a ID.
**Structure Image Names**
_ID_xminmm_xmincoords_xmaxmm_xmaxcoords_ymincm_ymincoords_ymaxcm_ymaxcoords_.jpg
**Example Image Names**
_100_xminmm_480500000_xmaxmm_480600000_ymincm_5601100000_ymaxcm_5601200000_.jpg
**Example Corresponding Shapefile**
_100_..._.shp

If you want to store object id and object class (e.g. species) in the final text files you need to store both information as numeric in attribute fields in the shape files. Name those fields "treeID" and "species_id". Or change ll. 42 and 56 in the parser script accroding to your data.

### Folder structure
Create an output folder and store two empty folders inside. Name those folders "box" and "poly".

## Run shapefile parser
Activate conda environment. Got to the script and run:

`python yolo_shapefileparser.py --imagepath "PATH/TO/IMAGES" --shapepath "PATH/TO/SHAPEFILES" --outpath "PATH/TO/OUTPUTFOLDER" --imagesize 640 --attributes False`

For help run:
`python yolo_shapefileparser.py --help` 
