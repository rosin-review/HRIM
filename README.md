[![Build Status](https://travis-ci.org/erlerobot/HRIM.svg?branch=master)](https://travis-ci.org/erlerobot/HRIM)

# Hardware Robot Information Model (HRIM)

![](https://docs.h-ros.com/user/pages/04.HRIM/StandardLogicalInterface.jpg)

The Hardware Robot Information Model or **HRIM** for short, is a common interface that facilitates interoperability among different vendors of robot hardware components with the purpose of building modular robots. HRIM focuses on the standardization of the logical interfaces between robot modules, designing a set of rules that each device has to meet in order to achieve interoperability.

- [Documentation](https://docs.h-ros.com/hrim)
- [Web page](http://therobotmodel.com)
- [Discussion and issues](https://github.com/erlerobot/HRIM/issues)
- [Contributions (through pull requests)](https://github.com/erlerobot/HRIM/pulls)

Real world implementations requires taking into account the common hardware modules used in robotics. The robot modules have been classified in 7 **types** of devices: sensor, actuator, cognition, communication, power, ui and composite. Each type is composed by **sub-types or devices** related to the functionality of the module. *For example, a camera is a sub-type of the sensor type* and represented with the following structure:

```
sensor/
...
├── camera
│   ├── hrim_sensor_camera_msgs
│   │   ├── CMakeLists.txt
│   │   ├── msg
│   │   │   ├── CameraInfo.msg
│   │   │   ├── CompressedImage.msg
│   │   │   ├── Image.msg
│   │   │   ├── PTZ.msg
│   │   │   └── SpecsCamera.msg
│   │   └── package.xml
│   └── hrim_sensor_camera_srvs
│       ├── CMakeLists.txt
│       ├── package.xml
│       └── srv
│           └── SetCameraInfo.srv
...
```

###


A preliminary whitepaper about this work is available at https://arxiv.org/abs/1802.01459. Please use the following BibTex entry to cite our work:

```
@article{hrim,
  title={An information model for modular robots: the Hardware Robot Information Model (HRIM)},
  author={Zamalloa, Irati and Muguruza, Iñigo and Hernández, Alejandro and Kojcev, Risto and Mayoral, Víctor},
  journal={arXiv preprint arXiv:1802.01459},
  year={2018}
}
```

#### Script usage

To parse and print the contents of a component the command structure would be the following:
```
python hrim.py {path-to-component.xml} [1]
```
Where `{path-to-component.xml}` is mandatory and signifies the absolute path to one of the following files:
* models/actuator/servo/servo.xml
* models/actuator/servo/servo_clean.xml
* models/sensor/rangefinder/rangefinder.xml
* models/sensor/rangefinder/rangefinder_clean.xml
* models/sensor/torque/torque.xml
* models/sensor/torque/torque_clean.xml

And `[1]` is optional and signifies the script should show the definition of topics/properties not defined inside the parsed component itself, for example the generic topics (id, power...) or the header. Disabled by default.
