<div align="center">

# Logic42-IOT

### Edge-First, AI-Native IoT Platform

[![Downloads](https://img.shields.io/github/downloads/Buddhi-Kendro/Logic42-IOT/total?color=brightgreen)](https://github.com/Buddhi-Kendro/Logic42-IOT/releases)
[![Latest Release](https://img.shields.io/github/v/release/Buddhi-Kendro/Logic42-IOT?include_prereleases)](https://github.com/Buddhi-Kendro/Logic42-IOT/releases/latest)
[![Docs](https://img.shields.io/badge/Docs-live-blue)](https://doc-logic42-iot-oss.web.app)
[![License](https://img.shields.io/badge/License-Proprietary-red)](LICENSE)

*A complete IoT platform that runs on a Raspberry Pi. Multi-protocol ingestion, auto-device configuration, real-time rules engine, and AI-native MCP integration.*

[Download](#download) · [Documentation](https://doc-logic42-iot-oss.web.app) · [Getting Started](#getting-started) · [Support](#support)

</div>

---

## What is Logic42-IOT?

Logic42-IOT is an **edge-first IoT platform** that runs entirely on a Raspberry Pi 4/5. No cloud dependency required. Connect sensors, auto-detect devices, process data in real-time, and query everything through AI.

### Key Features

| Feature | Description |
|---|---|
| 🔌 **14 Protocols** | MQTT, HTTP, Modbus, LoRaWAN, BACnet, OPC-UA, and more |
| 🧠 **Auto-Configuration** | Fingerprint engine auto-detects device types from payload patterns |
| 🤖 **AI-Native MCP** | Built-in Model Context Protocol — query IoT data with Claude, Cursor, or any AI assistant |
| 👥 **Multi-Tenant** | Isolated tenants with per-tenant data, API keys, and dashboards |
| ⚡ **Real-Time Rules** | Expression-based rules engine with email, webhook, SMS, and Kafka actions |
| 📊 **Dashboard** | Beautiful real-time monitoring UI |
| 🏭 **Industry Verticals** | Water, energy, parking, waste management — built-in |

### Architecture

```
IoT Devices ──► Gateway ──► Kafka ──► Decoder ──► Writer ──► TimescaleDB
                  :8080                  │           │            │
                                    Fingerprint  Rules ──► Notifier
                                    (auto-detect) Engine
                                                              │
                                   Dashboard ◄── MCP Server ◄─┘
                                     :3000        :8081
```

---

## Download

### Pi OS Image (Recommended)

Download the latest pre-built image from [**Releases**](https://github.com/Buddhi-Kendro/Logic42-IOT/releases).

| File | Description | Size |
|---|---|---|
| `logic42-iot-x.x.x.img.xz` | Flashable Pi OS image (Pi 4/5) | ~1.6 GB |
| `logic42-iot-edge-x.x.x.tar.gz` | Docker image bundle (for existing Pi OS) | ~1.2 GB |

### System Requirements

| Component | Minimum | Recommended |
|---|---|---|
| **Board** | Raspberry Pi 4 (4GB) | Raspberry Pi 5 (8GB) |
| **Storage** | 32GB SD card | 64GB+ SD card or NVMe |
| **Network** | Ethernet | Ethernet + WiFi |
| **Power** | Official 5V/3A PSU | Official USB-C PSU |

---

## Getting Started

### Option 1: Flash the Pi Image

1. Download `logic42-iot-x.x.x.img.xz` from [Releases](https://github.com/Buddhi-Kendro/Logic42-IOT/releases)
2. Flash to SD card using [Raspberry Pi Imager](https://www.raspberrypi.com/software/) or [Balena Etcher](https://etcher.balena.io/)
3. Insert SD card and boot your Pi
4. First boot automatically installs Docker and starts all services (~5 min)

```
Default login: bkiot / bkiot
SSH: enabled

Dashboard:  http://<pi-ip>:3000
Gateway:    http://<pi-ip>:8080
MCP Server: http://<pi-ip>:8081
```

### Option 2: Docker Bundle (Existing Pi OS)

If you already have Raspberry Pi OS running:

```bash
# Download and extract the bundle
tar xzf logic42-iot-edge-x.x.x.tar.gz
cd logic42-iot-edge

# Install (requires sudo)
sudo ./install.sh
```

---

## MCP Integration

Connect your AI assistant to query IoT data in natural language:

```json
{
  "mcpServers": {
    "logic42-iot": {
      "url": "http://<pi-ip>:8081/sse",
      "transport": "sse"
    }
  }
}
```

Then ask your AI: *"Show me all water meters with flow rate above 50 L/min in the last hour"*

---

## Documentation

Full documentation at **[doc-logic42-iot-oss.web.app](https://doc-logic42-iot-oss.web.app)**

- [Getting Started](https://doc-logic42-iot-oss.web.app/getting-started/overview/)
- [Architecture](https://doc-logic42-iot-oss.web.app/getting-started/architecture/)
- [Hardware Requirements](https://doc-logic42-iot-oss.web.app/getting-started/hardware/)
- [API Reference](https://doc-logic42-iot-oss.web.app/api/authentication/)
- [MCP Integration](https://doc-logic42-iot-oss.web.app/mcp/overview/)
- [User Guide](https://doc-logic42-iot-oss.web.app/user-guide/flash-sd-card/)
- [Troubleshooting](https://doc-logic42-iot-oss.web.app/user-guide/troubleshooting/)

---

## Services Included

| Service | Description |
|---|---|
| **Gateway** | Multi-protocol IoT data ingestion |
| **Decoder** | Plugin-based payload decoding |
| **Writer** | High-performance batch writer to TimescaleDB |
| **Rules Engine** | Expression-based real-time alerting |
| **Notifier** | Multi-channel notifications (email, webhook, SMS) |
| **Fingerprint Engine** | Automatic device type detection |
| **Scheduler** | Cron-like task scheduling |
| **Archiver** | Data lifecycle and retention management |
| **MCP Server** | AI-native Model Context Protocol |
| **API Gateway** | REST API with JWT authentication |
| **Dashboard** | Real-time monitoring and management UI |
| **Phone Home** | Edge-to-cloud heartbeat and management |
| **Verticals** | Industry-specific analytics (water, energy, etc.) |

---

## Support

- 📖 [Documentation](https://doc-logic42-iot-oss.web.app)
- 🐛 [Report Issues](https://github.com/Buddhi-Kendro/Logic42-IOT/issues)
- 💬 [Discussions](https://github.com/Buddhi-Kendro/Logic42-IOT/discussions)
- 📧 Contact: customersuccess@buddhikendro.com

---

## License

Logic42-IOT is proprietary software developed by [Buddhi-Kendro](https://github.com/Buddhi-Kendro).

Pre-built images are provided free for evaluation and non-commercial use. For commercial licensing, contact [customersuccess@buddhikendro.com](mailto:customersuccess@buddhikendro.com).

See [LICENSE](LICENSE) for full terms.

---

<div align="center">

**Built by [Buddhi-Kendro](https://github.com/Buddhi-Kendro)**

*Edge intelligence for the real world.*

</div>
