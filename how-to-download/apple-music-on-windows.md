# Apple Music On Windows

## Apple Music On Windows

### Apple Music Download on Windows (WSL)

***

#### **Part 1 - Initial Setup**

_(Skip this if you already have WSL configured or are using Linux.)_

***

**1. Enable Windows Feature**

Enable Windows Feature

Turn on the following Windows Features:

* Virtual Machine Platform
* Windows Hypervisor Platform
* Windows Subsystem For Linux

**2. Install WSL**

Run the following command in Command Prompt or PowerShell:

```bash
winget install --id Microsoft.WSL
```

***

**3. Install a WSL Distro**

* Install Ubuntu 24.04 (recommended):

```bash
winget install --id Canonical.Ubuntu.2404
```

* Open Ubuntu and complete the initial setup process until you're in the shell.

***

Here’s the **Part 2 - Setup** section in a structured and clear format for your documentation:

***

## **Part 2 - Setup**

### **Prerequisites**

Before proceeding, ensure you have the following dependencies installed. Run the following command in your terminal:

### **Update Dependencies**

```bash
sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt clean -y && sudo apt autoclean -y
```

### **Install Dependencies**

```bash
sudo apt install clang wget git unzip ffmpeg cmake build-essential golang pkg-config zlib1g-dev
```

***

### **Step 1: Compile MP4Box**

1.  Clone the GPAC repository and compile MP4Box:

    ```bash
    git clone --depth 1 https://github.com/gpac/gpac.git && cd gpac && ./configure --static-bin && make -j4 && sudo make install && cd ~
    ```

***

### **Step 2: Download and Extract the NDK**

1.  Download the Android NDK required to build the wrapper:

    ```bash
    wget https://dl.google.com/android/repository/android-ndk-r23b-linux.zip && unzip android-ndk-r23b-linux.zip -d ~
    ```

***

### **Step 3: Clone the Repositories**

1.  Clone the `wrapper` and `downloader` repositories:

    ```bash
    git clone --depth 1 https://github.com/WorldObservationLog/wrapper && git clone --depth 1 https://github.com/zhaarey/apple-music-downloader downloader
    ```

***

### **Step 4: Build the Wrapper**

1.  Navigate to the `wrapper` directory and build it:

    ```bash
    cd wrapper && mkdir build && cd build && cmake .. && make -j4 && cd ..
    ```

***

### **Step 5: Run the Wrapper**

1.  Run the wrapper as root. Replace `email:password` with your Apple Music credentials:

    ```bash
    sudo ./wrapper -M 20020 -L email:password
    ```

    * **Note**: The wrapper must run in the background.
    *   If your email or password contains special characters, wrap them in single quotes:

        ```bash
        sudo ./wrapper -M 20020 -L 'email':'password'
        ```

***

### **Step 6: Build the Downloader**

1. Open a new terminal window (Linux) or a new Ubuntu window (Windows).
2.  Navigate to the `downloader` directory:

    ```bash
    cd downloader
    ```
3.  Build the downloader:

    ```bash
    go build
    ```

***

### **Notes**

* At the time of writing, the agent's m3u8 retrieving functionality is disabled due to instability. Specifying the m3u8 port (`-M 20020`) is mandatory to avoid errors.
* Ensure the wrapper is running in the background before using the downloader.

***

#### **To Download Next Time**

**Terminal 1 (Ubuntu)**

Run the wrapper:

```bash
cd wrapper
sudo ./wrapper -M 20020
```

* Enter the password you set during the Ubuntu setup.

***

**Terminal 2 (Ubuntu)**

Run the downloader:

```bash
cd downloader
```

and run the downloader:

#### **ALAC Lossless**

1.  **Download an album or playlist:**

    ```bash
    ./main <url>
    ```
2.  **Select specific tracks:**

    ```bash
    ./main --select <url>
    ```

#### **Dolby Atmos**

1.  **Download an album or playlist Atmos:**

    ```bash
    ./main --atmos <url>
    ```
2.  **Select specific Atmos tracks:**

    ```bash
    ./main --atmos --select <url>
    ```

#### **M4A AAC**

1.  **Download an album or playlist M4A AAC:**

    ```bash
    ./main --aac <url>
    ```
2.  **Select specific M4A AAC tracks:**

    ```bash
    ./main --aac --select <url>
    ```

***

#### **To Update**

**Step 1: Update the Downloader**

```bash
cd downloader
git reset --hard HEAD
git pull origin main
go build
```

**Step 2: Update the Wrapper**

```bash
cd /wrapper
git pull
```

***

#### **Files Location**

After downloading, files are stored in:

```plaintext
Linux > Ubuntu > Home > User > downloader
```

***

#### **Notes**

* Ensure WSL is properly configured and running on your Windows system.
* Replace `<url>` with the actual Apple Music URL of the content you want to download.
* This guide assumes basic familiarity with WSL, Ubuntu, and command-line tools.
