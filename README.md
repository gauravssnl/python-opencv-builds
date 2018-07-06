# python-opencv-builds
This repository contains opencv builds for Python2 and Python3 for Ubuntu/Linux

OpenCV version = 3.4.1

Use thse commands  

```code

sudo apt-get update
sudo apt-get upgrade
Remove any previous installations of x264</h3>
sudo apt-get remove x264 libx264-dev
 
We will Install dependencies now
 
sudo apt-get install build-essential checkinstall cmake pkg-config yasm
sudo apt-get install git gfortran
sudo apt-get install libjpeg8-dev jasper-dev libpng-dev
 
# If you are using Ubuntu 14.04
sudo apt-get install libtiff4-dev
# If you are using Ubuntu 16.04
sudo apt-get install libtiff5-dev
 
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
sudo apt-get install libxine2-dev libv4l-dev
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
sudo apt-get install qt5-default libgtk2.0-dev libtbb-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libfaac-dev libmp3lame-dev libtheora-dev
sudo apt-get install libvorbis-dev libxvidcore-dev
sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get install x264 v4l-utils
 
# Optional dependencies
sudo apt-get install libprotobuf-dev protobuf-compiler
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen

sudo apt-get install python-dev python-pip python3-dev python3-pip
sudo -H pip2 install -U pip numpy
sudo -H pip3 install -U pip numpy

pip install numpy scipy matplotlib scikit-image scikit-learn ipython

git clone https://github.com/opencv/opencv.git
cd opencv 
git checkout 3.4.1 
cd ..

git clone https://github.com/opencv/opencv_contrib.git
cd opencv_contrib
git checkout 3.4.1
cd ..

```

### set your python executable for which  you want to install cv2 by setting  PYTHON_EXECUTABLE option & set D INSTALL_C_EXAMPLES=ON to install C examples 

```code

cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_C_EXAMPLES=OFF \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D WITH_QT=ON \
      -D WITH_OPENGL=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
       -D PYTHON_EXECUTABLE=/usr/bin/python3 \
      -D BUILD_EXAMPLES=ON ..
      

# find out number of CPU cores in your machine
nproc

# substitute 4 by output of nproc
make -j4

sudo make install
sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig

# Find cv2.so files 
find /usr/local/lib/ -type f -name "cv2*.so"

```

# Python2 

1.Change your directory to python/virtualenv site-packages folder :
```code
cd /home/gauravssnl/.pyenv/versions/py2/lib/python2.7/site-packages
```
2. create symbolic link for cv2.so
```code
ln -s /usr/local/lib/python2.7/dist-packages/cv2.so cv2.so
```


Note : cv2.so has been built by me with these options

$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_C_EXAMPLES=OFF \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D WITH_QT=ON \
      -D WITH_OPENGL=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
       -D PYTHON_EXECUTABLE=/usr/bin/python2 \
      -D BUILD_EXAMPLES=ON ..
    
    
    
    
# Python3

1.Change your directory to python/virtualenv site-packages folder :
```code
cd /home/gauravssnl/.pyenv/versions/py3/lib/python3.7/site-packages
```

2. create symbolic link for cv2.so
```code
ln -s /usr/local/lib/python3.6/dist-packages/cv2.cpython-36m-x86_64-linux-gnu.so cv2.so
```


Note : cv2.cpython-35m-x86_64-linux-gnu.so has been built by me with these options

$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_C_EXAMPLES=OFF \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D WITH_QT=ON \
      -D WITH_OPENGL=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
       -D PYTHON_EXECUTABLE=/usr/bin/python3 \
      -D BUILD_EXAMPLES=ON ..



