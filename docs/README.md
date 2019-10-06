# TWCManager Documentation

## Physical (RS-485) Installation

Please see the [Installation Guide](InstallationGuide.md) for detailed information on the installation of the Tesla Wall Connector interface to TWCManager.

## Software Installation

### Install necessary python modules
```
pip3 install commentjson paho-mqtt pyserial sysv_ipc
```

### Clone GIT Repository and copy files
```
git clone https://github.com/ngardiner/TWCManager
cd TWCManager
git checkout v1.0.1
make install
```

### Configure TWCManager
After performing the installation tasks above, edit the /etc/twcmanager/config.json file and customize to suit your environment.

### Running the script
*To be completed shortly*

## Frequently Asked Questions

### How many units can be set up in this fashion?

The TWC Load Balancing protocol allows for up to four units within a group. As we are occupying one of the TWC Load Balancing unit IDs in order to provide the Master control of the charger group, there may be a total of three other units connected. When connecting additional units, they should be chained from the unused (In or Out) RS-485 terminals of the unit that is currently connected to TWCManager, which will allow all (up to) three of the units to be managed by one TWCManager instance.

### What can I do if my TWC is showing a red light blinking on the front of the unit?

This is because it has identified an error. If this occurred after starting the TWCManager.py script, it is highly likely that it has been caused by the TWCManager script.

Check the output of the TWCManager.py script. This will show you the reason for the error if it has been detected by the script. For example, if your rotary switch has not been adjusted to make the TWC a slave unit, you will see the following warning:

```
03:38:12 ERROR: TWC is set to Master mode so it can't be controlled by TWCManager.  Search installation instruction PDF for 'rotary switch' and set switch so its arrow points to F on the dial.
```

Similarly, if you are not running the TWCManager.py script and your TWC is set to Slave Mode, the same error condition will be shown via the TWC blinking red LED. In both cases, the error code is green: solid and red: 4 blinks. If you have any other error condition shown, refer to the table in your TWC user guide for specific details.
