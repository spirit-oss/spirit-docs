# SPIRIT Hardware Specifications

## Overview

This document provides the complete technical specifications for the SPIRIT smartphone hardware platform. SPIRIT is built around the Raspberry Pi Compute Module 5 with a custom carrier board that integrates all smartphone components.

## Core Platform

### System-on-Chip (SoC)
- **Model:** Broadcom BCM2712
- **Architecture:** ARM Cortex-A76 quad-core (4x 2.4GHz)
- **Process Node:** 16nm FinFET
- **Instruction Set:** ARMv8-A 64-bit (aarch64)
- **GPU:** VideoCore VII (support for OpenGL ES 3.1, Vulkan 1.2)
- **Video Decoding:** H.264, H.265 (HEVC), VP9
- **Video Encoding:** H.264, H.265 (HEVC)

### Compute Module
- **Platform:** Raspberry Pi Compute Module 5 (CM5)
- **Form Factor:** DDR2 SODIMM-style connector (200-pin)
- **Available Variants:**
  - CM5 Lite (2GB RAM, no eMMC) - requires microSD
  - CM5 (4GB RAM, 16GB eMMC)
  - CM5 (4GB RAM, 32GB eMMC)  
  - CM5 (8GB RAM, 64GB eMMC)

### Memory
- **System RAM:** 2GB, 4GB, or 8GB LPDDR4X-4267
- **Internal Storage:** 16GB, 32GB, or 64GB eMMC 5.1
- **Expandable Storage:** microSD card slot (up to 1TB theoretical)
- **Memory Bandwidth:** ~17GB/s (LPDDR4X-4267)

### Storage Performance
- **eMMC Sequential Read:** ~300MB/s
- **eMMC Sequential Write:** ~100-150MB/s (varies by capacity)
- **eMMC Random Read:** ~30MB/s (4K)
- **eMMC Random Write:** ~10MB/s (4K)

## Display System

### LCD Panel
- **Size:** 5.5 inches diagonal
- **Resolution:** 720×1280 pixels (HD+, 16:9 aspect ratio)
- **Pixel Density:** ~267 PPI
- **Technology:** TFT LCD
- **Colors:** 16.7M colors (24-bit)
- **Brightness:** 400 nits typical
- **Viewing Angles:** 70° horizontal, 70° vertical
- **Response Time:** 25ms typical
- **Backlight:** White LED backlight

### Touch Controller
- **Technology:** Projected Capacitive (PCAP)
- **Touch Points:** Up to 10 simultaneous touches
- **Touch Accuracy:** ±1mm
- **Touch Response Time:** <20ms
- **Interface:** I2C communication
- **Power Consumption:** <10mA active, <1μA standby

### Display Interface
- **Connection:** MIPI DSI (Display Serial Interface)
- **Lanes:** 2-lane MIPI DSI
- **Data Rate:** Up to 1Gbps per lane
- **Color Format:** RGB888 (24-bit true color)

## Audio System

### Audio Codec
- **Model:** Texas Instruments TLV320AIC3204
- **Resolution:** 24-bit, 192kHz sampling rate
- **SNR:** 100dB (ADC), 108dB (DAC)
- **THD+N:** -85dB (1kHz, -1dBFS)
- **Power Supply:** 1.8V digital, 3.3V analog
- **Interface:** I2C control, I2S audio data

### Speakers
- **Configuration:** Dual speaker setup (stereo)
- **Model:** CMR-15062S-67 (CUI Devices)
- **Impedance:** 4Ω ±15%
- **Power Rating:** 1W continuous, 2W peak
- **Frequency Response:** 500Hz - 20kHz
- **Dimensions:** 15×6.2×4.5mm each

### Microphone
- **Type:** Digital MEMS microphone
- **Model:** Knowles SPH0645LM4H-B
- **Interface:** I2S digital output
- **SNR:** 65dB (A-weighted)
- **Sensitivity:** -26dBFS ±1dB
- **Frequency Range:** 50Hz - 15kHz
- **Power Supply:** 1.6V - 3.6V

### Headphone Jack
- **Connector:** 3.5mm TRS/TRRS
- **Output Power:** 30mW into 16Ω
- **Frequency Response:** 20Hz - 20kHz ±0.5dB
- **SNR:** 100dB
- **Supports:** Stereo audio output, mono microphone input

## Cameras

### Rear Camera
- **Sensor:** Sony IMX682 (via Arducam module)
- **Resolution:** 64MP (9248×6936)
- **Pixel Size:** 0.8μm
- **Optical Format:** 1/1.73"
- **Interface:** MIPI CSI-2 (4-lane)
- **Focus:** Fixed focus or autofocus (module dependent)
- **Video Recording:** Up to 4K@30fps, 1080p@60fps

### Front Camera (Optional)
- **Sensor:** Variable (depending on module selected)
- **Resolution:** 5MP - 16MP options available
- **Interface:** MIPI CSI-2 (2-lane)
- **Video Recording:** Up to 1080p@30fps

### Camera Interface
- **CSI Ports:** 2x MIPI CSI-2 ports on CM5
- **Lane Configuration:** Port 0: 4-lane, Port 1: 2-lane
- **Data Rate:** Up to 1.5Gbps per lane
- **Supported Formats:** RAW8, RAW10, RAW12, YUV422, RGB565, RGB888

## Connectivity

### Cellular Module
- **Model:** Quectel EC25VFA-512-STD
- **Technology:** 4G LTE Category 4
- **Form Factor:** LCC (Land Grid Array)
- **Dimensions:** 42×42×2.4mm
- **Bands:** Multiple global frequency bands
  - LTE-FDD: B1/B3/B5/B7/B8/B20
  - LTE-TDD: B38/B40/B41
  - WCDMA: B1/B5/B8
  - GSM: B3/B8
- **Data Rates:** 150Mbps down, 50Mbps up (LTE Cat 4)
- **Voice:** VoLTE, VoWiFi support
- **SMS:** Text messaging support
- **Interface:** USB 2.0 High Speed
- **Power Supply:** 3.3V - 4.3V
- **Power Consumption:** <2W typical, <3W peak

### Wi-Fi & Bluetooth
- **Built into CM5:** Broadcom BCM43455 combo chip
- **Wi-Fi Standards:** 802.11a/b/g/n/ac (Wi-Fi 5)
- **Frequency Bands:** 2.4GHz and 5GHz dual-band
- **Data Rates:** Up to 433Mbps (802.11ac)
- **Antenna:** PCB trace antenna + external antenna connector
- **Bluetooth Version:** 5.0 with BLE (Bluetooth Low Energy)
- **Bluetooth Range:** Up to 10 meters (Class 2)

### GPS/GNSS
- **Integrated in Cellular Module:** GNSS receiver
- **Constellations:** GPS, GLONASS, BeiDou, Galileo
- **Accuracy:** <2.5m CEP (Circular Error Probable)
- **Cold Start:** <32 seconds
- **Hot Start:** <1 second
- **Sensitivity:** -165dBm (tracking)

### USB Connectivity
- **Connector:** USB-C (USB4056-03-A)
- **Standards:** USB 3.2 Gen 1 (SuperSpeed, 5Gbps)
- **Features:**
  - Data transfer
  - Power delivery (charging)
  - DisplayPort Alternate Mode (DP Alt Mode)
  - Audio Adapter Accessory Mode
- **Power Delivery:** USB PD 3.0, up to 20V/3A (60W)

## Power Management

### Battery System
- **Type:** Lithium Polymer (Li-Po)
- **Voltage:** 3.7V nominal (3.0V - 4.2V range)
- **Capacity Options:**
  - Standard: 2000mAh (LP504783JU)
  - Extended: 3500mAh (LP685077JU)
- **Connector:** JST-PH 2.0mm pitch
- **Protection:** Built-in protection circuit
- **Cycle Life:** >500 cycles to 80% capacity

### Charging System
- **Input:** USB-C Power Delivery
- **Charging IC:** TI BQ24161YFFR or similar
- **Charging Current:** Up to 2A (adjustable)
- **Charging Voltage:** 4.2V ±1%
- **Charging Time:** 
  - 2000mAh battery: ~1.5 hours (2A)
  - 3500mAh battery: ~2.5 hours (2A)
- **Safety Features:** Over-current, over-voltage, thermal protection

### Power Rails
- **3.3V:** Main system power (1.5A capacity)
- **1.8V:** Low-power digital (0.5A capacity) 
- **1.2V:** Core voltage for CPU (3A capacity)
- **5V:** USB and high-power peripherals (1A capacity)
- **Battery Direct:** For charging circuit and backup

### Power Consumption
- **Idle (screen off):** 15-25mA
- **Light usage:** 150-300mA
- **Heavy usage:** 500-800mA
- **Peak (cellular transmission):** 1.2A
- **Sleep mode:** <1mA

## Physical Privacy Switches

### Microphone Kill Switch
- **Type:** Hardware power disconnect
- **Location:** Side-mounted toggle switch
- **Function:** Physically cuts power to microphone
- **Indicator:** LED status indicator
- **Switch Rating:** 50V DC, 0.5A

### Camera Kill Switch
- **Type:** Hardware power disconnect
- **Location:** Side-mounted toggle switch  
- **Function:** Physically cuts power to both cameras
- **Indicator:** LED status indicator
- **Scope:** Front and rear cameras

### GPS/Cellular Kill Switch
- **Type:** RF section isolation
- **Location:** Side-mounted toggle switch
- **Function:** Disconnects antenna connections and power
- **Indicator:** LED status indicator
- **Scope:** Cellular modem and GPS receiver

### Battery Kill Switch
- **Type:** Master power disconnect
- **Location:** Accessible internal switch
- **Function:** Completely disconnects battery
- **Use Case:** Ultimate privacy/security mode
- **Note:** Requires device disassembly to access

## Additional Components

### Fingerprint Scanner
- **Model:** Goodix or similar (SEN-17151)
- **Technology:** Capacitive fingerprint sensing
- **Resolution:** 508 DPI
- **Interface:** SPI communication
- **Recognition Time:** <0.5 seconds
- **Storage:** Up to 10 fingerprint templates
- **Power:** 3.3V, <10mA active

### Vibration Motor
- **Type:** Linear resonant actuator (LRA)
- **Model:** TDK PowerHap HD-EMB1205-3-SC-R
- **Resonant Frequency:** 175Hz ±25Hz
- **Voltage:** 3V typical
- **Current:** 85mA typical
- **Tactile Response:** Crisp, precise vibration

### Status LEDs
- **Power/Charging:** RGB LED indicator
- **Privacy Switches:** Individual LED for each switch
- **Notification:** User-configurable LED
- **Type:** High-efficiency SMD LEDs
- **Control:** PWM dimming support

### External Connectors
- **SIM Card:** Nano-SIM tray
- **microSD:** Push-push socket
- **Expansion:** Test points for unused CM5 GPIO
- **Debug:** UART header for development

## PCB Specifications

### Main Board
- **Size:** 80mm × 150mm
- **Layers:** 4-layer PCB design
- **Thickness:** 1.6mm (±0.1mm)
- **Materials:** FR-4 with HASL finish
- **Copper Weight:** 1oz (35μm) outer layers, 0.5oz (17.5μm) inner
- **Via Size:** 0.2mm minimum (typical 0.25mm)
- **Trace Width:** 0.1mm minimum (typical 0.15mm+)

### Manufacturing
- **Assembly:** Surface-mount technology (SMT)
- **Component Pitch:** Down to 0.4mm BGA
- **Testing:** In-circuit test (ICT) and functional test
- **Quality:** IPC-A-610 Class 2 standard
- **RoHS Compliance:** Lead-free manufacturing

## Environmental Specifications

### Operating Conditions
- **Temperature:** 0°C to 40°C
- **Humidity:** 10% to 85% RH (non-condensing)
- **Altitude:** Up to 3000m
- **Shock:** 15G, 11ms half-sine wave
- **Vibration:** 1.5G, 10-500Hz

### Storage Conditions  
- **Temperature:** -20°C to 60°C
- **Humidity:** 5% to 95% RH (non-condensing)
- **Duration:** Up to 12 months

### Certifications (Planned)
- **FCC:** Part 15 (unlicensed radio), Part 22/24 (cellular)
- **CE:** European Conformity marking
- **IC:** Industry Canada certification
- **RoHS:** Restriction of Hazardous Substances
- **WEEE:** Waste Electrical and Electronic Equipment

## Mechanical Design

### Dimensions
- **Length:** 160mm (approximate)
- **Width:** 85mm (approximate)  
- **Thickness:** 12mm (approximate)
- **Weight:** 180g (approximate, with 2000mAh battery)

### Materials
- **Case:** 3D printed or injection molded plastic
- **Screen:** Tempered glass (optional)
- **Buttons:** Tactile switches with plastic actuators
- **Fasteners:** Phillips head screws for serviceability

### Repairability Features
- **Standard Screws:** No proprietary fasteners
- **Modular Design:** Components can be replaced individually
- **Clear Labeling:** All connectors and components marked
- **Service Manual:** Complete repair documentation provided

---

## Revision History

- **v1.0** (Current): Initial hardware specification
- **v1.1** (Planned): Updates based on prototype testing
- **v2.0** (Future): Next generation improvements

---

*This specification is living document and will be updated as the hardware design evolves. For questions or clarifications, please [open an issue](https://github.com/your-org/spirit-docs/issues) or join our [Discord community](https://discord.gg/zBG4KdHJWx).*
