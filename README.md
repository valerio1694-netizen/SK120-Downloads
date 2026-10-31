# SK120 Downloads

Öffentliche Installationsdateien für SK120 Control Android und ESP32-C3.

## Version 0.2.0

- [Android APK](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.2.0/SK120-Control-v0.2.apk)
- [C3 Factory-BIN für USB](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.2.0/SK120-OTA-C3-factory.bin)
- [C3 OTA Firmware-BIN](https://github.com/valerio1694-netizen/SK120-Downloads/releases/download/v0.2.0/SK120-OTA-C3-firmware.bin)

## Einrichtung

1. Factory-BIN per USB auf ESP32-C3 ab Offset 0x0 flashen (nicht per OTA).
2. SSD1306 OLED 128x64 an GPIO6 SDA / GPIO7 SCL und 3,3 V. OLED zeigt WLAN-Passwort und Portal-QR.
3. Handy mit SK120-OTA-XXXX WLAN verbinden, Android APK installieren.
4. App startet mit Live-Daten unter http://10.0.0.1. Für Sollwerte und Ausgangsschaltung WLAN-Passwort in der App eingeben.
5. SK120 TX -> C3 GPIO4 RX; SK120 RX <- C3 GPIO5 TX; GND gemeinsam. Vorher TTL-Pegel prüfen, keine RS232-Pegel.
6. HUSB238 und MPU6050 liegen am I2C-Bus GPIO6 und GPIO7.

Web-OTA: Am ESP-Portal http://10.0.0.1 Ausgang ausschalten, OTA-BIN auswählen, mit admin und WLAN-Passwort anmelden.

## Funktionsstand

Live: U, I, P, Uin, mAh, mWh, Laufzeit, Temperatur, CV/CC, Ausgangsstatus, HUSB238 PD-Vertrag, MPU6050 xyz.
Schalten: Spannung/Strom (vorläufig maximal 20V / 5A), Ausgang EIN/AUS. Schutzwerte nur lesend.

BEACHTEN: Builds sind kompiliert, aber noch nicht an echter Hardware geprüft. Modbus Adresse 1, Baudrate 115200.
Nicht an unbeaufsichtigten Lasten verwenden. Quellcode bleibt in privaten Repositories.