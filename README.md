# AirborneAAT
This project is about a type of antenna AAT (Airborne - Antenna - Tracking) module, which is for FPV (First - Person - View) UAVs. It aligns the airborne antenna's beam direction to a specified target location (usually the ground control station) based on the GNSS positioning. It is conducive to extending the RF transmission distance and improving the signal quality.

Part 1: Principle
The antenna dish has multiple sub-antenna lobes, and the beam direction of each lobe is different. First, switch to the antenna lobe closest to the direction of the ground station, and then rotate the antenna dish so that the antenna beam accurately points to the ground station and maintains high gain.
It is necessary to obtain the current position of the aircraft and the position of the ground station from the flight controller, and calculate the relative azimuth of the ground station accordingly.

Part 2: Specification Overview
Compatible flight control firmware: INAV, Ardupilot (under testing)
FC Interface Protocol: MAVLink
FC Interface baude Rate: 115200
Max RF Power: 1000mw
RF Band: 5.8GHz
RF Input Impedance: 50Ω
Antenna Gain: 10dBi
Power Supply: 2~6S
Antenna Polarization:	Horizontal
Dimensions: Diameter 14cm, Height 4cm
Total Weight: 50g
