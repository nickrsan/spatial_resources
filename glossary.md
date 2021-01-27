# Introductory Glossary of GIS Terms
## GIS Generally
1.	**Spatial Data** – data with a geographic location, representation, or reference point that it describes.
2.	**Cartography** – the science of map making, including data inclusion, layout, elements, colors, and design. As much as it’s a science, it’s an art form.
3.	**Shapefile** – an Esri proprietary data format for storing geographic data. Very cross-GIS compatible, but limiting in many aspects. Often misused to mean any geographic dataset as in “could you send me that shapefile?”
4.	**Layer** – multiple meanings in a GIS context:
  a.	The distinct data elements that compose a map document, ordered one on top of the next for GIS drawing order (top is drawn last and seen first)
  b.	A single data element, saved into a GIS file format along with its associated symbology.
5.	**Scale** – the ratio of the size of elements on screen or in print on the map to their size in the real world
6.	**Raster** – spatial data that stores location based upon a single origin point and a data stream of known width, height, and resolution. Often used for continuous surfaces.
    1. **DEM – Digital Elevation Model**. A specific use case of raster data where the pixel value represents the elevation of areas covered by the pixel. Sometimes called a DTM (digital terrain model), DSM (Digital Surface Model), or DED (digital elevation dataset), depending upon which surface features are included in elevations.
7.	**Vector** – spatial data that stores location using Cartesian coordinate locations.
    1.	**Point** – A single spot in (usually) two dimensional space. Attributes represent only that location (and sometimes are inferred to represent nearby locations).
    2.	**Line (Polyline)** – Multiple points connected to represent all locations in between along the connection.
    3.	**Polygon** – Multiple polylines connected to create a boundary. Polygon zones are generalized representations where all locations contained within the boundaries are considered to have the same property.
8.	**Coordinate System/Spatial Reference** – defines the origin point, coordinate space, and geoid for a dataset’s spatial data
    1.	**Datum** – the origin point of the coordinate system and information required to accurately define an origin, like a surface model
    2.	**Geographic Coordinate System (GCS)** – A coordinate system that specifies latitude and longitude as coordinates
    3.	**Projected Coordinate System** – similar to and includes a GCS. “Projects”/transforms coordinates into a new coordinates system to display a map in 2D space. Sometimes referred to as “the projection” of a dataset.
9.	**Resolution** – the density of data of a raster dataset or rasterized map document. Sometimes used to mean the density of data in any dataset. For raster datasets, this value is expressed as the length of the side of a pixel (eg: 10m pixels). For rasterized graphic formats, it is most commonly expressed in pixels per inch of paper (ppi) or dots per inch of paper (dpi) and a good target to reach is 300 dpi for clear prints.
10.	**Geoprocessing** – the practice of using GIS tools to process, transform, filter, and query GIS data.
11.	**Python** – a programming language with capabilities for GIS analysis. Useful for automating tasks in GIS.
12.	**Join** – The use of a common attribute to link data tables in order to access the attributes of one along with the other or assign the attributes of one to the other based upon a key value. When this is the record ID of the other dataset, it’s often a foreign key. Eg:  summary statistics tables built for HUC12s, stored in separate datasets can be linked back to the HUC12 by the HUC12 ID.
13.	**Spatial Join** – Similar to a Join in that it transfers attributes, but the linkage used to connect the datasets is the location of each item. I find this to be the “hammer” of GIS.
14.	**Symbology** – the representation of a particular dataset in a map document.
15.	**Tables** – a data structure with a defined set of fields, and many rows representing individual data records.
    1.	**Fields (columns)** – a variable represented in a data table. Instances of this field can be looked up per record to find the value
    2.	**Rows** – individual data records
    3.	**Primary Key** – an identifier attribute, usually assigned automatically by the database management engine, that provides a unique integer value by which to reference a data record.
16.	**Environment Variables (Environments)** – variables/settings that affect the run of a geoprocessing tool. In other computer systems, variables that affect how programs are found and run.
17.	**Basemap** – a prerendered set of mapping data that can be placed below the data of interest to quickly create a map with context. Frequently, a basemap is served up over the Internet by a basemap server and loaded on the fly by your GIS.
18. **Tiles**

## ArcGIS-Specific
1.	**Feature Class** – data stored in an ESRI geodatabase. A feature class is a collection of features with the same geometry type, projection, and fields. Can be commonly thought of as a dataset.
2.	**File Geodatabase** – An Esri proprietary database format. Data stored within it is obfuscated and can only be accessed reliably from Esri software. Faster and more efficient than other storage methods and able to store huge datasets and large amounts of data overall.
3.	**Default Geodatabase** – The default location that ArcMap will use to save geoprocessing and export products. It saves you from always having to define locations for data. It is defined for each map document and can be changed upon loading the document, in map document properties, or in environment setttings.
4.	**Spatial Analyst** – An extension to ArcGIS that adds significant raster processing functionality. Many of the tools are useful for a watershed GIS workflow.
5.	**Table of Contents** – the set of layers in ArcGIS. Provides access to layer properties and tools.

### ArcGIS Pro-Specific
1. **Project**

### ArcMap-Specific
1.	**ArcMap** – the interface for geographic data analysis, querying, layout, and export.
2.	**ArcCatalog** – the interface for geographic data management.
3.	**ArcToolbox** – a suite of tools, available from both ArcMap and ArcCatalog, for analyzing, transforming, and querying geographic data.
4.	**Map Document** – much like a Word document, a map document stores information about a particular map and its layout. It does not store the geographic data or import it and so a map document file cannot be sent in the same way as other documents
5.	**MXD** (See Map Document) – File extension for map documents. Often used as a synonym for it (eg: “do you have the MXDs?”)
6.	**Data View** – the interface used to view and query data in ArcGIS.
7.	**Layout View** – the interface used to design and lay out a map for export - all nongeographic elements such as title, data sources, scale bar, etc.
    1.	**Data Frame** – the container for layers in layout or data view, but also the viewport for data on the page in layout view.
8.	**Personal Geodatabase** – A type of geodatabase that uses Microsoft Access 2003 format databases as the container, allowing it to be used as a database within Access and for spatial data. A super handy tool to have in your back pocket if you understand relational databases.
9. **Folder Connection**

### FOSS-Specific
1. QGIS
2. GDAL
3. OGR
4. Leaflet

## Remote Sensing
1.  **Orthophoto** – an aerial photo whose pixels are location corrected for the differential distortion created by the lens and elevation of land.
2.  **GeoTIFF** -
3.  **COG - Cloud Optimized GeoTIFF**

## Watershed Analysis
2.	**Watershed** – The entire land area contributing to the water flow at an outlet or stream junction.
3.	**Contributing Watershed** – a watershed based upon an arbitrary point of interest (a dam, etc)
4.	**Blue Lines** – a common cartography term for steams.
5.	**NHD – National Hydrography Dataset** – A dataset that contains water bodies and streamlines for the United States.
    1.	**Flowlines** – the streamlines contained within NHD
6.	**WBD – Watershed Boundary Dataset** – a dataset containing nested watershed boundaries for the United States
    1. **HUCs – Hydrologic Unit Codes** – the watersheds created by the WBD. Usually designated by their size with the digit length (2,4,6,8,10,12) indicating the scale with 12 being the most specific and refined. HUC8s in CA are likely familiar, and HUC12 are useful for refined scale mapping.
7.	**NHDPlus** – an enhanced version of NHD that adds additional attributes for each streamline, such as contributing area, flow, elevation, WBD, etc. Often used in place of NHD.

## Other
1.	**Color Ramp** – the scale of colors used to symbolize a range of values in a map


Licensed Creative Commons Attribution Share-Alike
