### System Overview (Hardware & CI/CD Side-by-Side)

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
 │               │            ┌─────────────────────┐
 │ Relay Module  │            │  API Deployment     │
 │ 16-Ch         │            │ (Internal Network)  │
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
