# Spatial Python Environments on Windows, with Geopandas, Without Conda
You might be reading this because, like me, you've fussed with conda environments, trying to get them to play nice with the complex spatial dependency tree. Recently I found that [Christoph Gohlke](https://www.cgohlke.com/) (bless them) is still publishing binary built wheels of common Python libraries, but especially of the spatial software stack 🤌.

Their wheel builds of spatial dependencies are in the repository at https://github.com/cgohlke/geospatial-wheels/ with new builds for updates and different Python versions published as releases at https://github.com/cgohlke/geospatial-wheels/releases.

The general recipe to work with this is to build a requirements file - we'll call it `spatial-requirements-310.txt` in this example - that references the files in those releases directly, in the following order:

```
Rtree
cftime
netCDF4
pyproj
GDAL
pygeos
rasterio
shapely
fiona
```

The requirements file supports referencing a specific wheel at a location on the web, so you can right click on the wheel for your version of Python, your system architecture, and the release/build you want and copy the link, then paste it
into your requirements file in the format `package_name @ url`. So, for example, the most recent release of Rtree would look like the following in my requirements file:
`Rtree @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/Rtree-1.0.1-cp310-cp310-win_amd64.whl`

The rest of my requirements file for Python 3.10 would look like:
```
Rtree @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/Rtree-1.0.1-cp310-cp310-win_amd64.whl
cftime @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/cftime-1.6.2-cp310-cp310-win_amd64.whl
netCDF4 @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/netCDF4-1.6.4-cp310-cp310-win_amd64.whl
pyproj @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/pyproj-3.6.0-cp310-cp310-win_amd64.whl
GDAL @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/GDAL-3.7.1-cp310-cp310-win_amd64.whl
pygeos @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/pygeos-0.14.0-cp310-cp310-win_amd64.whl
rasterio @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/rasterio-1.3.8-cp310-cp310-win_amd64.whl
shapely @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/shapely-2.0.1-cp310-cp310-win_amd64.whl
fiona @ https://github.com/cgohlke/geospatial-wheels/releases/download/v2023.7.16/Fiona-1.9.4.post1-cp310-cp310-win_amd64.whl
geopandas
```

where it installs everything directly from cgohlke's GitHub releases, then retrieves geopandas directly from PyPI. Importantly, we've already resolved most of the geopandas dependencies here, so installation should be very simple
after installing these wheels (and their dependencies). Optionally, if you need to control versions of matplotlib, numpy, scipy, Pandas, etc, insert those before these installations in the file to try to force dependency resolution to use them.

Then I can just run `python -m pip install -r spatial-requirements-310.txt` in my Python environment (whether virtualenv, pipenv, etc) in order to obtain the full stack of dependencies.

Note: At some point, I'd love to make a small service that automatically builds the requirements files, but at least for now, here are the instructions to DIY.

