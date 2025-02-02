# Apple Music Downloader

## Apple Music Downloader

This project provides tools to download Apple Music tracks, albums, and playlists in high-quality formats (ALAC and Atmos) on various platforms, including **Android**, **macOS**, and **Windows (via WSL)**. It uses a combination of a decryption client, a downloader, and a wrapper to facilitate the process.

***

### **Supported Platforms**

* **Android**
* **macOS**
* **Windows (using WSL)**

***

### **Features**

* Download Apple Music tracks, albums, and playlists.
* Support for **ALAC** (Apple Lossless Audio Codec) and **Atmos** formats.
* Cross-platform compatibility.
* Easy-to-follow setup and usage instructions.

***

### **Prerequisites**

* An active **Apple Music subscription**.
* Basic familiarity with command-line tools.
* For Windows: **WSL** (Windows Subsystem for Linux) must be installed.

***

### **Quick Start**

#### **Android**

1. Download and install the required APKs:
   * [Decryption Client](https://github.com/itouakirai/apple-music-jshook-script/releases/download/wsa/Apple.Music_4.9.3_arm64v8a_gadget.apk)
   * [Download Client](https://github.com/hanxinhao000/ZeroTermux/releases/download/release/ZeroTermux-0.118.1.41.apk)
2. Follow the Android Guide for detailed instructions.

***

#### **macOS**

1.  Install dependencies:

    ```bash
    brew install go gpac git docker
    ```
2.  Clone the repository:

    ```bash
    git clone https://github.com/zhaarey/apple-music-alac-atmos-downloader.git
    ```
3. Follow the macOS Guide for detailed instructions.

***

#### **Windows (WSL)**

1.  Install WSL and Ubuntu:

    ```bash
    winget install --id Microsoft.WSL
    winget install --id Canonical.Ubuntu.2404
    ```
2. Follow the Windows Guide for detailed instructions.

***

### **Usage**

*   For **Album/Playlist/Artist**:

    ```bash
    go run main.go <url>
    ```
*   For **Atmos Tracks**:

    ```bash
    go run main.go --atmos <url>
    ```
*   For **Selecting Specific Tracks**:

    ```bash
    go run main.go --select <url>
    ```

***

### **Examples**

1.  Download an album:

    ```bash
    go run main.go https://music.apple.com/vn/album/ditto/1657231957
    ```
2.  Download Atmos tracks:

    ```bash
    go run main.go --atmos https://music.apple.com/vn/album/ditto/1657231957
    ```
3.  Select specific tracks:

    ```bash
    go run main.go --select https://music.apple.com/vn/album/ditto/1657231957
    ```

***

### **Troubleshooting**

*   **Special Characters in Credentials**: If your email or password contains special characters, wrap them in single quotes:

    ```bash
    sudo ./wrapper -M 20020 -L 'email':'password'
    ```

    Example:

    ```bash
    sudo ./wrapper -M 20020 -L 'alex@gmail.com':'Alexg1osd@(#$'
    ```
* For other issues, refer to the Troubleshooting Guide.

***

### **Updating**

To update the downloader and wrapper:

1.  Update the downloader:

    ```bash
    cd downloader
    git pull
    go build
    ```
2.  Update the wrapper:

    ```bash
    cd /wrapper
    git pull
    ```

***

### **File Locations**

* **Android**: Files are saved in `/storage/emulated/0/Music/AM/`.
* **macOS/Windows**: Files are saved in the `downloader` directory.

***

### **Disclaimer**

This project is for educational purposes only. Ensure you have the right to download and use the content. The developers are not responsible for any misuse of this tool.

***

### **License**

This project is licensed under the MIT License. See the LICENSE file for details.
