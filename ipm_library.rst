IPM Library
###########

The IPM library is a Python library that provides the functionality to perform inverse perspective mapping for a point, or a set of points.

Simply

.. code-block:: python

  from ipm_library.ipm import IPM
  from shape_msgs.msg import Plane
  from vision_msgs.msg import Point2D

  tf_buffer = tf2.Buffer()
  ipm = IPM(tf_buffer, camera_info)

  plane = Plane()  # Plane is in the form of ax + by + cz + d = 0
  plane[0] = 0.0   # a
  plane[1] = 0.0   # b
  plane[2] = 1.0   # c
  plane[3] = 1.0   # d

  point = Point2D()  # Point is a pixel coordinate
  point.x = 100.0
  point.y = 200.0

  time = Time()  # Time of the transforms we want to use

  point_mapped = ipm.map_point(plane, point, time)
  print(point_mapped)

