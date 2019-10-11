# ChangeLog

This document shows the changes per release

## Current Head

  * Improvements to HomeAssistant EMS module to avoid setting Consumption/Generation values to zero as a result of a connection failure, and better exception handling in general for the module.
  * Separation of Slave TWC code from Master TWC code - this adds stability by removing a large number of global variables and reduces complexity for future feature improvements.

## v1.1.0 - Current testing branch

### New Features

  * Separation of Tesla API class from TWCManager code, this allows pluggable modules for interfacing with vehicles.
  * Added Fronius EMS module - read generation and consumption values from a Fronius inverter.

## v1.0.2 - 2019-10-11

  * Option to subtract charger utilization from consumption value if consumption meter is counting charger load.
  * Updated status output to more clearly define the generation and consumption values being tracked.

## v1.0.1 - 2019-10-06

This release is a bugfix release for v1.0.0. It contains the following fixes:

  * Fixed: MQTT status connection timeout causes a delay to heartbeat timers, which then cause TWCManager reconnections to Slaves
  * Fixed: MQTT and HASS status update rates are too high. All updates now rate limited to one per minute.

## v1.0.0 - 2019-10-05

This module provides HomeAssistant sensor functionality to the TWCManager project. It is the first release after the fork and restructuring of the code and configuration files.

### New Features

  * Forked original repository by cdragon
  * Integrated multi-charger and multi-car MQTT integration (Status Module) from flodorn's repository
  * Split the Sensor (EMS) and Status functions out of the main script
  * Created HomeAssistant EMS and Status modules and tested successfully
  
### Known Issues

  * No MQTT authentication is available currently. This will be fixed in an upcoming patch (v1.1.0).
  * Large numbers of uncaught exceptions around connectivity for EMS and Status interfaces - These can be safely ignored, they will be fixed in v1.1. Currently, they will only result in excessive logging.
  
### Future Changes

  * Split TWCMaster class for code readability
  * Separate class for serial communications - so TWCMaster and TWCSlave don't both need to speak to the serial port directly
  * Modular serial interface - allow dummy module to be substituted for testing (along with above work)
