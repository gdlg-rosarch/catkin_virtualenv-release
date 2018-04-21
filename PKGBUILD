# Script generated with Bloom
pkgdesc="ROS - Bundle a virtualenv with a catkin package."


pkgname='ros-lunar-catkin-virtualenv'
pkgver='0.1.4_1'
pkgrel=1
arch=('any')
license=('GPL'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-roslint'
)

depends=('python'
'python2-enum34'
'python2-virtualenv'
)

conflicts=()
replaces=()

_dir=catkin_virtualenv
source=()
md5sums=()

prepare() {
    cp -R $startdir/catkin_virtualenv $srcdir/catkin_virtualenv
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
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

