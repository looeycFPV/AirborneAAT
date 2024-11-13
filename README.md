# AirborneAAT
This project is about a type of antenna AAT (Airborne - Antenna - Tracking) module, which is for FPV (First - Person - View) UAVs. It aligns the airborne antenna's beam direction to a specified target location (usually the ground control station) based on the GNSS positioning. It is conducive to extending the RF transmission distance and improving the signal quality.
![IMG_20241007_171608_edit_132942220993769](https://github.com/user-attachments/assets/3ddd9013-6e76-4087-b6c9-43321abb0f35)

Part 1: Principle

The antenna dish has multiple sub-antenna lobes, and the beam direction of each lobe is different. First, switch to the antenna lobe closest to the direction of the ground station, and then rotate the antenna dish so that the antenna beam accurately points to the ground station and maintains high gain.
It is necessary to obtain the current position of the aircraft and the position of the ground station from the flight controller, and calculate the relative azimuth of the ground station accordingly.
![1](https://github.com/user-attachments/assets/4f62d73c-6568-459f-8500-c5db37b6409f)

Part 2: Specification Overview

Compatible FC firmware: INAV, Ardupilot (under testing)  
FC Interface Protocol: MAVLink  
FC Interface baude Rate: 115200  
Max RF Power: 1000mw (30dBm)
RF Band: 5.8GHz  
RF Input Impedance: 50Ω  
Antenna Gain: 10dBi  
Power Supply: 2~6S  
Antenna Polarization:	Horizontal  
Dimensions: Diameter 14cm, Height 4cm  
Total Weight: 50g  

Part 3: Connection Instructions

The RF interface of the antenna dish is directly connected to the RF signal output interface of the video transmitter, and the others are respectively connected to the corresponding interfaces of the control board.
In addition to being connected to the antenna dish, the control board also needs to be externally powered (directly connected to the battery output 2s - 6s) and connected to the MAVLink telemetry data output interface of the FC.
![4](https://github.com/user-attachments/assets/707d0d83-6a4f-4e87-ba2b-34402f264ba1)

Part 4: Antenna Installation

![5](https://github.com/user-attachments/assets/cbdc1567-93bf-4203-a823-5e96bcc93e17)

Note: It should be ensured that after installation, when the antenna rotation angle is zero, the sub-lobe 1 is facing towards the nose direction of the aircraft. Otherwise, the RF beam direction will not be able to aligned correctly.

Part 5: Flight Controller Settings

The flight controller must be equipped with GPS(or GNSS) and a magnetic compass (the antenna uses GNSS positioning data and magnetic compass data to calculate the target direction).
The flight controller must enable telemetry data output through the MAVLink data transmission interface. Taking a F405 flight controller board with INAV firmware as an example, in the flight controller settings page, enable GPS navigation telemetry and telemetry output respectively, and enable MAVLink telemetry output of UART4 with a baud rate of 115200. (After setting each page, you must click "Save and Restart")

Part 6: Initial Testing

Step 1: Make good line connections as shown in Part 3. Note that when connecting the video transmitter, please make sure that the transmission power of the video transmitter does not exceed 1000mw. (Excessive power may cause damage to the antenna RF circuit)
Step 2: After power-on, the antenna will immediately rotate to the zero position and stay for several seconds. At this time, please check and confirm that sub-lobe 1 is correctly facing the nose direction of the aircraft (if not, the installation direction needs to be adjusted).
Step 3: Only one of the 6 LEDs on the control board should be turned on (without blinking), indicating which one of the 6 antenna lobes is activated. If any one or more of them are blinking, it indicates a fault (see the following LED fault indication instructions for details).
Step 4: After several seconds, if the antenna dish starts to rotate randomly, it means that the settings are correct and the antenna has started to work. At this time, slowly rotate the flight controller, and the antenna dish should follow the rotation. At the same time, the LED indicator lights will light up in turn, indicating the current beam switching.
Step 5: For outdoor testing, wait for the GPS to complete positioning after power-on, unlock (note safety, it is necessary to remove the propeller blades or disconnect the motor in advance), walk around with the aircraft equipped with the antenna, and observe whether the activated antenna beam is aligned with the original position. Due to the limitation of GPS positioning accuracy, there may be deviations when the distance is close, and the walking distance should be more than 200 meters at least.

Part 7: LED Fault Indication Instructions

LED1 flashing - No MAVLink data received from the FC. Please confirm that the flight controller settings are normal and the connection between the flight controller and the antenna control board is correct.
LED2 flashing - The antenna dish is not detected. Please confirm that the connection between the antenna control board and the antenna dish is correct.

Precautions:

(1) Do not forcibly rotate the antenna dish by external force, otherwise it may cause damage to the antenna servo or impairment of the tracking function.
(2) The video transmission signal power should not exceed 1000 milliwatts (30dBm), otherwise it may cause damage to the antenna RF circuit.
(3) This antenna assembly is only applicable to personal leisure, entertainment, and learning and research purposes.

Have fun!
