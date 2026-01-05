# STM32F405RGT6 INAV Firmware  
### Custom INAV Flight Controller Firmware

---

## Hardware Overview
- **MCU:** STM32F405RGT6  
- **Maximum Frequency:** 168 MHz  
- **RAM:** 192 KB  
- **Flash (ROM):** 1 MB  

---

## Configuration

INAV firmware is configured primarily through the **INAV Configurator GUI**.  
The configurator version must correspond to the installed INAV firmware version. Always download the correct configurator for the firmware you are using.

Older configurator versions are available here:  
https://github.com/iNavFlight/inav-configurator/releases  

Please read the **README** included with the configurator for installation instructions.

Complete INAV installation and setup documentation can be found at:  
https://github.com/iNavFlight/inav/blob/master/docs

---

## Controls and Arming

Arming is the final safety step that enables your **quadcopter or fixed-wing vehicle** to operate.  
The aircraft will not function unless the arming procedure is completed.

To arm the vehicle:
1. Open **INAV Configurator**
2. Enable arming from the **Arming** section
3. Verify motor and servo outputs from the **Output** tab

<img width="1919" height="822" alt="image" src="https://github.com/user-attachments/assets/b86186fd-6aca-41fb-980f-9c7d185d4f96" />

<img width="1918" height="887" alt="image" src="https://github.com/user-attachments/assets/2f7388b1-7a47-4322-9a2e-501a4ed2d102" />

<img width="1918" height="982" alt="Screenshot 2026-01-04 232839" src="https://github.com/user-attachments/assets/35ebd5e0-ffc1-459f-b162-354527c0d0df" />




Further information about INAV is available through official documentation and YouTube tutorials. Covering all features here is beyond the scope of this document.

---

## Basic Setup

Click images to enlarge.

<img width="2760" height="3336" alt="basic" src="https://github.com/user-attachments/assets/99fe316b-34d1-46df-8523-5b38a99b9b4a" />


### MPU6050 Performance Note

The **MPU6050** sensor operates slowly and may increase **MCU load up to 90%**.

To reduce processor load, execute the following **CLI command**:
`set looptime = 1500`


For better performance, the **MPU6500** sensor is recommended using the **SPI2** interface.

---

## Pin Connections and Details

Detailed pin assignments are shown below.

<img width="3876" height="1912" alt="image" src="https://github.com/user-attachments/assets/38a309e8-08fe-4092-9195-c27db01e67db" />


---

## Supported Sensors


---

## Example SPI2 Sensor Connection

<img width="1147" height="627" alt="image" src="https://github.com/user-attachments/assets/1f455abd-611f-4455-8a4e-9ae5ed40f029" />


The following sensors support **SPI2**. Only **one sensor** can be used at a time:

- MPU6500  
- BMI160  
- BMI270  
- MPU9250  
- ICM42605  

---

## I2C Sensor Connection

Multiple sensors can be connected via **I2C**, provided they are from different categories.  
Only one sensor per type (Gyro, Acc, Baro, Mag) can be used.

<img width="1202" height="638" alt="image" src="https://github.com/user-attachments/assets/11363451-61a3-4fa4-a977-84798748ed82" />


---

## Supported Internal MicroSD Card


---

## External OSD Support

External OSD support can be added using the **MAX7456** chip.  
The MAX7456 must be connected through the **SPI2** interface.

<img width="1570" height="1171" alt="image" src="https://github.com/user-attachments/assets/0721d85f-7597-4e9f-9f16-04a2a0f7d72f" />


---

## Receiver Connection

Receivers are connected via **UART2 RX**.

Supported receiver types:
- SBUS  
- IBUS  
- PPM  

> **SBUS requires an inverter circuit** consisting of one transistor and two resistors.
<img width="1919" height="997" alt="image" src="https://github.com/user-attachments/assets/b0a892ee-59b9-4b23-b82a-e813a2cc4e3c" />

<img width="1919" height="1016" alt="Screenshot 2026-01-04 232749" src="https://github.com/user-attachments/assets/5f8464c3-d01d-4bdf-8c4e-461b761e77d4" />

Steps:
1. Connect receiver signal to **UART2**
2. Enable **Serial RX** on **UART2** in INAV Configurator

<img width="1617" height="1032" alt="image" src="https://github.com/user-attachments/assets/4f3ec78f-08e6-433f-baef-02c682cdbc99" />

<img width="1919" height="997" alt="Screenshot 2026-01-05 164332" src="https://github.com/user-attachments/assets/d1a48217-d48f-4a78-8874-a58cb8adc1b6" />


---

## WS2811 5V LED Strip

- WS2811 LEDs require an **external 5V power source**
- Do **not** power LEDs from the board
- Powering from the board may damage the microcontroller

<img width="1892" height="1060" alt="image" src="https://github.com/user-attachments/assets/5c338cf6-6d35-4c6f-8bdd-9eed694b0420" />


---

## Notes
- Always verify wiring before powering the board  
- Match INAV firmware and configurator versions  
- Prefer SPI-based sensors for improved performance  

---

