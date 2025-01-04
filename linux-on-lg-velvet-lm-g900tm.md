Changing the OS on your **LG Velvet LM-G900TM** from Android to a Linux-based OS is a complex process that involves unlocking the bootloader, installing a custom recovery, and flashing a Linux image. This guide will walk you through the entire process, highlighting the necessary precautions, tools, and steps involved. 

### **Important Considerations**

1. **Risk of Bricking**: Flashing a new OS on your device can lead to a bricked phone if something goes wrong.
2. **Warranty Voiding**: This process will void any warranty on your device.
3. **Data Loss**: This procedure will erase all data on your device. Be sure to back up everything you need.
4. **Hardware Compatibility**: Not all devices have full Linux support, so you might encounter issues with Wi-Fi, touchscreen, camera, or other sensors.
5. **Device-Specific Limitations**: While some Linux distributions like PostmarketOS and Ubuntu Touch are designed for mobile devices, they might not fully support every feature of your LG Velvet.

### **Step-by-Step Guide to Install Linux on the LG Velvet LM-G900TM**

---

#### **1. Unlock the Bootloader**

Before you can install a new OS, you'll need to unlock the bootloader of your device. This allows you to flash custom firmware and recoveries.

##### Steps to unlock the bootloader:
- **Enable Developer Options**:
  - Go to **Settings** → **About phone** → Tap **Build number** 7 times to enable Developer Options.
  
- **Enable OEM Unlocking**:
  - Go to **Settings** → **System** → **Developer options** → Enable **OEM Unlocking**.

- **Enable USB Debugging**:
  - In Developer Options, enable **USB Debugging**.

- **Install ADB and Fastboot on your PC**:
  - On Linux:
    ```bash
    sudo apt update
    sudo apt install adb fastboot
    ```
  - On Windows, you can use the [ADB tool](https://developer.android.com/studio).

- **Connect your phone to your computer** via USB and open a terminal or command prompt.

- **Check if ADB recognizes your phone**:
  ```bash
  adb devices
  ```
  - If your device is listed, proceed.

- **Reboot into bootloader**:
  ```bash
  adb reboot bootloader
  ```

- **Unlock the bootloader** (this will wipe your device!):
  ```bash
  fastboot oem unlock
  ```

  - Follow the on-screen instructions to confirm the unlock. This may take a few minutes.

- After the process, your device will reboot, and you may need to reset your phone.

---

#### **2. Install a Custom Recovery (TWRP)**

You’ll need a custom recovery like **TWRP** to install the Linux-based OS. 

##### Steps to install TWRP:
- **Download the TWRP image** for your device from [TWRP's official website](https://twrp.me) or search on XDA forums for a compatible version for the LG Velvet LM-G900TM.
  
- **Flash TWRP via fastboot**:
  ```bash
  fastboot flash recovery twrp.img
  ```

- **Reboot into TWRP recovery**:
  ```bash
  fastboot boot twrp.img
  ```

- Once in TWRP, you can proceed with flashing your Linux OS.

---

#### **3. Download a Linux Distro for ARM Architecture**

There are several Linux-based OS options available for mobile devices. The most popular ones are **PostmarketOS**, **Ubuntu Touch**, and **Sailfish OS**. For this guide, we'll focus on **PostmarketOS**.

##### PostmarketOS Installation:

- **PostmarketOS** is a lightweight, mobile-focused Linux distribution designed for use on smartphones. It supports ARM architecture, which is compatible with your device.

  - Visit the [PostmarketOS installation page](https://postmarketos.org) for a detailed guide on supported devices and installation instructions.
  - For the LG Velvet, you may need to check compatibility on the [PostmarketOS Wiki](https://wiki.postmarketos.org).

##### Download the PostmarketOS Image:
1. Go to [PostmarketOS's official site](https://postmarketos.org) and download the image for your device, if available.
2. If your device isn’t supported, you might need to either port it yourself (which can be quite technical) or wait until support is available.

---

#### **4. Flash the Linux OS onto Your Device**

- **Transfer the Linux image to your device**:
  - Use ADB to copy the PostmarketOS image to your device:
    ```bash
    adb push postmarketos.img /sdcard/
    ```

- **Reboot into TWRP** if you're not already there.

- **Wipe the device**:
  - In TWRP, go to **Wipe** → **Advanced Wipe**, and wipe **Dalvik/ART Cache**, **System**, **Data**, and **Cache** partitions. This is necessary to ensure no Android remnants remain.

- **Flash PostmarketOS**:
  - In TWRP, go to **Install** and select the **PostmarketOS image** you transferred earlier.
  - Confirm the flash, and the installation should proceed.

- After flashing, reboot the device.

---

#### **5. First Boot and Setup**

- Upon booting into the new OS, you may face some initial setup steps such as configuring Wi-Fi, setting up user preferences, and enabling additional features.

- **Check Hardware Compatibility**:
  - Not all features may work out of the box (e.g., camera, sensors, touch screen). You might need to manually install drivers or configurations.

---

### **Challenges You Might Face**

- **Hardware Support**: Not all features of the LG Velvet may be supported out-of-the-box in Linux. This could include things like camera drivers, GPS, fingerprint sensor, and more.
- **Performance Issues**: Linux on mobile is still under development, so performance may not be as smooth as Android.
- **No Easy Recovery**: If something goes wrong, you may have difficulty recovering the device without access to Android-based recovery tools.

---

### **Alternative Linux Distros for Mobile**

- **Ubuntu Touch**: A more user-friendly option, although it may have limited support for certain devices.
- **Sailfish OS**: Another Linux-based mobile OS with some Android compatibility.

### **Resources**

- **PostmarketOS Wiki**: [https://wiki.postmarketos.org](https://wiki.postmarketos.org)
- **Ubuntu Touch**: [https://ubuntu-touch.io](https://ubuntu-touch.io)
- **TWRP for LG Velvet**: Check XDA for specific images.
- **XDA Forum for LG Velvet**: [XDA LG Velvet](https://forum.xda-developers.com)

---

### **Final Words**

Changing the OS from Android to Linux on your LG Velvet is a challenging and experimental task that requires technical expertise. While it is possible, the hardware compatibility and overall stability of the Linux OS on mobile devices are still evolving. I highly recommend checking community forums like XDA for specific guides, issues, and updates related to the LG Velvet model.