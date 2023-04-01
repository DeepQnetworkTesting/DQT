# DQT(pre-released)
## Overview
A pre-released version of DQT and the corresponding experimental data.

## Data
Download all data via: [https://drive.google.com/drive/folders/1O9y88lXGLLmEMC0PHYWHJa0_scid7N59?usp=sharing](https://drive.google.com/drive/folders/1O9y88lXGLLmEMC0PHYWHJa0_scid7N59?usp=sharing)

- logs.zip: Our experimental data, including testing data of 5 tools on 30 open-source apps at 5 rounds. 
   - Directories: data dirs are named like "_Tool Name_-xxxx-xxx-_Round Number_-xx"
   - File names end with "log": The runtime cmd output of the tool.
   - File names end with "bug": The runtime filtered Logcat output.
- DQT_executable.zip: A pre-released executable version of DQT.
   - There is the DQT project with corresponding python libraries packaged by PyInstaller on Ubuntu 18.04 with Python 3.7

## Experimental Environment

- System: Ubuntu 18.04
- Python: 
   - The project is based on python 3.7, except Module _system_event_trigger_ that only supports python 2.7
      - a python 3.7 _venv_ has been provided under "DQT_executable/dist/venv" and a python 2.7 _venv _has been provided under "DQT_executable/dist/main/system_event_trigger/venv"
      - The two provided _venv_ rely on your system's "/usr/bin/python3.7" and "/usr/bin/python2.7"
      - You can either use them directly or replace them with your own under the same directories
   - Make sure that Python 3.7 and Python 2.7 are all available in your ubuntu
      - It is recommended to install python via apt command (e.g., use "ppa:deadsnakes/ppa" source), thus "/usr/bin/python3.7" and "/usr/bin/python2.7" will be directly available
- Deep Learning Environment
   - GPU Driver: 470.161.03
   - CUDA: 11.4
   - Torch: 1.10.0+cu113
- Android Environment
   - Tool Used: ADB, AAPT, AAPT2
   - Make sure these tools are available on system variables to support command-line calls
- Android Emulator
   - Device: Google Pixel 2
   - Resultion: 1080*1920
   - Android Version: Android 9.0 (API Level 28)
   - RAM: 4GB
   - VM Heap: 2GB
   - Internal Storage: 8GB
   - SD Card: 1GB

## Run DQT

1. unzip DQT_executable.zip
2. start an Android Emulator (After starting, use the command "adb devices" to check)
3. enter the python 3.7 _venv_
4. enter the main dir
5. edit config.yaml
6. run main in cmd like ./main

## config.yaml

- ALLOW_CLEAN: Allow the tool to clean app data during testing. 
   - Some apps need login in advance for normal operation. If an app is logged in early, please set this to "false"
   - Special cases such as database conflicts or plug-in missing may require this field to be "false"; otherwise, this field is usually set to "true"
   - Among our 30 experimental apps, these 5 apps need a "false": Signal (login), Tachiyomi (prevent plug-in loss), K9Mail (login), Conversations (login), MoneyManagerEx (database problem)
- APK_LOCATION: The dir location of the app.
- APK_NAME: The App Under Test (AUT). We have provided an example app _MyExpenses_
- DEVICE_ID: The device for testing
- RESULT_LOCATION: The dir location for saving testing results
- TIME_LIMIT: The testing time (s)

## Reference Links

1. Logcat: [https://developer.android.com/studio/command-line/logcat](https://developer.android.com/studio/command-line/logcat)
2. Emulator: [https://developer.android.com/studio/run/emulator](https://developer.android.com/studio/run/emulator)
3. Emulator(cmd): [https://developer.android.com/studio/run/emulator-commandline](https://developer.android.com/studio/run/emulator-commandline)
4. ADB: [https://developer.android.com/studio/command-line/adb](https://developer.android.com/studio/command-line/adb)
5. AAPT2: [https://developer.android.com/studio/command-line/aapt2](https://developer.android.com/studio/command-line/aapt2)
6. Python venv: [https://docs.python.org/3.7/tutorial/venv.html](https://docs.python.org/3.7/tutorial/venv.html)

