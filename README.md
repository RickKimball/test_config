# test_config
Automated testing setup for Arduino_STM32 using linux

### Pre-requiste setup

  * Install arduino 1.8.8
  * Install Arduino SAM board from Tools/Board Manager
  * Use an empty Sketch directory. I use ~/Documents/Arduino
  * Clone this repo I put it in $HOME/test_config
  * Install python3

```
$ cd ~/arduino-1.8.8/hardware
$ git clone https://github.com/RickKimball/Arduino_STM32.git
$ git checkout final_release *
```
**Note: final_release branch isn't setup yet

### Make sure Arduino_STM32 works
 * Start Arduino
 * Under tools, select STM32F103C8 from the STM32F1 boards (stm32duino.com)
 * Compile a bare minimum sketch

### Check out this repo and modify

```
$ cd ~/
$ git clone https://github.com/RickKimball/test_config
$ cd test_config
```
Edit the file 'path_config.json' modify to suit your home directories.

### Launch simple test run using the arduino-builder.py script

```
$ python3 arduino-builder.py --arch STM32F1 -b 'STM32F103C8'
Arduino IDE version used: 10808
Cores configuration JSON file that will be used: conf/cores_config.json
Build configuration for 'Arduino_STM32' maintainer and 'STM32F1' architecture

Building : /home/kimballr/arduino-1.8.8/examples/01.Basics/BareMinimum/BareMinimum.ino (1/1) 
Build STM32F103C8 (1/1)... 
  --> STM32F103C8 SUCESS

****************** PROCESSING COMPLETED ******************
TOTAL PASSED = 1/1 (100.0%) 
TOTAL FAILED = 0/1 (0.0%) 
TOTAL SKIPPED = 0/1 (0.0%) 
Logs are available here: /home/kimballr/Documents/arduinoBuilderOutput/build_2019-01-07_18-19-48
Build duration: 0:00:06.167815
```

### Launch filelist test run
```
$ python3 arduino-builder.py --arch STM32F1 -b 'STM32F103C8' -f conf/sketch_list.txt
Arduino IDE version used: 10808
Cores configuration JSON file that will be used: conf/cores_config.json
Build configuration for 'Arduino_STM32' maintainer and 'STM32F1' architecture

Building : /home/kimballr/arduino-1.8.8/examples/01.Basics/BareMinimum/BareMinimum.ino (1/1) 
Build STM32F103C8 (1/1)... 

... a while later 

Building : /home/kimballr/arduino-1.8.8/libraries/Stepper/examples/stepper_speedControl/stepper_speedControl.ino (53/53) 
Build STM32F103C8 (1/1)... 
  --> STM32F103C8 SUCESS

****************** PROCESSING COMPLETED ******************
TOTAL PASSED = 48/53 (90.57%) 
TOTAL FAILED = 5/53 (9.43%) 
TOTAL SKIPPED = 0/53 (0.0%) 
Logs are available here: /home/kimballr/Documents/arduinoBuilderOutput/build_2019-01-07_18-20-58
Build duration: 0:03:38.689700
```






