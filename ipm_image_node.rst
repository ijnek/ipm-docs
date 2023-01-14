IPM Image Node
##############

In this tutorial, we'll look at using the ipm_image_node package, which is a ROS node that applies inverse perspective mapping to an image from a topic.

We'll use ``usb_cam`` to get images from a camera:

.. code-block:: bash

  apt install ros-${ROS_DISTRO}-usb-cam  # Use sudo if necessary
  ros2 run usb_cam usb_cam_node_exe

Make sure you have your `camera calibrated`_ first.

Then we'll run the IPM image node:

.. code-block:: bash

  ros2 run ipm_image_node ipm --ros-args -r input:=image_raw -p "output_frame:=default_cam"

.. _camera calibrated: https://navigation.ros.org/tutorials/docs/camera_calibration.html
