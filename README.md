# SPIRIT Smartphone – Documentation

<p align="center">
    <img src="https://github.com/user-attachments/assets/60e87523-02cf-482b-8433-5f611e48ca2d" width="40%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Documentation-Complete-brightgreen">
  <img src="https://img.shields.io/badge/License-Open%20Source-blue">
  <img src="https://img.shields.io/badge/Project-SPIRIT-purple">
</p>

---

## About This Repository

This is the **comprehensive documentation hub** for the SPIRIT Smartphone project – an open-source smartphone designed to put control, repairability, and privacy back in the hands of users.

This repository contains all documentation, guides, specifications, and resources needed to understand, build, modify, and contribute to the SPIRIT project.

---

## Project Overview

**SPIRIT** breaks away from locked-down devices by:

1. **Empowering the user** – you decide what runs and what's connected
2. **Ensuring privacy** – hardware switches physically cut off mic, camera, GPS, and cellular radios  
3. **Encouraging community collaboration** – hardware, firmware, and documentation are all open

---

## Quick Links to Project Repositories

| Repository | Purpose | Link |
|------------|---------|------|
| **Main Project** | Entry point & project overview | [spirit](../spirit) |
| **Hardware Design** | KiCad schematics, PCB layouts, mechanical | [spirit-design](../spirit-design) |
| **Software/OS** | AOSP Android build for Raspberry Pi 5 | [spirit-os](../spirit-os) |
| **Documentation** | Complete project documentation (this repo) | [spirit-docs](../spirit-docs) |

---

## Documentation Structure

```
📁 spirit-docs/
├── 📄 README.md                    # This file
├── 📁 getting-started/              # New user guides
│   ├── 📄 project-overview.md       # Detailed project introduction
│   ├── 📄 quick-start.md           # Get up and running quickly
│   └── 📄 faq.md                   # Frequently asked questions
├── 📁 hardware/                     # Hardware documentation
│   ├── 📄 specifications.md         # Complete hardware specs
│   ├── 📄 schematics-guide.md      # Understanding the schematics
│   ├── 📄 pcb-layout.md            # PCB design explanations
│   ├── 📄 bom.md                   # Bill of materials details
│   ├── 📄 assembly-guide.md        # Hardware assembly instructions
│   └── 📄 troubleshooting.md       # Hardware troubleshooting
├── 📁 software/                     # Software documentation
│   ├── 📄 os-overview.md           # AOSP build overview
│   ├── 📄 building-aosp.md         # Detailed build instructions
│   ├── 📄 driver-development.md    # Driver development guide
│   ├── 📄 customization.md         # Customizing the OS
│   └── 📄 debugging.md             # Software debugging guide
├── 📁 development/                  # Developer resources
│   ├── 📄 contributing.md          # How to contribute
│   ├── 📄 development-setup.md     # Setting up dev environment
│   ├── 📄 coding-standards.md      # Code style and standards
│   ├── 📄 testing.md               # Testing procedures
│   └── 📄 roadmap.md               # Project roadmap
├── 📁 user-guides/                  # End-user documentation
│   ├── 📄 using-spirit.md          # Using your SPIRIT phone
│   ├── 📄 privacy-features.md      # Privacy switch usage
│   ├── 📄 apps-and-software.md     # Recommended apps
│   └── 📄 maintenance.md           # Device maintenance
├── 📁 community/                    # Community resources
│   ├── 📄 code-of-conduct.md       # Community guidelines
│   ├── 📄 support.md               # Getting help
│   ├── 📄 discord.md               # Discord server info
│   └── 📄 events.md                # Community events
└── 📁 assets/                       # Documentation assets
    ├── 📁 images/                   # Images and diagrams
    ├── 📁 videos/                   # Video resources
    └── 📁 downloads/                # Downloadable resources
```

---

## Quick Start

### For Users
- **New to SPIRIT?** → Start with [Getting Started Guide](getting-started/project-overview.md)
- **Want to build one?** → Check [Assembly Guide](hardware/assembly-guide.md)
- **Using your device?** → See [User Guides](user-guides/)

### For Developers
- **Want to contribute?** → Read [Contributing Guide](development/contributing.md)
- **Hardware development?** → See [Hardware Documentation](hardware/)
- **Software development?** → Check [Software Documentation](software/)

### For Enthusiasts
- **Join the community** → [Discord Server](community/discord.md)
- **Follow development** → [Project Roadmap](development/roadmap.md)
- **Stay updated** → [V Electronics YouTube](https://www.youtube.com/@V_Electronics)

---

## Core Specifications

- **Processor:** Broadcom BCM2712 (64-bit, quad-core, up to 2.4GHz)
- **RAM:** 2GB–16GB LPDDR4 options
- **Storage:** 16GB–64GB eMMC, expandable  
- **Display:** 5.5" TFT, 720×1280 resolution
- **Connectivity:** Wi-Fi, Bluetooth 5, GSM, GPS/GNSS
- **Privacy Switches:** Mic, GPS/GSM, Camera, Battery
- **OS:** Pure AOSP 16 (Android Open Source Project)
- **Platform:** Raspberry Pi Compute Module 5

---

## Contributing to Documentation

We welcome contributions to improve this documentation! 

- **Found an error?** → Open an issue or submit a PR
- **Missing information?** → Create an issue describing what's needed
- **Want to write docs?** → Check our [Contributing Guide](development/contributing.md)

Please ensure all documentation:
- Is written in clear, accessible English
- Follows our documentation standards
- Includes relevant images/diagrams where helpful
- Is kept up-to-date with project changes

---

## License

All SPIRIT documentation is released under open licenses compatible with the main project. See individual files for specific license information.

---

## Contact

- **Discord:** [V Electronics Discord Server](https://discord.gg/zBG4KdHJWx)
- **Email:** jwaga76@gmail.com
- **YouTube:** [V Electronics Channel](https://www.youtube.com/@V_Electronics)
- **GitHub Issues:** Use the issues section for documentation requests

---

<p align="center">
  <strong>SPIRIT: Taking back control of our digital lives</strong>
</p>
