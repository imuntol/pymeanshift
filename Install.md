# Prerequisites #

## Binary packages ##

Python 2.7 and Numpy are required for the **binary packages** provided in the [Downloads](http://code.google.com/p/pymeanshift/downloads) section.
  * On recent Debian-based (e.g. Ubuntu) Linux distributions, Python is already installed; Numpy is provided by the package _python-numpy_.
  * On recent Redhat-based Linux distributions (e.g. Fedora), Python is already installed; Numpy is provided by the package _numpy_.
  * On MacOS X, Python is already installed, but is usually one or two years old.  It is thus better to install the official Python release available at http://www.python.org/download/releases/2.7.3 ; Numpy is available for MacOS X at http://sourceforge.net/projects/numpy/files/NumPy .
  * On Windows, Python (32 or 64 bits) can be installed using the official release available at http://www.python.org/download/releases/2.7.3 ; Numpy (32 bits) is available for Windows  at http://sourceforge.net/projects/numpy/files/NumPy .
    * **Python 64 bits only**: A 64 bits version of Numpy is also required; An unofficial release is available at http://www.lfd.uci.edu/~gohlke/pythonlibs/ (the installer contains both the binaries and the headers).

## Source code ##

To install PyMeanShift from the **source code** (source package or Mercurial repository), Python 2.7 (or 3.2) and Numpy development headers are required:
  * On recent Debian-based (ex. Ubuntu) Linux distributions, the Python  headers are provided by the package _python-dev_ (2.7) or _python3-dev_ (3.2); The Numpy headers are provided by the package _python-numpy-dev_ (2.7) or _python3-numpy-dev_ (3.2).
  * On recent Redhat-based Linux distributions (ex. Fedora), the Python headers are provided by the package _python-devel_ (2.7) or _python3-devel_ (3.2); The Numpy headers are provided by the package _numpy_ (2.7) or _python3-numpy_ (3.2).
  * On MacOS X, the Python headers are installed during the Python installation process (with the official Python release, not the MacOS X version of Python); The Numpy headers are installed during the Numpy installation process.
  * On Windows, the Python headers are installed during the Python installation process. The Numpy headers are installed during the Numpy installation process.
    * **Also needed**: Visual C++ 2008 Express Edition with SP1 (http://www.microsoft.com/visualstudio/en-us/products/2008-editions/express).
    * **Also needed for Python 64 bits**: Windows 7 Platform SDK is needed (with some hacks) to compile a 64 bits extension for Python 64 bits (see http://mattptr.net/2010/07/28/building-python-extensions-in-a-modern-windows-environment/ ); A 64 bits version of Numpy is also required; An unofficial release is available at http://www.lfd.uci.edu/~gohlke/pythonlibs/ (the installer contains both the binaries and the headers).


---


# Install #

## Binary packages ##

  * **Linux**: No binary package available for now (coming soon).
  * **MacOS X**: No binary package available. If someone would like to provide binary packages for MacOS X, let me know by posting a new issue on the [Issues](http://code.google.com/p/pymeanshift/issues) page.
  * **Windows**: Installers are available in the [Downloads](http://code.google.com/p/pymeanshift/downloads) section. Choose the one that **matches your Python version**: 32 bits (win32) or 64 bits (win-amd64). If you have Python 32 bits installed on a Windows 64 bits OS, you need the 32 bits (win32) version of the extension.

## Source code ##

  1. The Python extension is compiled as follows:
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
  1. The wrapper module and the extension can be installed as follows:
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
./setup.py install --user
```
      * **Windows** (at the command prompt):
```
python setup.py install --user
```
  1. If everything went fine, it should be possible to import the _pymeanshift_ module in Python code. The module provides a function named _segment_ and a class named _Segmenter_.

> Code example with OpenCV:
```
import cv2
import pymeanshift as pms

original_image = cv2.imread("example.png")

(segmented_image, labels_image, number_regions) = pms.segment(original_image, spatial_radius=6, 
                                                              range_radius=4.5, min_density=50)
```

> Code example with PIL:
```
from PIL import Image
import pymeanshift as pms

original_image = Image.open("example.png")

(segmented_image, labels_image, number_regions) = pms.segment(original_image, spatial_radius=6, 
                                                              range_radius=4.5, min_density=50)
```

> Code example using the Segmenter class:
```
import pymeanshift as pms

# [...]
# load image in "original_image"
# [...]

my_segmenter = pms.Segmenter()

my_segmenter.spatial_radius = 6
my_segmenter.range_radius = 4.5
my_segmenter.min_density = 50

(segmented_image, labels_image, number_regions) = my_segmenter(original_image)
```