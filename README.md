# SK120 Downloads

Öffentliche Installationsdateien für SK120 Control Android und ESP32-C3.

## Version 0.6.0 – SK120 LAB (neue Funktionen noch hardwareseitig zu prüfen)

- [Android-App v0.6](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.6.0/SK120-LAB-v0.6.apk)
- [ESP32-C3 OTA-Firmware v0.6](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.6.0/SK120-LAB-v0.6-OTA.bin)
- [ESP32-C3 Factory-BIN v0.6, nur für USB/esptool](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.6.0/SK120-LAB-v0.6-factory.bin)

Neu: BLE-only, OLED-QR+PIN ohne Verbindung, sechs OLED-Modi mit Schonmodus, MPU6050 mit 3D-Lage/Wasserwaage/G-Meter/Stoßmonitor, Offline-Hilfe sowie BLE-OTA/Android-USB-Flasher.

**Wichtig:** App und Firmware kompilieren. Die neuen Updateverfahren, das komplette OLED-Verhalten und die Modbus-Hardwarekommunikation sind noch nicht am realen SK120 validiert. Die bisher funktionierende v0.4 bleibt für die Wiederherstellung verfügbar.

## Version 0.4.0 – BLE Test

- [Android BLE-Test APK](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.4.0/SK120-BLE-Test-v0.4.apk)
- [C3 Factory-BIN für USB](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.4.0/SK120-OTA-C3-factory.bin)
- [C3 OTA Firmware-BIN](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.4.0/SK120-OTA-C3-firmware.bin)

**Neu in v0.4:** Bluetooth LE mit PIN-Kopplung am OLED. Die BLE-Test-App ist als separates Android-Paket installierbar; die bisherige WLAN-App bleibt bestehen. BLE-Kopplung und Live-Telemetrie mit einem Handy wurden geprüft; Steuerbefehle an SK120 sowie ein zweites Gerät sind noch nicht geprüft.\n\n**Seit v0.3:** Die C3-Firmware beantwortet Captive-Portal-DNS-Anfragen und leitet Android-/Windows-/Apple-Netzwerktests auf das lokale Portal um. Die Android-App öffnet ihre HTTP-Verbindungen gezielt über das WLAN-Interface mit einer Adresse 10.0.0.x, auch wenn mobile Daten die Standard-Internetroute sind. Das automatische Öffnen des Portals unter HyperOS ist noch nicht nachgewiesen.

## Einrichtung

1. Factory-BIN per USB auf ESP32-C3 ab Offset 0x0 flashen (nicht per OTA).
2. SSD1306 OLED 128x64 an GPIO6 SDA / GPIO7 SCL und 3,3 V. OLED zeigt WLAN-Passwort und Portal-QR.
3. Android-BLE-Test-App über den OLED-QR-Code oder den Download-Link installieren; für BLE ist keine WLAN-Verbindung zum ESP erforderlich.
4. App öffnen, SK120 über Bluetooth suchen und mit der sechsstelligen OLED-PIN koppeln. Das WLAN-Webportal unter http://10.0.0.1 bleibt für OTA und Diagnose erreichbar.
5. SK120 TX -> C3 GPIO4 RX; SK120 RX <- C3 GPIO5 TX; GND gemeinsam. Vorher TTL-Pegel prüfen, keine RS232-Pegel.
6. HUSB238 und MPU6050 liegen am I2C-Bus GPIO6 und GPIO7.

Web-OTA: Am ESP-Portal http://10.0.0.1 Ausgang ausschalten, OTA-BIN auswählen, mit admin und WLAN-Passwort anmelden.

## Funktionsstand

Live: U, I, P, Uin, mAh, mWh, Laufzeit, Temperatur, CV/CC, Ausgangsstatus, HUSB238 PD-Vertrag, MPU6050 xyz.
Schalten: Spannung/Strom (vorläufig maximal 20V / 5A), Ausgang EIN/AUS. Schutzwerte nur lesend.

BEACHTEN: BLE-Verbindung und Telemetrie wurden getestet, SK120-Modbus/Steuerung aber noch nicht an echter Hardware geprüft. Modbus Adresse 1, Baudrate 115200.
Nicht an unbeaufsichtigten Lasten verwenden. Quellcode bleibt in privaten Repositories.