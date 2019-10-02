# Melopero_Autostart

## Getting Started
### Prerequisites
You will need:
- a python3 version, which you can get here: download python3
- a linux distro with systemd
    
### Installing
You can install the melopero-autostart module by typing this line in the terminal (Install works only with superuser privileges!):
```python
sudo pip3 install --no-cache melopero-autostart
```
On install the module will create a new directory under your /home/ folder : /home/melopero-autostart/ .
The directory is organized as folllows:

/home/melopero-autostart/
    StartScripts.sh
    instructions.txt
    scripts/
    uninstall/
        uninstall-instructions.txt
        uninstall.sh

Furthermore it will copy a system service unit in your /etc/systemd/system/ folder and enable it. This system service will start the StartScripts.sh script at startup. 

### Usage
To run your python scripts at startup you simply have to copy or move them in the scripts folder (/home/melopero-autostart/scripts/). To write to this folder you will need superuser privileges. Each script will be run in background in a separate process with superuser privileges (!). The output of the python scripts is redirected to log files (each process has it's own log file), this files are generated in the scripts folder. The output is unbuffered, which means that every `print` writes directly to the log file, be careful with print statements they may slow down your process.

### Uninstalling
To uninstall the software correctly you will have to run the uninstall script. Simply enter the uninstall folder and run the script with superuser privileges :
```bash
cd /home/melopero-autostart/uninstall/
sudo ./uninstall.sh
```
This will remove the system service unit, the melopero-autostart folder and the melopero-autostart module from your pc.
