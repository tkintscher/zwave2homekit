# ZWave2HomeKit
Expose Z-Wave accessories to HomeKit.


## Features

 * Expose Z-Wave thermostats to HomeKit.
 * Change the setpoint via HomeKit


This program was tested using Docker on Synology,
an Aeotec Gen5 Z-Wave stick,
and Danfoss LC-13 014G0013 thermostats.


## Requirements

The Z-Wave devices are accessed using [python-openzwave](https://github.com/OpenZWave/python-openzwave).

HomeKit supported is provided through [HAP-python](https://github.com/ikalchev/HAP-python).

See the [Dockerfile](Dockerfile) for all required packages.


## Environment Variables

 * `ZWAVE_DEVICE`: Device name of the Z-Wave device (default: `/dev/ttyACM0`).
 * `BRIDGE_NAME`:  Display name of the bridge in HomeKit (default: `Z-Wave Bridge`).
 * `MAC`:          Any unique MAC address not used elsewhere (default: `AA:11:22:33:44:55`).
 * `PINCODE`:      PIN for adding the accessory in HomeKit (default: `123-45-678`).


## Running on Synology

The Docker image can be installed on Synology.
When adding the container, ensure that

 * "Execute container using high privilege" is activated
   (necessary for accessing the Z-Wave device; Synology's interface does not allow passthrough of individual USB devices),
 * some directory on the NAS is bound to `/config`,
 * and environment variables are set as desired (see above).
