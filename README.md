# oz2DeviceTree <==> device tree for hikingGPS project

This Device Tree sets up Beaglebone Black Rev C for 
running PeterMacleodThompson/hikingGPS repository using
 - UART1 for gps
 - i2c1 for fxos8700 accelerometer/magnetometer 

oz2DeviceTree pristine (initial commit) is an exact copy of source files
from Linux 4.16.13 compiled with 
 - make omap2plus_defconfig
 - make dtbs

The out-of-tree compile is based on 
 - arm-linux-gnueabihf-cpp  --version Ubuntu/Linaro 4.8.4
 - dtc  --version: DTC 1.4.5-gc1e55a55

The steps for an out-of-tree compile using this repository are as follows:

```
export CPATH=.
arm-linux-gnueabihf-cpp  -nostdinc -I include -undef -x assembler-with-cpp   am335x-boneblack.dts   >  tempdeleteme.dts 
~/bbb2018/linux-stable/scripts/dtc/dtc -I dts -O dtb -b 0 -o am335x-boneblack.dtb tempdeleteme.dts 
rm tempdeleteme.dts
cp am335x-boneblack.dtb /media/peter/boot/  /*sdcard*/ 
```

Beaglebone Black PIN CONNECTION  
  UART1 rx = pin P9_26  
  UART1 tx = pin P9_24  
  i2c1 scl = pin P9_17  
  i2c1 sda = pin P9_18  
        OR (i2c2 also works)  
  i2c1 scl = pin P9_19  
  i2c1 sda = pin P9_20  


