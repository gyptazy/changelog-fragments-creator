
run:
mkdir build
cd build
cmake ..
cpack -G RPM .
cpack -G DEB .
