# tracking-uas
Basic UAS control with AI object tracking to allow a UAS to track a moving landing zone (say, quadcoptor landing on moving boat or trailer)

Project to combine multiple areas of interest.  Some have been well-defined and it would be easier to "stand on the shoulders of giants", but starting from nothing enables a low-level understanding, so...

- Asymmetric Multi-Processor (AMP) usage
- Low-level UAV flight controller (FC)
- AI/ML object detection

Initial notes:
Basic flight controller provides steady flight.
Object detection provides directional control over IPC to FC when a specific object is detected.
Limited budget drives design decisions (as in real programs)
Zynq FPGA IP provides interfaces to external components.  
Microprocessor Core0 running FreeRTOS provides flight control.
Core1 running Linux provides object detection.
Use OpenAMP to communicate across cores
See UG1186 for OpenAMP app note on using with Xilinx Zynq
MYIR Zynq board (w/ breakout)
Use exisitng scratchbuilt drone body, ESCs, motors, receiver, transmitter

VMS (Vehicle Mgt System):
- FPGA IP:
  * PWM for motor control (use cheap ESCs)
  * GPS: process NMEA messages
  * RX: process receiver commands for manual flight
- Core0 FreeRTOS
  * FLight control
  * OpenAmp for IPC to core1
 
AI/ML Object Detection (Core1):
- Linux
- Python
- TensorFlow Lite
- OpenCV
- OpenAMP for IPC to Core0
- WiFi for mission status

![image](https://github.com/user-attachments/assets/c59bcf3b-73ac-4367-b6d8-87f9d33dc13a)
 

