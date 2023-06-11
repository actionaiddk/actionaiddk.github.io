---
title: Analyse Android devices
comments: false
---

### Analyse Android devices
---
#### 1.1 Preparing the Android device
To analyse an Android device, the **developer options** and **USB debugging** need to be enabled. On the device, head to the **Settings** -> **About phone** and press the build number several times. Once the developer options are enabled, enable USB Debugging from within **Settings** -> **System** -> **Developer options** and toggle **USB debugging**.

#### 1.2 Perform analysis
To analyse your device, connect it to the laptop with a compatible cable. A cable of good quality is advised. Make the phone is turned on and unlocked Press the Windows or Super button on the keyboard and search for terminal or select it from the menu in the upper left corner: **Applications** -> **Utilities** -> **Terminal**. Once the terminal is open, type `mvt-android check-adb` and hit enter.

A prompt will appear on the Android device asking whether to trust this PC. Toggle **Always allow from this computer** and press **Allow**.

Next, a prompt will show asking whether to allow a full backup. Press **Back up my data**.
The analysis will now run and analyse the data with the indicators of compromised provided by [Mobile Verification Toolkit](https://github.com/mvt-project/mvt).

#### 1.3 Error handling

You may run into an error stating **Device is busy, maybe run `adb kill-server` and try again**. Type `killall adb` and try again. If the problem persists. Try unplugging the phone and redoing the steps again. You may also try the command `adb kill-server`, however we found that `killall adb` works in the majority of cases.

---

#### Update indicators of compromise
To update the indicators of compromise, make sure the laptop is online through either WiFi or cabled connection. Once connected, a window with the title **Tor Connection** will appear. Toggle **Connect to Tor automatically** and press **Connect to Tor**. Once the connection is established, open a terminal and type `torify mvt-android download-iocs`and `torify mvt-ios download-iocs`.

Note that the indicators of compromise are reset for every reboot and will need updating again. We try to release a new image when new indicators are published to support offline complete offline analysis.

---

#### ⚠️ **IMPORTANT** ⚠️ ####
Not finding any indications of compromise does **NOT** mean your device is not infected. It just means that the public indicators of compromise was not matched with data extracted from your phone. The indicators are derived from forensic work and they are publicly available. This means the the spyware authors have access to them as well, and can rule them out of future spyware and infections.  
