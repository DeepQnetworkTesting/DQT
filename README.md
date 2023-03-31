# DQT(pre-released)
## Overview
A pre-released version of DQT and the corresponding experimental data.

## Data
Download all data via: [https://drive.google.com/drive/folders/1O9y88lXGLLmEMC0PHYWHJa0_scid7N59?usp=sharing](https://drive.google.com/drive/folders/1O9y88lXGLLmEMC0PHYWHJa0_scid7N59?usp=sharing)

- logs.zip: Our experimental data, including testing data of 5 tools on 30 open-source apps at 5 rounds. 
   - Directories: named like <Tool Name>-xxxx-xxx-<Round Number>-xx
   - File names end with "log": The runtime cmd output of the tool.
   - File names end with "bug": The runtime filtered Logcat output.
- DQT_executable.zip: A pre-released executable version of DQT.
   - There is the DQT project with corresponding python libraries packaged by PyInstaller on Ubuntu 18.04 with Python 3.7

## Experimental Environment

- System: Ubuntu 18.04
- Python: 3.7.12
   - except Module _system_event_trigger_, since it only supports python 2.7
      - a venv has been provided for it under main/system_event_trigger/venv
      - if there is problem with this module, you can remove it and rebuild one
      - but please at least make sure a python 2.7 venv under main/system_event_trigger/venv is available
- Deep Learning Environment
   - GPU Driver: 470.161.03
   - CUDA: 11.4
   - Torch: 1.10.0+cu113
- Android Environment
   - ADB, AAPT, AAPT2
   - Make sure these tools are available on system variables to support command-line calls

## Run DQT

1. unzip DQT_executable.zip
2. start an Android Emulator
3. enter a python 3.7 venv (the python 3.7.12 venv we have provided or build your own)
4. enter the main dir
5. edit config.yaml
6. run main in cmd like ./main

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

## Reference Links

1. Logcat: [https://developer.android.com/studio/command-line/logcat](https://developer.android.com/studio/command-line/logcat)
2. Emulator: [https://developer.android.com/studio/run/emulator](https://developer.android.com/studio/run/emulator)
3. ADB: [https://developer.android.com/studio/command-line/adb](https://developer.android.com/studio/command-line/adb)
4. AAPT2: [https://developer.android.com/studio/command-line/aapt2](https://developer.android.com/studio/command-line/aapt2)
5. Python venv: [https://docs.python.org/3.7/tutorial/venv.html](https://docs.python.org/3.7/tutorial/venv.html)

