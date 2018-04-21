# Script generated with Bloom
pkgdesc="ROS - Package to test catkin_virtualenv."


pkgname='ros-kinetic-test-catkin-virtualenv'
pkgver='0.1.4_0'
pkgrel=1
arch=('any')
license=('GPL'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-catkin-virtualenv'
'ros-kinetic-rostest'
)

depends=()

conflicts=()
replaces=()

_dir=test_catkin_virtualenv
source=()
md5sums=()

prepare() {
    cp -R $startdir/test_catkin_virtualenv $srcdir/test_catkin_virtualenv
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

