The mean shift algorithm and its C++ implementation are by Chris M. Christoudias and Bogdan Georgescu. The PyMeanShift extension provides the "glue" that is necessary in order to use this C++ implementation with Numpy arrays in Python. In PyMeanShift source code, the Christoudias and Georgescu implementation of the mean shift algorithm consists in the following files:
  * [ms.h](http://code.google.com/p/pymeanshift/source/browse/ms.h)
  * [ms.cpp](http://code.google.com/p/pymeanshift/source/browse/ms.cpp)
  * [msImageProcessor.cpp](http://code.google.com/p/pymeanshift/source/browse/msImageProcessor.cpp)
  * [msImageProcessor.h](http://code.google.com/p/pymeanshift/source/browse/msImageProcessor.h)
  * [RAList.cpp](http://code.google.com/p/pymeanshift/source/browse/RAList.cpp)
  * [RAList.h](http://code.google.com/p/pymeanshift/source/browse/RAList.h)
  * [rlist.cpp](http://code.google.com/p/pymeanshift/source/browse/rlist.cpp)
  * [rlist.h](http://code.google.com/p/pymeanshift/source/browse/rlist.h)
  * [tdef.h](http://code.google.com/p/pymeanshift/source/browse/tdef.h)
  * [MSReadme.txt](http://code.google.com/p/pymeanshift/source/browse/MSReadme.txt)
See the file [MSReadme.txt](http://code.google.com/p/pymeanshift/source/browse/MSReadme.txt) in the PyMeanShift sources for more information. These files were obtained from the Blepo computer vision library (http://www.ces.clemson.edu/~stb/blepo/).

For details on the mean shift algorithm, see the following paper:
> D. Comanicu, P. Meer: "[Mean shift: A robust approach toward feature space analysis](http://dx.doi.org/10.1109/34.1000236)". IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 24, no. 5, May 2002.