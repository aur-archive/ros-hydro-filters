# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This library provides a standardized interface for processing data as a sequence of filters."
url='http://ros.org/wiki/filters'

pkgname='ros-hydro-filters'
pkgver='1.7.4'
_pkgver_patch=2
arch=('any')
pkgrel=3
license=('BSD')

ros_makedepends=(ros-hydro-rosconsole
  ros-hydro-roscpp
  ros-hydro-roslib
  ros-hydro-catkin
  ros-hydro-pluginlib
  ros-hydro-rostest)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-roscpp
  ros-hydro-roslib
  ros-hydro-rosconsole
  ros-hydro-pluginlib)
depends=(${ros_depends[@]})

_tag=release/hydro/filters/${pkgver}-${_pkgver_patch}
_dir=filters
source=("${_dir}"::"git+https://github.com/ros-gbp/filters-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
