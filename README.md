# 7.2kW EVSE Board - STM32F401, ADE7953, AFE3010, AZEV200

## Overview

This project is a custom-designed Single-Phase 7.2kW EVSE (Electric Vehicle Supply Equipment) control board built around the **STM32F401** microcontroller. The board integrates advanced energy metering, EV-specific safety mechanisms, communication expansion headers, and an isolated power supply, forming a complete and scalable EVSE solution.

---

## Features

- ⚡ **7.2kW Power Support**
- 🔌 **EV Relay Control using AZEV200**
- 📊 **Real-time Power Monitoring via ADE7953**
- 🔐 **Leakage & Earth Fault Detection via AFE3010**
- 🔄 **Communication Expansion (USART/SPI)**
- 🔋 **Integrated Flyback Power Supply using InnoSwitch3-EP**

---


## Components Description

### 1. **STM32F401 Microcontroller**
- Acts as the **main controller** of the EVSE.
- Interfaces with:
  - ADE7953 for metering data (SPI)
  - AFE3010 for fault monitoring (analog/digital lines)
  - External modules via USART headers allows for further expansion in future with a communication board.
  - Optional SPI TFT display for GUI
- Manages control logic, user interface, charging session state, and error handling.

---

### 2. **ADE7953 - Energy Metering IC**
- Provides **accurate measurement** using integrated **sigma-delta ADCs ** of:
  - Voltage
  - Current
  - Active and reactive power
  - Power factor
- Communicates with STM32 via **SPI**.
- Useful for:
  - Billing
  - Power monitoring
  - Compliance with EV charging standards

---

### 3. **AFE3010 - EV Leakage Detection and Monitoring**
- Provides **earth fault protection** and **leakage current detection**.
- Critical for:
  - Detecting AC/DC leakage
  - Complying with IEC 62752 standard for EVSE
- The ALARM pin of the IC is connected to the MCU, which can be programmed to react to a fault condition accordingly.

---

### 4. **AZEV200 Relay (Zettler)**
- High-current **7.2kW capable relay** for connecting/disconnecting the vehicle from the mains supply.
- Controlled via a relay driver circuit by the STM32.
- Provides galvanic isolation and compliance with safety regulations for EV charging.
- Capable of 50k cycles and compatible with CC2 standards.
- 3PST Relay

---

### 5. **Flyback Power Supply (InnoSwitch3-EP PowiGaN 750 Controller)**
- Supplies isolated power to all board components.
- Designed using **Power Integrations’ online tool**.
- Features:
  - High efficiency
  - Integrated feedback and switching
  - Provides -14,+14 and 5V output rails.

---

### 6. **External Communication Interfaces**
#### USART Headers:
- For **debugging**, **firmware updates**, or **add-on modules** like Wi-Fi/Bluetooth.

#### SPI Display Header:
- Allows connection to an **optional external TFT display**.
- Useful for real-time visual feedback like voltage, current, charging status, and errors.

---

### 7. **Control Pilot Signal Generation**
- The board has a dedicated control pilot output terminal for communication with vehicle.
- Designed in compliance with SAE J1772 Standard.
- Components used in Control Pilot Circuit:
  - TLV1805DBVR Rail to Rail Opamp
  - Seperate Detection Circuit to allow for CP line voltage detection by MCU.
  - SMAJ14CA Voltage Suppressor.

---

## Expansion & Applications

This board is modular and can be extended for:
- **Smart EVSE implementations**
- **Home automation systems**
- **Commercial charging stations**
- **Portable EV charging solutions**

---

## Safety & Compliance

- Designed with **isolation barriers**, **EMI filtering**, and **fault detection**.
- Supports **earth leakage protection**, **overcurrent handling**, and **relay safety shutdown** features.

---

## Future Enhancements

- Integration with OCPP (Open Charge Point Protocol)
- Mobile app support via BLE or Wi-Fi
- Real-time data logging via SD card or cloud

---

## Getting Started

### Powering the Board
- Connect AC mains to the input terminals.
- The flyback power supply will generate required 5V/3.3V rails.

### Programming the MCU
- Use the USART header with a USB-to-Serial adapter.
- Flash firmware via STM32CubeProgrammer or ST-Link.

### Monitoring & Debugging
- Use USART for serial output.
- Attach an SPI display for GUI testing.

---

## License
This project is open for educational and non-commercial use. Contact the author for other licensing.

---

## Author
**Madhav Maheshwari**



