# Installation Instructions 

## Base Install

* Install [Anaconda](http://continuum.io/downloads) (I'm using Anaconda-2.0.1 [64-Bit - Python 2.7])

* Create a new virtual environment (Skip this step on Windows, trust me, it'll be easier):
```bash
conda create -n scipygis pandas ipython-notebook
source acivate scipygis
conda install pip
```

* If you don't want to use something like Anaconda (or [Enthought Canopy](https://www.enthought.com/products/canopy/)), I still strongly recommend you use [`virtualenv`](https://virtualenv.pypa.io/en/latest/)s and probably even [`virtualenvwrapper`](http://virtualenvwrapper.readthedocs.org/en/latest/).

* If you don't already have it, you might need to install `cython`
```bash
conda install cython
```

* Install required packages (on Windows, use [binaries from here](http://www.lfd.uci.edu/~gohlke/pythonlibs/) for `shapely`, `pyproj`, and `rasterio`)
```bash
conda install matplotlib
conda install shapely
conda install fiona
pip install pyproj
pip install descartes
pip install rasterio
```

* Install `geopandas` (important!)
```bash
pip install git+git://github.com/kjordahl/geopandas.git
```

## (Web)mapping Packages

* Install `cartopy` (on Windows, use [binaries from here](http://www.lfd.uci.edu/~gohlke/pythonlibs/) for `cartopy`)
```bash
pip install pyshp
pip install Cython
pip install git+git://github.com/SciTools/cartopy.git
```

* Alternatively (better?), you can install `cartopy` via `conda` like this:
```bash
conda remove geos shapely cartopy
conda install -c rsignell cartopy
```

* mplleaflet (for making slippy maps)
```bash
pip install git+git://github.com/mpld3/mplexporter.git
pip install git+git://github.com/jwass/mplleaflet.git
```

* geojson.py for shooting data to the web!
```bash
pip install git+git://github.com/jwass/geojsonio.py.git
```

## Optional Packages

* Install `basemap`, a common package for making static maps
```bash
conda install basemap
```

* Install `psycopg2` for interacting with PostGIS
```bash
pip install psycopg2
```

## Install QGIS

* Go to the [official QGIS page](http://qgis.org/en/site/forusers/download.html) for details, or install via `brew` on OSX, `apt-get` on Linux, or `OSGeo4W` on Windows.

## Alternative Install Guide

* Here is the [install guide](https://github.com/kjordahl/SciPy2013#installation-instructions) from a [similar course](https://github.com/kjordahl/SciPy2013) last year.

## Known Issues

* Linux Initial Setup
```bash
sudo add-apt-repository -y ppa:ubuntugis/ppa
sudo apt-get update -qq
sudo apt-get install -y gdal-bin libgdal-dev
```

* OSX Initial Setup
    * First install [`brew`](http://brew.sh/): `ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"`
   * Then update and install `gdal`
```
brew doctor
brew update
brew install gdal
```

* Windows Initial Setup
   * Download and install GDAL [from here](http://www.lfd.uci.edu/~gohlke/pythonlibs/#gdal)
   * If you use this one, then you can also use the `fiona` binary from that site. Otherwise, you'll have to play around with system PATHs etc. Others have had success with [OSGeo4W](http://trac.osgeo.org/osgeo4w/), which includes many important libraries and their Python bindings.

* If you don't already have it, you'll need to install `git`
    * Linux: `sudo apt-get install git`
    * OSX:   `brew install git`
    * Windows: Download and install git [from here](http://www.git-scm.com/downloads). When installing, make sure you choose to "Use Git from the Windows Command Prompt" (You may also want to install optional Unix tools). You can also download GitHub for Windows [here](https://windows.github.com/).

* In *some* cases, it may be better to `pip install shapely` than to `conda install shapely`, particularly when using `cartopy`.

* The `openpyxl` dependency of `pandas` may produce a funny warning: `UserWarning: Installed openpyxl is not supported at this time. Use >=1.6.1 and <2.0.0`

   * To fix this warning, try the following:
```bash
pip install openpyxl
pip uninstall openpyxl
pip install openpyxl==1.8.6 
```

* On vanilla Ubuntu, you might need to install `g++` before installing `rasterio`:
```
sudo apt-get install g++
```

* On OSX (Mavericks), if you don't already have developer tools installed, `pip install pyproj` will 
probably fail (due to missing `gcc`) and then ask you if you want to install them, so click 'yes' and 
then rerun `pip install pyproj`.

* On Windows, `source` is not needed when activating a virtual environment if you are using the Anaconda Command Prompt:  `activate scipygis`.
