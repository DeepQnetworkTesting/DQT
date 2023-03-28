# DQT(pre-released)

## Overview
A pre-released version of DQT and the corresponding experimental data.

Download data via: https://drive.google.com/drive/folders/1O9y88lXGLLmEMC0PHYWHJa0_scid7N59?usp=sharing

- logs.zip: Our experimental data, including testing data of 5 tools on 30 open-source apps at 5 rounds.
	- File name end with "log": The runtime cmd output of the tool.
	- File name end with "bug": The runtime filtered logcat output.
- DQT_executable.zip: A pre-released executable version of DQT.


## Experimental Environment
- System: Ubuntu 18.04
- Python: 3.7.12
- GPU Driver: 470.161.03
- CUDA: 11.4
- Torch: 1.10.0+cu113


## Run DQT
1. unzip DQT_executable.zip
2. enter a python venv (enter the python 3.7.12 venv we have provided or use your own)
3. enter the main dir
4. edit config.yaml
5. run in cmd with ./main


## config.yaml
- ALLOW_CLEAN: Allow the tool to clean app data during testing.
	- Some apps need login in advance for normal operation. If an app is early logged in , please set this to "false".
	- Special cases such as database conflicts or plug-in missing may require this field to be "false".
	- Otherwise, this field is usually set to "true".
	- Among our 30 experimental apps, these 5 apps need a "false": Signal (login), Tachiyomi (prevent plug-in loss), K9Mail (login), Conversations (login), MoneyManagerEx (database problem).
- APK_LOCATION: The dir location of the app.
- APK_NAME: The current AUT. We have provided an example app MyExpenses.
- DEVICE_ID: The device for testing.
- RESULT_LOCATION: The dir location for saving testing results.
- TIME_LIMIT: The testing time (s).


## Notice
1. Our project is based on python 3.7 while the module main/system_event_trigger need python 2.7 and a venv has been provided for this module under main/system_event_trigger, if there are any problem abount thie module, please at least make sure a python 2.7 venv for it.
2. DQT uses Android tools like ADB, AAPT and AAPT2, please make sure they are available in your system environment.
