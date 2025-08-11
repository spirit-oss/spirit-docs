# Building AOSP for SPIRIT

This guide walks you through building the AOSP (Android Open Source Project) operating system for the SPIRIT smartphone. The SPIRIT OS is based on pure AOSP 16 with optimizations for the Raspberry Pi 5 platform.

## Prerequisites

### System Requirements

**Minimum Requirements:**
- 64-bit Linux distribution (Ubuntu 22.04 LTS recommended)
- 400GB+ free disk space (SSD strongly recommended)
- 16GB RAM minimum (32GB+ recommended)
- Fast internet connection (initial sync is ~150GB)

**Recommended Development Machine:**
- Ubuntu 22.04 LTS or similar
- 1TB+ NVMe SSD
- 32GB+ RAM
- 8+ CPU cores
- Gigabit internet connection

### Required Software Packages

Install the required packages on Ubuntu/Debian:

```bash
sudo apt update
sudo apt install -y \
  git-core gnupg flex bison build-essential zip curl \
  zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
  libncurses5 lib32ncurses5-dev x11proto-core-dev \
  libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils \
  xsltproc unzip fontconfig python3 python3-pip \
  openjdk-11-jdk bc rsync repo
```

For other Linux distributions, consult the [AOSP system requirements](https://source.android.com/docs/setup/start).

### Configure Git

Set up your git identity (required for repo):

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

## Setting Up the Build Environment

### 1. Create Working Directory

```bash
# Create a dedicated directory for the SPIRIT build
mkdir -p ~/spirit-aosp
cd ~/spirit-aosp
```

### 2. Initialize the Repository

**Note:** Replace the manifest URL with the actual SPIRIT manifest repository when available.

```bash
# Initialize the repo with SPIRIT manifest
repo init -u https://github.com/V3lectronics/spirit-manifest.git -b android-16

# Alternative: Use AOSP upstream for now (until SPIRIT manifest is ready)
repo init -u https://android.googlesource.com/platform/manifest -b android-16.0.0_r1
```

### 3. Sync the Source Code

This step downloads all AOSP source code (~150GB). This will take several hours:

```bash
# Sync all repositories (use -j flag to parallelize)
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

# If sync fails due to network issues, simply re-run the command
```

**Tip:** The sync can be interrupted and resumed. If you experience network issues, just run the sync command again.

## Building the SPIRIT OS

### 1. Set Up Build Environment

```bash
# Navigate to the AOSP root directory
cd ~/spirit-aosp

# Initialize the build environment
source build/envsetup.sh
```

### 2. Choose Target Device

```bash
# For SPIRIT device (when available)
lunch aosp_spirit-userdebug

# Alternative: Use Raspberry Pi generic target for now
lunch aosp_rpi5-userdebug
```

**Build Types Explained:**
- **user**: Production build, no root access, optimized
- **userdebug**: Like user but with root access and debugging features
- **eng**: Development build with additional debugging tools

### 3. Configure Build (Optional)

You can customize the build with additional options:

```bash
# Set number of parallel jobs (adjust based on your CPU cores)
export USE_CCACHE=1
export CCACHE_EXEC=/usr/bin/ccache

# Optional: Set Java heap size for better performance
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4g"
```

### 4. Start the Build

```bash
# Start the full build (this takes 2-6 hours depending on hardware)
m

# Alternative: Build specific targets
m bootimage systemimage vendorimage
```

**Build Output Location:**
After successful compilation, build artifacts will be in:
```
out/target/product/spirit/
├── boot.img          # Boot image
├── system.img        # System partition
├── vendor.img        # Vendor partition
├── userdata.img      # User data partition
└── recovery.img      # Recovery image
```

## SPIRIT-Specific Modifications

### Device Configuration

The SPIRIT device configuration includes:

```bash
# Device tree location (when available)
device/spirit/spirit/

# Key configuration files:
├── AndroidProducts.mk    # Product definitions
├── BoardConfig.mk        # Hardware configuration
├── device.mk            # Device-specific settings
├── manifest.xml         # Hardware abstraction layer (HAL) manifest
└── sepolicy/            # Security policy files
```

### Hardware Abstraction Layers (HALs)

SPIRIT includes custom HALs for:

- **Audio HAL**: TI TLV320AIC3204 codec support
- **Camera HAL**: Arducam 64MP module integration
- **Cellular HAL**: Quectel EC25VFA modem support
- **Privacy Switch HAL**: Hardware switch monitoring
- **Sensor HAL**: Fingerprint and other sensors

### Kernel Configuration

The SPIRIT kernel is based on the Raspberry Pi kernel with additional patches:

```bash
# Kernel source location
kernel/rpi/

# SPIRIT-specific kernel configs
arch/arm64/configs/spirit_defconfig
```

## Flashing the Build

### 1. Prepare the Device

1. Ensure your SPIRIT device is in fastboot mode
2. Connect via USB-C cable to your development machine
3. Verify connection: `fastboot devices`

### 2. Flash Images

```bash
cd ~/spirit-aosp/out/target/product/spirit/

# Flash individual partitions
fastboot flash boot boot.img
fastboot flash system system.img
fastboot flash vendor vendor.img
fastboot flash userdata userdata.img

# Alternative: Flash all partitions at once
fastboot flashall

# Reboot the device
fastboot reboot
```

### 3. First Boot

The first boot will take 5-10 minutes as the system:
- Optimizes apps for the hardware
- Sets up the runtime environment
- Configures privacy switches
- Initializes hardware components

## Incremental Builds

After making changes to the source code:

```bash
# For small changes, incremental builds are much faster
source build/envsetup.sh
lunch aosp_spirit-userdebug

# Build only changed components
m

# Flash only the affected partitions
fastboot flash system system.img
fastboot reboot
```

## Debugging Build Issues

### Common Build Problems

**Out of Memory:**
```bash
# Reduce parallel jobs
m -j4
```

**Missing Dependencies:**
```bash
# Clean and rebuild
m clean
m
```

**Repo Sync Issues:**
```bash
# Force sync with retry
repo sync --force-sync --force-broken
```

### Build Logs

Build logs are located in:
```bash
# Main build log
~/spirit-aosp/out/verbose.log.gz

# Individual module logs
~/spirit-aosp/out/target/product/spirit/logs/
```

### Getting Help

If you encounter build issues:

1. **Check the logs** for specific error messages
2. **Search existing issues** on the SPIRIT GitHub repositories
3. **Ask in Discord** with relevant log snippets
4. **Open a GitHub issue** with full error details

## Development Workflow

### Making Changes

1. **Create a topic branch:**
   ```bash
   repo start my-feature-branch .
   ```

2. **Make your changes** in the relevant repositories

3. **Test the changes:**
   ```bash
   m && fastboot flashall
   ```

4. **Commit and upload for review:**
   ```bash
   git add .
   git commit -m "Add feature XYZ"
   repo upload
   ```

### Testing

Before submitting changes:

1. **Build successfully** without warnings
2. **Boot test** on actual hardware
3. **Function test** the affected components
4. **Privacy switch test** if hardware changes were made

## Performance Optimization

### Build Performance

```bash
# Use ccache for faster rebuilds
export USE_CCACHE=1
export CCACHE_DIR=~/.ccache
ccache -M 50G  # Set cache size

# Use RAM for temporary files (if you have plenty of RAM)
export TMP=/tmp
export TMPDIR=/tmp
```

### Advanced Build Options

```bash
# Enable link-time optimization (slower build, better runtime performance)
export GLOBAL_THINLTO=true

# Use Gold linker for faster linking
export USE_GOLD_LINKER=true

# Skip building unused modules
export PRODUCT_MINIMIZE_JAVA_DEBUG_INFO=true
```

## Customizing Your Build

### Adding Custom Apps

To include custom applications in the build:

1. Add APK to `vendor/spirit/apps/`
2. Create Android.mk file
3. Add to PRODUCT_PACKAGES in device.mk

### Modifying Privacy Features

Privacy switch behavior is controlled by:
```bash
# HAL implementation
hardware/interfaces/spirit/privacy/

# System service
frameworks/base/services/core/java/com/android/server/privacy/

# Settings UI
packages/apps/Settings/src/com/android/settings/privacy/
```

## Continuous Integration

For automated builds, you can set up a CI pipeline:

```bash
#!/bin/bash
# Example CI build script

# Set up environment
source build/envsetup.sh
lunch aosp_spirit-userdebug

# Clean build for CI
m clean
m -j$(nproc)

# Generate build artifacts
cp out/target/product/spirit/*.img ./artifacts/
```

## Troubleshooting

### Build Hangs

If the build appears to hang:

1. Check system resources (RAM, disk space)
2. Reduce parallel jobs: `m -j4`
3. Check for hardware issues (thermal throttling)

### Bootloop After Flash

If the device bootloops after flashing:

1. Check kernel logs: `dmesg`
2. Flash known-good images
3. Verify hardware connections
4. Check for selinux denials: `logcat | grep avc`

---

## Next Steps

After successfully building AOSP for SPIRIT:

1. **Learn about customization** in [Customization Guide](customization.md)
2. **Set up debugging** with [Debugging Guide](debugging.md)
3. **Contribute to development** following [Contributing Guide](../development/contributing.md)

---

*Need help with building? Join our [Discord community](https://discord.gg/zBG4KdHJWx) or [open an issue](https://github.com/V3lectronics/spirit-os/issues).*
