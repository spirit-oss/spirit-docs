# SPIRIT Project Overview

## What is SPIRIT?

SPIRIT is an **open-source smartphone project** that aims to revolutionize mobile devices by prioritizing user control, privacy, and repairability. Unlike traditional smartphones that lock users out of their own devices, SPIRIT is designed from the ground up to be completely transparent and modifiable.

## Why SPIRIT Exists

### The Problem
Modern smartphones have several fundamental issues:
- **Proprietary software** that users can't inspect or modify
- **Hardware kill switches** that don't actually cut power to components
- **Difficult to repair** designs that force users to buy new devices
- **Vendor lock-in** that limits user choice
- **Privacy concerns** with no physical way to ensure components are truly off

### The SPIRIT Solution
SPIRIT addresses these problems by providing:
- **Complete transparency** - all hardware designs and software are open source
- **Physical privacy switches** - hardware switches that physically disconnect components
- **Repairability by design** - components can be replaced and upgraded
- **Community control** - development driven by users, not corporations
- **Educational value** - learn how smartphones actually work

## Key Features

### Hardware
- **Raspberry Pi Compute Module 5** as the core processor
- **Custom carrier board** that connects all components
- **Physical privacy switches** for mic, camera, GPS/cellular, and battery
- **Standard components** that are available from multiple suppliers
- **Modular design** allowing component upgrades and replacements

### Software
- **Pure AOSP** (Android Open Source Project) - no vendor modifications
- **Optimized for privacy** with hardware integration
- **Community-driven development** 
- **FOSS-first approach** preferring open source drivers and applications

### Documentation
- **Complete design files** including schematics, PCB layouts, and mechanical drawings
- **Build instructions** for both hardware assembly and software compilation
- **Educational materials** explaining how each component works
- **Community resources** for getting help and contributing

## Technical Specifications

### Core Platform
- **SoC:** Broadcom BCM2712 (ARM Cortex-A76 quad-core, up to 2.4GHz)
- **Architecture:** 64-bit ARM (aarch64)
- **RAM:** 2GB, 4GB, or 8GB LPDDR4X options (via CM5 variants)
- **Storage:** 16GB-64GB eMMC + microSD expansion

### Display & Input
- **Screen:** 5.5" TFT LCD, 720×1280 resolution (HD+)
- **Touchscreen:** Capacitive multi-touch
- **Physical buttons:** Power, volume, privacy switches

### Connectivity
- **Cellular:** 4G LTE (EC25VFA-512-STD module)
- **Wi-Fi:** 802.11ac dual-band (2.4GHz & 5GHz)
- **Bluetooth:** 5.0/5.1 with BLE
- **GPS/GNSS:** Multi-constellation positioning
- **USB:** USB-C 3.2 (data, charging, display output)

### Audio
- **Speakers:** Dual speakers for stereo playback
- **Microphone:** Digital MEMS microphone (SPH0645LM4H-B)
- **Headphone Jack:** 3.5mm analog output
- **Audio Codec:** TI TLV320AIC3204

### Cameras
- **Rear Camera:** Up to 64MP (Arducam module)
- **Front Camera:** Variable resolution options
- **Video:** 4K recording capability (hardware dependent)

### Power Management
- **Battery:** 3.7V Li-Po, 2000-3500mAh capacity options
- **Charging:** USB-C PD (Power Delivery)
- **Power Management:** Custom circuit with multiple voltage rails

### Privacy Features
- **Microphone Kill Switch:** Physical disconnect of microphone power
- **Camera Kill Switch:** Physical disconnect of camera modules
- **GPS/Cellular Kill Switch:** RF section isolation
- **Battery Kill Switch:** Complete device power disconnect

## Development Status

As of the current development phase:

| Component | Status | Notes |
|-----------|--------|-------|
| **Hardware Design** | 🟢 Complete | PCB design finalized, tested |
| **Mechanical Design** | 🟡 In Progress | Case and assembly design |
| **AOSP Boot** | 🟢 Working | System boots to Android UI |
| **Display & Touch** | 🟢 Working | Full functionality |
| **Wi-Fi & Bluetooth** | 🟢 Working | Stable connectivity |
| **Audio** | 🟢 Working | Speakers, mic, headphone jack |
| **USB-C** | 🟢 Working | Data transfer and charging |
| **Cellular (RIL)** | 🟡 In Progress | Basic signaling working |
| **Camera HAL** | 🟡 In Progress | Driver integration ongoing |
| **GPS/GNSS** | 🔴 Planned | Driver development needed |
| **Privacy Switches** | 🟢 Hardware Ready | Software integration complete |

🟢 = Working | 🟡 = In Progress | 🔴 = Not Started

## Who Is SPIRIT For?

### Primary Audiences
- **Privacy-conscious users** who want physical control over their device
- **Developers and tinkerers** who want to modify their smartphone
- **Education and research** institutions teaching mobile technology
- **Repair enthusiasts** who want to fix their own devices
- **Security professionals** who need verifiable hardware

### Technical Requirements
To get the most out of SPIRIT, users should be comfortable with:
- **Basic Linux command line** for software building
- **Electronics fundamentals** for hardware assembly (optional but helpful)
- **Android development** for software contributions (optional)

## Getting Started

### I Want to Learn More
- Continue reading the [FAQ](faq.md)
- Check out the [Quick Start Guide](quick-start.md)
- Join our [Discord community](../community/discord.md)

### I Want to Build One
- Review the [Hardware Specifications](../hardware/specifications.md)
- Follow the [Assembly Guide](../hardware/assembly-guide.md)
- Build the software using our [AOSP Build Guide](../software/building-aosp.md)

### I Want to Contribute
- Read our [Contributing Guidelines](../development/contributing.md)
- Set up your [Development Environment](../development/development-setup.md)
- Check the [Project Roadmap](../development/roadmap.md) for current priorities

### I Need Help
- Check our [Support Resources](../community/support.md)
- Ask questions in our [Discord server](https://discord.gg/zBG4KdHJWx)
- Report issues on GitHub

## Philosophy & Values

SPIRIT is built on these core principles:

### Transparency
Every aspect of SPIRIT is open and documented. There are no hidden components, proprietary drivers, or secret protocols. If it's in your device, you can understand how it works.

### User Control
You own your device and should have complete control over it. SPIRIT ensures that users, not corporations, decide what software runs and what data is shared.

### Privacy by Design
Privacy isn't an afterthought - it's built into the hardware. Physical switches provide absolute certainty that components are truly off.

### Community Driven
SPIRIT belongs to the community that builds and uses it. Decisions are made in the open with community input, not behind corporate boardroom doors.

### Repairability
Devices should last and be fixable. SPIRIT uses standard components, provides complete repair documentation, and supports user modifications.

### Education
Understanding technology empowers users. SPIRIT serves as a teaching platform for mobile technology, from basic electronics to advanced software development.

---

## Next Steps

Ready to dive deeper? Here are your next steps:

1. **New Users:** Read our [FAQ](faq.md) and [Quick Start Guide](quick-start.md)
2. **Builders:** Check the [Hardware](../hardware/) and [Software](../software/) documentation
3. **Developers:** Visit our [Development](../development/) section
4. **Community:** Join our [Discord](../community/discord.md) and get involved

**Welcome to the SPIRIT community!** 🎉

---

*Have questions about this overview? [Open an issue](https://github.com/your-org/spirit-docs/issues) or ask in our [Discord server](https://discord.gg/zBG4KdHJWx).*
