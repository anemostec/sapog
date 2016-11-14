PX4 Sapog
=========

[![Join the chat at https://gitter.im/Zubax/general](https://img.shields.io/badge/GITTER-join%20chat-green.svg)](https://gitter.im/Zubax/general)

**Please refer to the documentation page at <https://docs.zubax.com/sapog>.**

## Firmware

### Build instructions

**Prebuilt binaries are available at <https://files.zubax.com/products/io.px4.sapog/>.**

Prerequisites:

* [GCC ARM 4.9 or newer](https://launchpad.net/gcc-arm-embedded)
* Python 3.2+
* Linux or OSX host computer

```bash
git submodule update --init --recursive
cd firmware
make RELEASE=1 # RELEASE is optional; omit to build the debug version
```

Execute `./blackmagic_flash.sh [portname]` from the `tools` directory to flash the firmware with a Black Magic Debug Probe.

### Development

We recommend Eclipse for IDE, but any other IDE will work equally well.
If you prefer Eclipse and need GUI debugging, avoid upgrading to any version newer than Luna,
since in newer releases GUI GDB debugging of embedded targets is broken.
Otherwise we recommend to use the latest Eclipse together with CLI GDB client.
It's inconvenient, but unlike Eclipse it works reliably.

When editing code, please follow the
[PX4 coding conventions](https://github.com/PX4/Firmware/blob/master/CONTRIBUTING.md).

### Hardware timer usage

* TIM1 - 3-phase FET bridge PWM
* TIM2 - ADC synchronization, works in lockstep with TIM1
* TIM3 - RGB LED PWM
* TIM4 - Hard real time callout interface for motor control logic (preempts the kernel)
* TIM5 - RC PWM input capture
* TIM6 - High precision timestamping for motor control logic (sub-microsecond resolution, never overflows)
* TIM7 - General purpose timestamping

## Hardware

Reference hardware design is published under CC BY-SA 3.0 in the [PX4 Hardware repository](https://github.com/PX4/Hardware).

Known commercially available compatible hardware designs are listed below.

- [Zubax Orel 20](https://docs.zubax.com/zubax_orel_20)
