# Portable Posture & Balance Analyzer

A wearable device designed to monitor back and shoulder posture in real time, alerting the user via vibration and OLED display when poor posture is detected.

> Work in Progress - PCB design is complete. Firmware development is ongoing.
>
> ## Overview
>
> This project is a health and ergonomics-focused embedded system that tracks posture using an IMU sensor. When poor posture is detected, the device triggers a vibration motor and sends a daily Bluetooth report to a paired device. The system is built around the MSP430G2553 microcontroller.
>
> ## Components
>
> - **MPU6050** - 6-axis IMU (accelerometer + gyroscope)
> - - **Vibration Motor** - Haptic alert for bad posture
>   - - **OLED Display** - Real-time posture score display
>     - - **HC-05 Bluetooth** - Daily report transmission
>       - - **MSP430G2553** - Main microcontroller
>        
>         - ## MSP430G2553 Peripheral Mapping
>        
>         - | Peripheral | Function |
>         - |---|---|
>         - | USCI_B0 | I2C - MPU6050 and OLED |
> | Timer_A | Score period control |
> | GPIO | Vibration motor control |
>
> ### Pin Connections
>
> - MPU6050 -> P1.6 (SCL), P1.7 (SDA)
> - - Vibration Motor -> P2.0
>   - - OLED -> Same I2C bus (different address)
>     - - Bluetooth HC-05 -> P1.1 (RX), P1.2 (TX)
>      
>       - ## How It Works
>      
>       - 1. MPU6050 raw data is read and processed using atan2 for angle calculation
>         2. 2. A posture score is computed every 30 seconds via Timer_A
>            3. 3. If poor posture is detected: vibration motor + OLED alert triggered
>               4. 4. Daily posture report is sent via Bluetooth
>                 
>                  5. ## Project Status
>                 
>                  6. - [x] PCB design complete
>                     - [ ] - [ ] Firmware development in progress
>                     - [ ] - [ ] Testing and calibration
>                     - [ ] - [ ] Enclosure design
