---
title: Analyse iOS devices
comments: false
---

### Analyse iOS devices
---
#### 1.1 Preparing folders
To analyse an iOS device, create a folder structure according to the one listed below. It can be done through the File Explorer found under **Applications** -> **Accessories** -> **Files** or by opening a terminal and typing `mkdir -p ios/backup ios/backup-decrypted ios/result`.

To open a terminal, press the Windows or Super button on the keyboard and search for terminal or select it from **Applications** -> **Utilities** -> **Terminal**

```
ios/
├── backup
├── backup-decrypted
└── result
```

#### 1.2 Create backup
Now connect your iOS device with a compatible cable and make sure it is unlocked. A prompt on the iOS device will show asking whether to trust this computer. Press **Trust**.

In the terminal type `idevicebackup2 -i encryption on`. You will be asked to enter a new backup password. Enter a password of your selection and make sure to remember it. If the password has previously been set, make sure you have the password ready. If the password is set but you don't know it, you may try to reset it by following the following steps described in the [MVT documentation](https://docs.mvt.re/en/latest/ios/backup/libimobiledevice/).

To create a backup, enter the following command in the terminal:

`idevicebackup2 backup --full ios/backup`

#### 1.3 Decrypt backup
To decrypt the backup, type the following command and replace <password> with the decryption password for you device backup. The `<long string of numbers>` will vary. You may press **Tab** to autocomplete after typing the first characters of the string.
  
`mvt-ios decrypt-backup -p <password> -d ios/backup-decrypted ios-analysis/backup/<long string of numbers>`

#### Perform analysis
 To check the backup, run the following command
  
 `mvt-ios check-backup --output ios/results ios/backup-decrypted`

The analysis will now run and analyse the data with the indicators of compromised provided by [Mobile V\
erification Toolkit](https://github.com/mvt-project/mvt).

---

#### Update indicators of compromise
To update the indicators of compromise, make sure the laptop is online through either WiFi or cabled connection. Once connected, a window with the title **Tor Connection** will appear. Toggle **Connect to Tor automatically** and press **Connect to Tor**. Once the connection is established, open a terminal and type `torify mvt-android download-iocs`and `torify mvt-ios download-iocs`.

Note that the indicators of compromise are reset for every reboot and will need updating again. We try to release a new image when new indicators are published to support offline complete offline analysis.

---

#### ⚠️ **IMPORTANT** ⚠️ ####
Not finding any indications of compromise does **NOT** mean your device is not infected. It just means that the public indicators of compromise was not matched with data extracted from your phone. The indicators are derived from forensic work and they are publicly available. This means the the spyware authors have access to them as well, and can rule them out of future spyware and infections.  
