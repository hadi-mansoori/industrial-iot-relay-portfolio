
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
   - [Mechanical & Thermal Design](#mechanical--thermal-design)  
6. [Software & IoT Integration](#software--iot-integration)  
   - [User & Access Management](#user--access-management)  
   - [Supported Protocols](#supported-protocols)  
   - [Dashboard & Controls](#dashboard--controls)  
7. [System Architecture & Diagrams](#system-architecture--diagrams)  
   - [CI/CD Pipeline](#cicd-pipeline)  
   - [Microservices Architecture](#microservices-architecture)  
   - [PWM Fan Control](#pwm-fan-control)  
8. [Source & Relay Handling](#source--relay-handling)  
9. [PCB & Production Notes](#pcb--production-notes)  
10. [Future Plans](#future-plans)  
11. [Notes](#notes)

---

## 📸 Device Photos
<a id="device-photos"></a>

| ![16-Channel Relay Board](docs/relay-x16.png) | ![Mansoori Relay Case](docs/mansoori-relay-case.png) |
|-----------------------------------------------|------------------------------------------------|

---

## 🎬 Demo Videos
<a id="demo-videos"></a>

| [![Case Demo](docs/case-thumbnail.png)](https://drive.google.com/file/d/1MGCB0fB2KWl_RKL3cDo0bGKrn-c_zvfe/view?usp=sharing)| [![Hardware Demo](docs/Hardware-thumbnail.png)](https://drive.google.com/file/d/17JpMd7C1Y9j4aAa2YxCbYHXK-l0a70tc/view?usp=sharing) |
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
| **Realu module** | 4x4 Isolated Relay Module |


### Mechanical & Thermal Design
<a id="mechanical--thermal-design"></a>

- Components mounted on **two 9×9 cm aluminum plates**  
- **1 mm silicone layer** between PCB and aluminum plate for insulation  
- Raised screws (~2.5 cm) for improved airflow  
- Heat-sensitive parts reinforced with heatsinks and aluminum inserts  

---

## 💻 Software & IoT Integration
<a id="software--iot-integration"></a>

### User & Access Management
<a id="user--access-management"></a>

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
<a id="dashboard--controls"></a>

- Live monitoring of **fan status and temperature**  
- Touchscreen can be disabled; control via web interface (IP-based)  
- Admin can define users, assign roles, and control relay permissions  

---

## 🏗 System Architecture & Diagrams
<a id="system-architecture--diagrams"></a>

### CI/CD Pipeline
<a id="cicd-pipeline"></a>

```text
Hardware:                       CI/CD:

┌───────────────┐               ┌─────────────┐
│  Power Supply │               │  Git Repo   │
│  Mean Well    │               │ (Firmware & │
│  RS-15-5      │               │   API Code) │
└──────┬────────┘               └─────┬───────┘
       │ 5V/12V                       │ Push / Commit
       ▼                               ▼
┌───────────────┐               ┌─────────────┐
│ ESP32 Type-C  │               │   Jenkins   │
│    32U MCU    │               │  CI/CD Node │
└──────┬────────┘               └─────┬───────┘
       │ GPIO / PWM                  │ Build & Test
 ┌─────┴─────────┐                   ▼
 │ Relay Module  │            ┌─────────────────────┐
 │ 16-Ch         │            │  API Deployment     │
 └───────────────┘            └─────┬───────────────┘
       │                               │ Secure Routing
       ▼                               ▼
┌───────────────┐               ┌─────────────┐
│ SSR / Load    │               │ Nginx       │
│ Industrial    │               │ Gateway     │
│ Devices       │               └─────┬───────┘
└───────────────┘                     │ Routes Requests
                                       ▼
                                 ┌─────────────┐
                                 │ Relay       │
                                 │ Controller  │
                                 │ (ESP32)     │
                                 └─────────────┘
```

---

## 🔹 Source & Relay Handling
<a id="source--relay-handling"></a>

- **Relay Modules:** The system uses **4×4-channel isolated relay modules**, providing a total of 16 channels.  
- **Isolation:** Each module is fully isolated, protecting the **ESP32 control board** from industrial voltage spikes.  
- **Triggering SSRs & Coils:** The relays can directly control **Solid State Relays (SSR)**, coils, or other high-current devices.  
- **Industrial Rating:** Each relay can handle **220V AC, 10–15A**, making them suitable for industrial applications.  
- **Control Flow:**  
```text
ESP32 GPIO --> 4x4 Isolated Relay Module --> Industrial Relays / SSRs / Coils
```
- **Software Control:** ESP32 receives commands via **FastAPI, MQTT, Webhooks, or Web Interface** and toggles the GPIO pins to activate the corresponding relay module channels.  
- **Protection & Cooling:** PWM-controlled fans and thermal sensors ensure **SSR and relay safety** under load conditions.  

---

## 📌 PCB & Production Notes
<a id="pcb--production-notes"></a>

- Double-sided metallized PCB, industrial-grade  
- Components soldered and inspected manually  
- Thermal vias and heatsinks applied for high-current tracks  

---

## 🔮 Future Plans
<a id="future-plans"></a>

- LoRa wireless integration  
- AI-assisted predictive relay scheduling  
- Remote firmware updates via secure OTA  

---

## 📝 Notes
<a id="notes"></a>

- Ensure **proper grounding** when connecting industrial loads  
- Verify SSR and relay ratings before switching high-current devices  
- Keep enclosure ventilated for optimal fan cooling
