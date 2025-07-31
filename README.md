
# ESP32 OTA Firmware Update via GitHub

This project demonstrates **Over-The-Air (OTA) firmware updates** for the **ESP32**, using a JSON versioning system hosted on **GitHub**. The ESP32 checks the latest firmware version against its current version and performs an OTA update if a newer version is available.

## 🔧 Features
- Automatic OTA firmware updates
- Version check using `version.json` from GitHub
- Secure HTTPS download using `WiFiClientSecure`
- JSON parsing using ArduinoJson
- Manual version control via `#define CURRENT_VERSION`

## 📁 Repository Structure
esp32-ota-firmware/
├── firmware.bin            # ✅ Compiled binary of your ESP32 firmware
├── version.json            # ✅ JSON file that includes the latest version and .bin URL
└── main.ino                # ✅ Arduino code that performs OTA update

``
## 📄 `version.json` Example
json
{
  "version": "1.0.3",
  "bin_url": "https://github.com/gautamk10/esp32-ota-firmware/raw/main/firmware.bin"
}

 ##🔌How It Works
1. ESP32 boots and connects to WiFi.
2. It fetches the `version.json` file hosted on GitHub.
3. Compares the current firmware version (`CURRENT_VERSION`) with the latest version from the JSON.
4. If a newer version is found, it downloads the `.bin` file over HTTPS.
5. Performs in-place firmware upgrade and restarts.

## 📝 How to Use

1. **Update `CURRENT_VERSION`** in the code before compiling and uploading to your ESP32.
2. **Compile and export** the firmware `.bin` from Arduino IDE or PlatformIO.
3. **Update `version.json`** with the new version number and `.bin` URL.
4. **Push changes** to your GitHub repo.
5. ESP32 will detect the update and perform OTA on next boot.

## 🔐 Note on Security

The `WiFiClientSecure` uses `.setInsecure()` for simplicity. For production use:

* Use **SSL certificate validation**
* Consider adding **update signature verification**

## 📦 Libraries Used

* [WiFi.h](https://www.arduino.cc/en/Reference/WiFi)
* [HTTPClient.h](https://www.arduino.cc/en/Reference/HTTPClient)
* [ArduinoJson](https://arduinojson.org/)
* [Update.h](https://www.arduino.cc/en/Reference/Update)
* [WiFiClientSecure.h](https://github.com/espressif/arduino-esp32)

## 🧪 Example Serial Output
Connecting to WiFi...
Connected!
Current Version: 1.0.2
Latest Version : 1.0.3
New version detected. Starting OTA...
OTA successful! Rebooting...

## 📸 Demo (Optional)

<img width="250" height="250" alt="Screenshot 2025-07-31 133851" src="https://github.com/user-attachments/assets/6c33149a-8556-4d73-bd26-93478c5c4ff5" />
<img width="250" height="250" alt="Screenshot 2025-07-31 133325" src="https://github.com/user-attachments/assets/52c8fed6-233c-43dc-a050-0a92a508e413" />

 ✍️ Author
**Gautam Kumar
Embedded Software Developer | [GitHub @gautamk10](https://github.com/gautamk10)

 📜 License
 
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

