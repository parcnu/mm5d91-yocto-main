# Main instruction to create mm5d91_driver build for yocto
* used yocto branch scarthgap
* all meta- repos intended to be cloned into same level

# Clone repositories:
## clone mm5d91_driver sources
* mkdir source
* cd source 
```
 # git clone https://github.com/parcnu/mm5d91-rpi4b-driver.git
```
* this is your source path for later source file linking.
# clone rest of the yocto environment
```
 # git clone -b scarthgap git://git.yoctoproject.org/poky
 # git clone -b scarthgap https://git.openembedded.org/meta-openembedded
 # git clone -b scarthgap git://git.yoctoproject.org/meta-raspberrypi 
 # git clone -b scarthgap https://github.com/parcnu/meta-mm5d91-dts.git
 # git clone -b scarthgap https://github.com/parcnu/meta-mm5d91-gui.git
 # git clone -b scarthgap https://github.com/parcnu/meta-mm5d91-module.git
 # git clone -b scarthgap https://github.com/parcnu/mm5d91-yocto-main.git
```
## Link source files accorging to instructions in each README file.
```
 # more meta-mm5d91-dts/README.md
 # more meta-mm5d91-gui/README.md
 # more meta-mm5d91-module/README.md
```

## source environment and create build folder
```
 # source poky/oe-init-build-env build
```
* you are now move to build folder. 
* copy conf files from source/mm5d91-yocto-main/conf to build conf folder
```
 # cd conf
 # cp ../../mm5d91-yocto-main/conf/* .
```
* run bitbake
```
 # bitbake core-image-base
``` 
* takes time to build - several hours based on your computer
* image is created in folder tmp/deploy/images/raspberrypi4-64/
* use balenaetcher to flash memory card
* source file is core-image-base-raspberrypi4-64.rootfs.wic.bz2
# run image and test app
* connect ethernet cable
* connect mm5d91 module as instructed in https://github.com/parcnu/mm5d91-rpi4b-driver/blob/main/README.md
* insert sd card to repi4b
* powerup the rpi4b
* from build computer ssh to rpi
```
 # ssh root@192.168.xxx.xxx (check your ip from router)
 # password = rpi4b
 # usertestapp
 # tail -f output.txt
```
