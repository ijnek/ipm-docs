IPM Image Node
##############

In this tutorial, we'll look at using the ipm_image_node package, which is a ROS node that applies inverse perspective mapping to an image from a topic.

We'll use ``usb_cam`` to get images from a camera:

.. code-block:: bash

  apt install ros-${ROS_DISTRO}-usb-cam  # Use sudo if necessary
  ros2 run usb_cam usb_cam_node_exe --ros-args -p "camera_name:=NAME_OF_YOUR_CAMERA" -p "camera_info_url:=file://PATH_TO_YOUR_CALIBRATION_YAML_FILE"

Make sure you have your `camera calibrated`_ first, and replace ``PATH_TO_YOUR_CALIBRATION_YAML_FILE`` and ``NAME_OF_YOUR_CAMERA`` appropriately.
``NAME_OF_YOUR_CAMERA`` should match the camera_name parameter in your calibration yaml file.

Then we'll run the IPM image node:

.. code-block:: bash

  ros2 run ipm_image_node ipm --ros-args -r input:=image_raw -p "output_frame:=CAMERA_FRAME"

Replace CAMERA_FRAME with the TF frame of your camera.

Next, we need to publish a transform from the base_link frame to the camera frame:

.. code-block:: bash

  ros2 run tf2_ros static_transform_publisher --frame-id base_link --child-frame-id default_cam

Finally, open RViz to observe the PointCloud2 topic:


.. _camera calibrated: https://navigation.ros.org/tutorials/docs/camera_calibration.html
