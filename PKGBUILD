# Script generated with Bloom
pkgdesc="ROS - RoDI ROS package. Allows to control a RoDI from the Robot Operating System (ROS) without the need to flash a custom firmware and just using the default firmware web services API."


pkgname='ros-kinetic-rodi-robot'
pkgver='0.0.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-geometry-msgs'
'ros-kinetic-roslint'
'ros-kinetic-rospy'
'ros-kinetic-rosunit'
'ros-kinetic-sensor-msgs'
)

depends=('ros-kinetic-geometry-msgs'
'ros-kinetic-roslint'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=rodi_robot
source=()
md5sums=()

prepare() {
    cp -R $startdir/rodi_robot $srcdir/rodi_robot
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

