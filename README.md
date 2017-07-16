# python-opencv-bulds
This repository contains opencv builds for Python2 and Python3 for Ubuntu.
OpenCV version = 3.2.0

How to use :
1.For Python2,copy cv2.so file to your python's library location ,either to dist-packages or site-pacckages .Examaple : /usr/local/lib/python2.7/dist-packages/ 

Yo can do the same even when you are using virtualenv,you just need to copy cv2.so to your currently activated environment python's library location.For example my activated virtualenv is cv then ,you need to change you working directory  and then copy cv2.so file to this directory :
cd  ~/.virtualenvs/cv/lib/python2.7/site-packages/

Note : cv2.so has been built by me with these options

$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_EXTRA_MODULES_PATH= ../opencv_contrib-3.2.0/modules \
    -D PYTHON_EXECUTABLE=~/usr/bin/python \
    -D BUILD_EXAMPLES=ON ..
    



