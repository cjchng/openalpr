# openalpr
資源版本:

ubuntu18.04 ; opencv3.3.0；log4cplus2.0；tesseract 4.00.00；leptonica-1.74.4；openalpr2.3。

編譯opencv
---
 1.Updating Ubuntu

  ```
  sudo apt-get updatesudo
  apt-get upgrade
  ```
 2.Install dependencies
  ```
  sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
  sudo apt-get install python3.6-dev python3-numpy libtbb2 libtbb-dev
  sudo apt-get install libjpeg-dev libpng-dev libtiff5-dev libjasper-dev libdc1394-22-dev libeigen3-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev sphinx-common libtbb-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev libavutil-dev libavfilter-dev libavresample-dev  
  ```
 3.Build and install OpenCV
  ```
  cd opencv
  sudo mkdir release
  cd release
  cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
  sudo make -j4
  sudo make install
  sudo ldconfig
  ```
 4.Check OpenCV version
  ```
  pkg-config --modversion opencv
  ```

編譯log4cplus
---
```
cd /opt/log4cplus
./configure CXXFLAGS="-std=c++0x"
sudo make
sudo make install
```

安裝依賴庫
---
```
sudo apt-get install g++ # or clang++
sudo apt-get install autoconf automake libtool
sudo apt-get install autoconf-archive
sudo apt-get install pkg-config
sudo apt-get install libpng-dev
sudo apt-get install libjpeg8-dev
sudo apt-get install libtiff5-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libicu-dev
sudo apt-get install libpango1.0-dev
sudo apt-get install libcairo2-dev
```  
編譯leptonica
---
```
cd /opt/leptonica
./configure --prefix=/usr/local
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