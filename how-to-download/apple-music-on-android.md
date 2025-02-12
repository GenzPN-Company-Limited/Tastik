# Apple Music On Android

## Apple Music Download on Android

***

### **Preface**

This guide provides step-by-step instructions to download Apple Music on Android devices.

***

### **Installation**

#### **Step 1: Download Required APKs**

1. Download and install the following **2 APKs**:
   * **Decryption client**:\
     [Apple.Music\_4.9.3\_arm64v8a\_gadget.apk](https://github.com/itouakirai/apple-music-jshook-script/releases/download/wsa/Apple.Music_4.9.3_arm64v8a_gadget.apk)
   * **Download client**:\
     [ZeroTermux-0.118.1.41.apk](https://github.com/hanxinhao000/ZeroTermux/releases/download/release/ZeroTermux-0.118.1.41.apk)

***

#### **Step 2: Set Up the Clients**

1. Open the **Apple Music** app, log in with your Apple Music account (**Subscription required**).
2. Open the **ZeroTermux** app, grant the required permissions, and run the following commands:

```bash
pkg update && pkg upgrade && pkg install git golang gpac ffmpeg && git clone --depth 1 https://github.com/zhaarey/apple-music-downloader downloader
```
And enter when asked to install dependencies.
***

#### **Step 3: Configure Storage Paths**

1. In ZeroTermux, swipe left from the right edge to open the file manager.
2. Navigate to **home > apple-music-alac-atmos-downloader > config.yaml**, then choose to edit the file.
3. Update the storage paths (recommended for Android):

```yaml
alac-save-folder: /storage/emulated/0/Music/AM/AM-DL downloads
atmos-save-folder: /storage/emulated/0/Music/AM/AM-DL-Atmos downloads
```

***

### **Usage**

#### **Step 1: Prepare Apple Music App**

1. Launch the Apple Music app and ensure it runs in the background (e.g., disable battery optimization, allow background running, etc.).
2. For Android 14/15, enable **Stop Restricting Child Processes** in Developer Settings.

***

#### **Step 2: Navigate to the Download Folder**

1. Start ZeroTermux and navigate to the download project folder:

```bash
cd downloader
```

***

#### **Step 3: Start Downloading**

Use the following commands to start downloading:

**For Album/Playlist/Artist**

```bash
go run main.go <url>
```

**For Atmos Tracks**

```bash
go run main.go --atmos <url>
```

**For Select Track**

```bash
go run main.go --select <url>
```

**For Select Atmos Track**

```bash
go run main.go --select --atmos <url>
```

***

### **Notes**

* Ensure you have a stable internet connection during the download process.
* The downloaded files will be saved in the specified folders (`/storage/emulated/0/Music/AM/`).
* This guide assumes basic familiarity with Android and command-line tools.

***
