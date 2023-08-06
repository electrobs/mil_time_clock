# Military Time Clock

Military Time Clock using the 89S51 microcontroller.

author: Jay Convertino

date: 2022.12.11

license: MIT (software/hardware)

IMPORTANT: No build instructions are included. All parts needed are here, you're on your own.

## Release Versions
### Current
  - v1.0.2 = Fixed time base issues with a smaller range tuning cap.

### Past
  - v1.0.1 = Sound buzz fixed with feedback bypass resistor.
  - v1.0.0 = Original Version


## Requirements
### Hardware
  - KiCad (v7.X.X)

### Software
  - sdcc compiler (4.0.0 #11528)

## Information

### Directory Listing:

  - docs
    - Datasheets: Data documents for various ICs.
    - Manual: User manual for the clock.
  - schematic: KiCad schematic of Military Time Clock, including PCB design and bill of materials.
  - model
    - FreeCAD: Any FreeCAD models used in the project.
    - Inventor: Any Autodesk Inventor 2023 models used in the project (STL included).
  - src: Any source code for the project.
    - clock_sdcc: contains make file and code for the clock project.

### Usage
  Please see the user manual on how to use the project. Build instructions really depend on how you want to build it. It uses all through hole parts and could be done with something as simple as an etch kit, PCB mill, or a PCB fab.

### Tuning
  Recommend using a platic tuning tool to adjust trimmer cap. Track the freqency at the 2.048kHz and lower pins till they all match there expected outputs (all powers of two, 1024, 512, 128 etc). Also let the device run for about 15 minutes and check. Frequency will rise by 1 to 2 hz and then stablize within the first 30 seconds, but it is wise to triple check after some time has passed.
