# Apple Music On Windows

## Apple Music Download on Windows (WSL)

***

### **Part 1 - Initial Setup**

_(Skip this if you already have WSL configured or are using Linux.)_

***

#### **1. Install WSL**

Run the following command in Command Prompt or PowerShell:

```bash
winget install --id Microsoft.WSL
```

***

#### **2. Install a WSL Distro**

* Install Ubuntu 24.04 (recommended):

```bash
winget install --id Canonical.Ubuntu.2404
```

* Open Ubuntu and complete the initial setup process until you're in the shell.

***

***

### **To Download Next Time**

#### **Terminal 1 (Ubuntu)**

Run the wrapper:

```bash
cd wrapper
sudo ./wrapper -M 20020
```

* Enter the password you set during the Ubuntu setup.

***

#### **Terminal 2 (Ubuntu)**

**For Album, Playlist, or Artist:**

```bash
./main <url>
```

**For Atmos Tracks:**

```bash
./main --atmos <url>
```

**For Selecting Specific Tracks:**

```bash
./main --select <url>
```

***

### **Examples**

1.  **Download an album or playlist:**

    ```bash
    ./main https://music.apple.com/vn/album/ditto/1657231957
    ```
2.  **Download Atmos tracks:**

    ```bash
    ./main --atmos https://music.apple.com/vn/album/ditto/1657231957
    ```
3.  **Select specific tracks to download:**

    ```bash
    ./main --select https://music.apple.com/vn/album/ditto/1657231957
    ./main --atmos --select https://music.apple.com/vn/album/ditto/1657231957
    ```

***

### **To Update**

#### **Step 1: Update the Downloader**

```bash
cd downloader
git pull
go build
```

#### **Step 2: Update the Wrapper**

```bash
cd /wrapper
git pull
```

***

### **Files Location**

After downloading, files are stored in:

```plaintext
Linux > Ubuntu > Home > User > downloader
```

***

### **Notes**

* Ensure WSL is properly configured and running on your Windows system.
* Replace `<url>` with the actual Apple Music URL of the content you want to download.
* This guide assumes basic familiarity with WSL, Ubuntu, and command-line tools.
