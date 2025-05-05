# camera_calibration

ROS 2 package for easy camera calibration with a graphical user interface.

## Usage

Make sure to have a camera connected somewhere in the network that publishes images on a topic, preferably using the `image_transport` package.

Get a checkerboard pattern and place it in front of the camera. Note down

- the size of a single square in meters,
- the size of the checkerboard in squares (e.g. 7x9), excluding the border squares (they will not be detected, especially the lighter ones, making the whole procedure incorrect),
- the base topic name of the camera image (e.g. `/camera/image_raw`).

Then run the following command, modifying :

```bash
ros2 run camera_calibration cameracalibrator --no-service-check --size 7x9 --square 0.02 --ros-args -r image:=/my_camera/image_raw -p camera:=/my_camera
```

The `--no-service-check` option is used to skip the check for the `set_camera_info` service, which is not needed for the calibration procedure.

To calibrate the camera, move the checkerboard in front of the camera, making sure to cover all the angles and positions. Also, try at different distances from the camera; for this to work at low resolutions, a checkerboard with larger squares is recommended.

You can consider the procedure complete when a reasonable number of images have been taken, and the calibration metrics are all maximized or close to the maximum.

Click on `CALIBRATE`, then on `SAVE` to save the calibration data into a `YAML` file. The same data will be written in the console.

---

## Copyright and License

Copyright 2025 dotX Automation s.r.l.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.

You may obtain a copy of the License at <http://www.apache.org/licenses/LICENSE-2.0>.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and limitations under the License.
