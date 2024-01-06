Install CMake through the Ubuntu Command Line
If you prefer the command line over the UI, here is the method you will need to follow in order to install the latest version of CMake. I also tried installing CMake through default Ubuntu repositories and also through PPA but none of them gave me the latest version. The only workable method involves downloading the source code from the Official CMake website “https://cmake.org/download/”, compiling it and then installing CMake through it.

Open the Ubuntu command line, the Terminal either through the Ctrl+Alt+T shortcut or through the Application launcher search.

Then, enter the following command to download the source code:

$ wget https://github.com/Kitware/CMake/releases/download/v3.15.2/cmake-3.15.2.tar.gz
Once the tar.gz file is downloaded, enter the following command to extract it:

$ tar -zxvf cmake-3.15.2.tar.gz
Then move to the extracted folder as follows:

$ cd cmake-3.15.2
Finally, run the following commands to compile and install CMake:

./bootstrap

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_272ad510558a93bc5d06faa1cc054ca1)

When CMake has bootstrapped, you can now make it using the following command:

$ make
And then install it as follows:

$ sudo make install


After the software is successfully installed, you can verify its installation and also if the correct version is installed, through the following command:

$ cmake --version

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6edb6ee084ffc14cf754a39906a9e6e1)

cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules -D OPENCV_ENABLE_NONFREE=ON -D ENABLE_NEON=ON -D ENABLE_VFPV3=ON -D WITH_TBB=ON -D BUILD_TESTS=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D BUILD_EXAMPLES=OFF  ..

