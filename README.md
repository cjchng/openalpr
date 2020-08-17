# openalpr
資源版本:

ubuntu18.04 ; 
[opencv3.3.0](https://github.com/opencv/opencv/archive/3.3.0.zip)；
[opencv_contrib 3.3.0](https://github.com/opencv/opencv_contrib/releases?after=3.4.3);
[log4cplus2.0](https://sourceforge.net/projects/log4cplus/files/log4cplus-stable/2.0.0/log4cplus-2.0.0.zip/download)；
[tesseract 4.00.00](https://github.com/tesseract-ocr/tesseract/releases)；
[leptonica-1.74.4](https://github.com/DanBloomberg/leptonica/releases)；
[openalpr2.3](https://github.com/openalpr/openalpr/releases)。

Updating Ubuntu 
---
```
  sudo apt-get update 
  sudo apt-get upgrade
``` 

安裝依賴庫
---
  ```
  sudo apt-get install build-essential
  sudo apt-get install cmake
  sudo apt-get install git
  sudo apt-get install g++ # or clang++
  sudo apt-get install autoconf automake libtool
  sudo apt-get install autoconf-archive
  sudo apt-get install pkg-config
  sudo apt-get install python-dev python3-dev
  sudo apt-get install libpng-dev
  sudo apt-get install libjpeg8-dev
  sudo apt-get install libtiff5-dev
  sudo apt-get install zlib1g-dev
  sudo apt-get install libicu-dev
  sudo apt-get install libgtk2.0-dev
  sudo apt-get install libpango1.0-dev
  sudo apt-get install libcairo2-dev
  sudo apt-get install libavformat-dev
  sudo apt-get install libavcodec-dev
  sudo apt-get install libswscale-dev
  sudo apt-get install libjpeg-dev
  sudo apt-get install libdc1394-22-dev
  sudo apt-get install libeigen3-dev
  sudo apt-get install libtheora-dev
  sudo apt-get install libvorbis-dev
  sudo apt-get install libxvidcore-dev
  sudo apt-get install libx264-dev
  sudo apt-get install sphinx-common
  sudo apt-get install libtbb-dev
  sudo apt-get install yasm
  sudo apt-get install libfaac-dev
  sudo apt-get install libopencore-amrnb-dev
  sudo apt-get install libgstreamer-plugins-base1.0-dev
  sudo apt-get install libavutil-dev
  sudo apt-get install libavfilter-dev
  sudo apt-get install libavresample-dev
  ```
  - install libjasper
  ```
  sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
  sudo apt-get update
  sudo apt install libjasper1 libjasper-dev
  ```
  - python 
  ```
  sudo apt-get install python3.6-dev
  sudo apt-get install python3-numpy
  sudo apt-get install libtbb2
  sudo apt-get install libtbb-dev
  ```

編譯opencv
---
  ```
  cd /opt/opencv
  sudo mkdir release
  cd release
  sudo cmake -D CMAKE_BUILD_TYPE=RELEASE \ -D INSTALL_C_EXAMPLES=OFF \ INSTALL_PYTHON_EXAMPLES=ON \ -D BUILD_EXAMPLES=OFF \ -DENABLE_CXX11=ON \ -D BUILD_opencv_python3=ON \ -D BUILD_opencv_python2=ON \ -D BUILD_opencv_java=OFF \ -D PYTHON3_EXECUTABLE=$(which python3)\ -D PYTHON3_INCLUDE_DIR=/usr/include/python3.5m \ -D PYTHON3_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.5m.so.1 \ -D PYTHON3_NUMPY_PATH=/usr/local/lib/python3.5/dist-packages \ -D PYTHON2_EXECUTABLE=$(which python2)\ -D PYTHON2_INCLUDE_DIR=/usr/include/python2.7 \ -D PYTHON2_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython2.7.so.1 \ -D PYTHON2_NUMPY_PATH=/usr/local/lib/python2.7/dist-packages -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules ..
  sudo make -j4
  sudo make install
  sudo ldconfig
  ```
編譯log4cplus
---
```
cd /opt/log4cplus
sudo sudo apt update./configure CXXFLAGS="-std=c++0x"
sudo make
sudo make install
```

編譯leptonica
---
```
cd /opt/leptonica
sudo ./configure --prefix=/usr/local
sudo make
sudo make install
```
編譯tesseract
---
```
cd /opt/tesseract
sudo gedit ./ccutil/unichar.h &
     using std::string;
sudo ./autogen.sh
sudo ./configure
sudo make
sudo make install 
sudo ldconfig
```
編譯openalpr
---
```
cd /opt/openalpr/src
sudo gedit CMakeLists.txt &
     set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --std=c++11")
     SET(OpenCV_DIR "/usr/local/lib")
     SET(Tesseract_DIR "/usr/local/src/tesseract-ocr")
sudo cmake ./
sudo gedit ./CMakeFiles/alprd.dir/build.make &
     alprd: /usr/local/lib/liblog4cplus.so
sudo make 
sudo make install
```

Check OpenCV version
---
  ```
  pkg-config --modversion opencv
  ```
Check alpr version
---
  ```
  alpr --version
  ```
Check alpr version
---
  ```
  tesseract --version
  ```
openalpr_tagger
---
```

```