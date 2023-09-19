# FOSS Spatial Python Environments on Windows, with Geopandas, Without Conda
You might be reading this because, like me, you've fussed with conda environments, trying to get them to play nice with the complex spatial dependency tree. Recently I found that [Christoph Gohlke](https://www.cgohlke.com/) (bless them) is still publishing binary built wheels of common Python libraries - especially of the spatial software stack 🤌.

Their wheel builds of spatial dependencies are in their Git repository at https://github.com/cgohlke/geospatial-wheels/ with new builds for updates and different Python versions published as releases at https://github.com/cgohlke/geospatial-wheels/releases.

The general recipe to work with this is to build a requirements file - we'll call it `spatial-requirements-310.txt` in this example since it'll install FOSS spatial libraries for Python 3.10 - that references the files in those releases directly, in the following order:

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

The requirements file supports referencing a specific wheel at a location on the web, so, while viewing the releases for your version of Python, your system architecture, and the release/build you have, you can right click on a wheel and copy the link, then paste it
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

I've placed the full requirements [file for download](python/requirements/3.10/spatial-requirements-310.txt) in this repository and if I make files for other versions I'll add them as well. I'll update that file in place whenever new wheels are released.

Note: At some point, I'd love to make a small service that automatically builds the requirements files, but at least for now, here are the instructions to DIY.

## FAQ
I'm putting some questions down here in order to keep the information above short and easy to reference


### What's wrong with using conda?
Nothing - if it works for you. I've personally had numerous problems getting environments to install geopandas, to the point where I stopped using it on Windows, even though it's a great library. I've also seen others with these same issues, so I was happy to see that Christoph Gohlke's wheels provide an alternative route that, in my experience, is faster to work with and more reliable across different Windows computers

### What's a wheel?
A wheel contains a packaged Python library, ready to install on your computer. Importantly, they could contain only source code and be agnostic to the computer/operating system you're running on, or they can optionally contain binary builds and dependencies that allow them to be fully self-contained when a library needs to run non-Python (e.g. C/C++) code that requires compilation for your machine. That's what the wheels here have, and installing these libraries with pip or an alternative means typically requires you have a compiler set up and/or you install external files that support the Python code.

