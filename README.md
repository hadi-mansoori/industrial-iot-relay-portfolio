# Industrial IoT Relay Portfolio – Mansoori x16

The **Mansoori x16** is a 16-channel industrial-grade IoT relay controller built with **ESP32 Type-C 32U** firmware and a **FastAPI backend**. Designed for industrial automation, it features robust hardware protection, a touchscreen interface with AI-assisted design, and secure IoT connectivity. The device is housed in a custom **“Mansoori Relay Case”**, engineered for cooling efficiency and industrial reliability.

---

## 📋 Table of Contents
1. [Device Photos](#device-photos)  
2. [Demo Videos](#demo-videos)  
3. [Project Highlights](#project-highlights)  
4. [Skills Demonstrated](#skills-demonstrated)  
5. [Hardware Overview](#hardware-overview)  
   - [Core Components](#core-components)  
   - [Mechanical & Thermal Design](#mechanical-thermal-design)  
6. [Software & IoT Integration](#software-iot-integration)  
   - [User & Access Management](#user-access-management)  
   - [Supported Protocols](#supported-protocols)  
   - [Dashboard & Controls](#dashboard-controls)  
7. [PCB & Production Notes](#pcb-production-notes)  
8. [Future Plans](#future-plans)  
9. [Notes](#notes)

---

## 📸 Device Photos
<a id="device-photos"></a>

| ![16-Channel Relay Board](docs/relay-x16.png) | ![Mansoori Relay Case](docs/mansoori-relay-case.png) |
|-----------------------------------------------|------------------------------------------------|

---

## 🎬 Demo Videos
<a id="demo-videos"></a>

| [![Case Demo](docs/case-thumbnail.png)](https://drive.google.com/file/d/1MGCB0fB2KWl_RKL3cDo0bGKrn-c_zvfe/view?usp=sharing) | [![Hardware Demo](docs/Hardware-thumbnail.png)](https://drive.google.com/file/d/17JpMd7C1Y9j4aAa2YxCbYHXK-l0a70tc/view?usp=sharing) |
|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|

---

## 🚀 Project Highlights
<a id="project-highlights"></a>

- **16-channel relay control** with industrial-grade protection for SSRs and high-amp devices  
- **Secure IoT communication:** MQTT, REST API, Webhooks, Wi-Fi, and LoRa-ready infrastructure  
- **Role-based access control:** multi-user management with individual relay permissions  
- **2.8” Nextion touchscreen GUI** with dashboards **designed with AI-assisted graphics** and refined in Photoshop  
- **PWM fan control** based on temperature (>40°C fan ON, <40°C fan OFF)  
- **Firmware CI/CD pipeline** for seamless updates  

---

## 🛠 Skills Demonstrated
<a id="skills-demonstrated"></a>

- **Embedded Systems:** ESP32 Type-C 32U, PWM, Relay Modules  
- **IoT & Networking:** MQTT, Webhooks, Wi-Fi, LoRa-ready  
- **Backend & API:** FastAPI, REST API, JWT authentication, Role/Scope-based access control  
- **Hardware & Power Management:** Thermal & surge protection, industrial power supply integration  
- **Additional Backend Skills:** Laravel, NestJS, Express.js  
- **DevOps:** CI/CD workflows for firmware deployment  

---

## 🔧 Hardware Overview
<a id="hardware-overview"></a>

### Core Components
<a id="core-components"></a>

| Component | Description |
|-----------|-------------|
| **Microcontroller** | ESP32 Type-C 32U |
| **Network Module** | W5500 Ethernet module with SPI interface |
| **PCB** | Green double-sided metallized PCB, industrial-grade and high-strength |
| **Enclosure** | Custom **Mansoori Relay Case**, metal box with raised aluminum plates (2.5 cm from base) for airflow and cooling |
| **Power Input** | 3-pin grounded power socket with glass fuses (2A fast-blow, 3A slow-blow) |
| **Power Supply** | Mean Well RS-15-5 |
| **Relay Control** | 16-channel via Makazol Expander Module |
| **Cooling** | Dual Raspberry Pi fan 320 mA, PWM controlled |
| **Temperature Sensor** | Activates fan >40°C, deactivates <40°C |
| **Capacitors** | 1000µF, 100µF, 10µF, 104 ceramic for filtering and transient suppression |
| **Heat Management** | Aluminum heatsinks with heat-resistant adhesive for critical components |
| **Cabling** | Handcrafted, sorted, and properly housed |
| **SSR Compatibility** | Can trigger industrial Solid State Relays for high-current devices |

### Mechanical & Thermal Design
<a id="mechanical-thermal-design"></a>

- Components mounted on **two 9×9 cm aluminum plates**  
- **1 mm silicone layer** between PCB and aluminum plate for insulation  
- Raised screws (~2.5 cm) for improved airflow  
- Heat-sensitive parts reinforced with heatsinks and aluminum inserts  

---

## 💻 Software & IoT Integration
<a id="software-iot-integration"></a>

### User & Access Management
<a id="user-access-management"></a>

- Multi-user management with **role-based permissions**  
- Relays can be renamed on the touchscreen  
- Users can **change their own passwords**  
- Admin can manage Wi-Fi credentials and user access  

### Supported Protocols
<a id="supported-protocols"></a>

- Internet (wired & Wi-Fi)  
- **MQTT**  
- **Webhooks**  
- **LoRa wireless** (infrastructure ready, not yet active)  
- REST API with JWT-based scope access  

### Dashboard & Controls
<a id="dashboard-controls"></a>

- Live monitoring of **fan status and temperature**  
- Touchscreen can be disabled; control via web interface (IP-based)  
- Admin can define users, assign roles, and control relay permissions  

---

## 📐 PCB & Production Notes
<a id="pcb-production-notes"></a>

- New PCB design exists but was **not mass-produced** due to low volume and cost-efficiency  
- Green double-sided metallized PCB used instead  
- Raised aluminum plates allow **efficient heat dissipation**  

---

## 🔮 Future Plans
<a id="future-plans"></a>

- Develop a **web-based control panel** with scenario scripting and industrial automation capabilities  

---

## 📝 Notes
<a id="notes"></a>

- Firmware source code is **private for security reasons**  
- Touchscreen interface fully **designed and programmed in Nextion IDE**, with **graphics designed using AI-assisted design tools**  
- Device supports **industrial automation, high-current relay control, and secure IoT operations**  
- LoRa integration prepared for future expansion
