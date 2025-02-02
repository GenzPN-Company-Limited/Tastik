# Apple Music On MacOS

## Apple Music Download on macOS

***

### **Preface**

This guide provides step-by-step instructions to download Apple Music on macOS using Docker and a command-line tool.

***

### **Installation**

#### **Step 1: Set Up the Environment**

1. Open the Terminal.
2. Install the required dependencies and clone the downloader repository:

```bash
brew install go gpac git docker ffmpeg && git clone https://github.com/zhaarey/apple-music-alac-atmos-downloader.git
```

***

#### **Step 2: Log In to the Wrapper**

1. Use the Docker command to log in to the wrapper. Replace `username:password` with your Apple Music account credentials (**Subscription required**).
2. If you have enabled 2FA, wait for the verification code, then open a new terminal and follow the prompts to enter the code.
3. If the response is `type 6`, the login is successful. Close all terminal windows.

***

### **Usage**

#### **1. Start the Wrapper**

Open the first terminal and run the appropriate command for your Mac's chip:

**For M Chip (Apple Silicon):**

```bash
docker run -v ./rootfs/data:/app/rootfs/data -p 10020:10020 -p 20020:20020 -e args="-M 20020 -H 0.0.0.0" --rm ghcr.io/itouakirai/wrapper:arm
```

**For Intel Chip:**

```bash
docker run -v ./rootfs/data:/app/rootfs/data -p 10020:10020 -p 20020:20020 -e args="-M 20020 -H 0.0.0.0" --rm ghcr.io/itouakirai/wrapper:x86
```

***

#### **2. Navigate to the Downloader Directory**

Open a second terminal and navigate to the downloader directory:

```bash
cd apple-music-alac-atmos-downloader
```

***

#### **Step 3: Start Downloading**

Use the following commands to start downloading

#### **ALAC Lossless**

1.  **Download an album or playlist:**

    ```bash
    go run main.go <url>
    ```
3.  **Select specific tracks:**

    ```bash
    go run main.go --select <url>
    ```
#### **Dolby Atmos**

1.  **Download an album or playlist Atmos:**

    ```bash
    go run main.go --atmos <url>
    ```

2.  **Select specific Atmos tracks:**

    ```bash
    go run main.go --atmos --select <url>
    ```
#### **M4A AAC**

1.  **Download an album or playlist M4A AAC:**

    ```bash
    go run main.go --aac <url>
    ```

2.  **Select specific M4A AAC tracks:**

    ```bash
    go run main.go --aac --select <url>
    ```

***

### **Notes**

* Ensure Docker is installed and running on your macOS.
* Replace `<url>` with the actual Apple Music URL of the content you want to download.
* Downloaded files will be saved in the specified directories within the `apple-music-alac-atmos-downloader` folder.
* This guide assumes basic familiarity with Terminal and Docker.
