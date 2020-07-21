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
  sudo cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
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
./autogen.sh
./configure
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