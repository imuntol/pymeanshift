# Prerequisites #

Python 2.7 and OpenCV library version 2.3 or greater, along with its Python binding, are required for the **binary packages** provided in the [Downloads](http://code.google.com/p/pymeanshift/downloads/list) section. See http://opencv.willowgarage.com.

To install PyMeanShift from the **source code** (source package or Mercurial repository), the following is also required:
  * OpenCV headers version 2.3 or greater. If OpenCV was compiled and installed from its source code, then the headers are already installed.  Otherwise, see http://opencv.willowgarage.com ;
  * Python development headers.
    * On Debian-based (ex. Ubuntu) Linux distributions, this is provided by the package _python-dev_;
    * On Redhat-based Linux distributions (ex. Fedora), this is provided by the package _python-devel_;
    * On MacOS X, (instructions to come);
    * On Windows, the Python headers can be installed during the Python installation process.
  * (**Windows only**): Visual C++ 2008 Express Edition with SP1 (http://www.microsoft.com/visualstudio/en-us/products/2008-editions/express).
  * (**Optional**) To regenerate the Python wrappers, Swig is required.
    * On most Linux distributions, Swig is provided by a package named _swig_;
    * For MaxOS X and Windows, see http://www.swig.org/download.html


---


# Install #

## Binary packages ##

  * **Linux**: (No binary package provided for now)
  * **MacOS X**: (No binary package provided for now)
  * **Windows**: Installer is available in the download section.

## Source code ##

  1. First, the OpenCV installation directory must be specified according to the operating system:
    * **Linux** and **MacOS X**:
> > > If OpenCV is not installed in /usr or /usr/local, the file _setup.cfg_ must be edited to specify the include directory and the library directory as follows:
```
[build_ext]
include_dirs = /usr/local/include/opencv
library_dirs = /usr/local/lib
```
> > > Both directory must be changed according to the actual location of OpenCV on the system.
    * **Windows**:
> > > The OpenCV installation directory must be specified in the OPENCV\_DIR environment variable (e.g. D:\librairies\opencv-2.3).  Ensure that the OpenCV ".LIB" files are under the "lib" directory in the OpenCV installation directory.
  1. Next, the Python extension is compiled as follows:
    * **Linux** and **MacOS X** (in a terminal window):
```
cd path-to-pymeanshift-sources
./setup.py build
```
    * **Windows** (at the command prompt):
```
cd path-to-pymeanshift-sources
python setup.py build
```
  1. Finally, the extension can be installed as follows:
    * Systemwide, for all users (admin privileges are needed):
      * **Linux** and **MacOS X** (in a terminal window):
```
sudo ./setup.py install
```
      * **Windows** (at the command prompt, from an admin account):
```
python setup.py install
```
    * For one user only:
      * **Linux** and **MacOS X** (in a terminal window):
```
sudo ./setup.py install --user
```
      * **Windows** (at the command prompt):
```
python setup.py install --user
```
  1. If everything went fine, it should be possible to import the PyMeanShift module in Python code. The module consists in one function named _segmentMeanShift_.
```
import cv
import pymeanshift as pms

origImage = cv.LoadImageM("example.png")

(segmentedImage, labelsImage, numberRegions) = pms.segmentMeanShift(origImage)
```