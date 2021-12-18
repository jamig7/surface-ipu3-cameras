#### Trying to get IPU3 cameras working on Surface devices

Link to issue: https://github.com/linux-surface/linux-surface/issues/91



#### links

Intel maintains IPU4 (not IPU3) drivers (crlmodule, ipu4-acpi, and ipu4) at linux-intel-lts repo (up to v4.19):
- https://github.com/intel/linux-intel-lts/tree/4.19/base

Especially, we may be interested in the crlmodule and ipu4-acpi drivers:
- https://github.com/intel/linux-intel-lts/tree/4.19/base/drivers/media/i2c/crlmodule
- https://github.com/intel/linux-intel-lts/blob/4.19/base/drivers/media/platform/intel/ipu4-acpi.c

The crlmodule looks like the common driver for sensors.
"CRL" stands for "common/configurable register list":
- [intel/linux-intel-lts@dc8fd430](https://github.com/intel/linux-intel-lts/commit/dc8fd43018fa26980c43a449d5b273861267fb73)
- [intel/linux-intel-lts@56c075d6](https://github.com/intel/linux-intel-lts/commit/56c075d6b2978a0841aaaffaf978874be5295ba8)

> Common register list based driver is based on a sensor configuration
> file created for a specific sensor module based on a set of
> rules.

Other places providing IPU4 drivers:
- https://github.com/intel/intel-camera-drivers [out-of-tree driver files, outdated]
- https://github.com/clearlinux-pkgs/linux-iot-lts2018 [as patch files]
- https://github.com/clearlinux-pkgs/linux-iot-lts2018-preempt-rt [same as above]



#### Chromebooks

Some Chromebooks use IPU3 with almost the same sensor drivers as upstream. But the sensor driver works anyway because Chromebooks handle power-managements at rather firmware through runtime_pm:
- https://github.com/coreboot/coreboot/blob/master/src/mainboard/google/poppy/variants/baseboard/include/baseboard/acpi/camera_pmic.asl
- https://github.com/torvalds/linux/blob/e9919e11e219eaa5e8041b7b1a196839143e9125/drivers/media/i2c/ov5670.c#L2515-L2518

links to ACPI asl files for devices with IPU3:
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/google/poppy/variants/baseboard/include/baseboard/acpi
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/google/poppy/variants/atlas/include/variant/acpi
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/google/poppy/variants/nautilus/include/variant/acpi
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/google/poppy/variants/nocturne/include/variant/acpi

links to ACPI asl files for devices with IPU4:
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/google/dedede/variants/baseboard/include/baseboard/acpi
- https://github.com/coreboot/coreboot/tree/master/src/mainboard/intel/jasperlake_rvp/variants/baseboard/include/baseboard/acpi
