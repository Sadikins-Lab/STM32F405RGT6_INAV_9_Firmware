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

![Arming Screen](image)  
![Output Tab](image)

<img width="1918" height="982" alt="Screenshot 2026-01-04 232839" src="https://github.com/user-attachments/assets/35ebd5e0-ffc1-459f-b162-354527c0d0df" />




Further information about INAV is available through official documentation and YouTube tutorials. Covering all features here is beyond the scope of this document.

---

## Basic Setup

Click images to enlarge.

![Basic Setup](image)

### MPU6050 Performance Note

The **MPU6050** sensor operates slowly and may increase **MCU load up to 90%**.

To reduce processor load, execute the following **CLI command**:
`set looptime = 1500`


For better performance, the **MPU6500** sensor is recommended using the **SPI2** interface.

---

## Pin Connections and Details

Detailed pin assignments are shown below.

![Pinout](image)  
![Pin Details](image)  
![Additional Pin Details](image)

---

## Supported Sensors

![Supported Sensors](image)

---

## Example SPI2 Sensor Connection

![SPI2 Sensor Connection](image)

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

![I2C Sensor Connection](image)

---

## Supported Internal MicroSD Card

![MicroSD Support](image)

---

## External OSD Support

External OSD support can be added using the **MAX7456** chip.  
The MAX7456 must be connected through the **SPI2** interface.

![External OSD](image)  
![MAX7456 Wiring](image)

---

## Receiver Connection

Receivers are connected via **UART2 RX**.

Supported receiver types:
- SBUS  
- IBUS  
- PPM  

> **SBUS requires an inverter circuit** consisting of one transistor and two resistors.

<img width="1919" height="1016" alt="Screenshot 2026-01-04 232749" src="https://github.com/user-attachments/assets/5f8464c3-d01d-4bdf-8c4e-461b761e77d4" />

Steps:
1. Connect receiver signal to **UART2**
2. Enable **Serial RX** on **UART2** in INAV Configurator

![Receiver Wiring](image)  
![UART Configuration](image)

---

## ESC and Motor Connection

![ESC and Motor Connection](image)

---

## ESC and Servo Connection

![ESC and Servo Connection](image)

---

## Motor, ESC, and LiPo Battery Connection

The diagram below shows an example motor and LiPo battery wiring.  
Motor order must match the sequence configured in **INAV Configurator**.

![Motor and Battery Connection](image)

---

## Battery Monitoring

To monitor LiPo battery voltage:
- Use a **voltage divider**
- Connect output to **VBAT_ADC_CHANNEL (PC4)**

⚠ The voltage at **PC4 must not exceed 3.3V**  
⚠ Voltages above **5V will damage the board**

Voltage divider calculator:  
https://ohmslawcalculator.com/voltage-divider-calculator

![Battery Monitor](image)

---

## WS2811 5V LED Strip

- WS2811 LEDs require an **external 5V power source**
- Do **not** power LEDs from the board
- Powering from the board may damage the microcontroller

![WS2811 LED Connection](image)

---

## Notes
- Always verify wiring before powering the board  
- Match INAV firmware and configurator versions  
- Prefer SPI-based sensors for improved performance  

---

