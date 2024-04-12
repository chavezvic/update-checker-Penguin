# update-checker-Penguin
Do you know if your Linux distro is outdated and insecure? Try this Linux Update Checker to save your day.

# Check CVE-2024-3094

## Description
This script checks if your Linux distribution is affected by CVE-2024-3094 and if updates are needed.

## Installation
- Python 3.x is required to run this script.
- No additional dependencies are needed.

## Usage
1. Open a terminal.
2. Navigate to the directory where the script is located.
3. Run the following command:
   ```bash
   python check_cve-v2.py
## Functions in the Script:
### `get_linux_distribution()`:
- This function finds out which version or type of Linux is installed on the computer. It uses a program called `lsb_release` to do this.
- If `lsb_release` can't be found (like if it's not installed), the function returns "Unknown" because it can't figure out the Linux version.
- Note: This method may encounter errors on certain Linux distributions.

### `get_kernel_version()`:
- This function figures out the version of the kernel (the heart of the operating system) that's running on the computer. It uses a built-in method called `os.uname().release` to get this information.
- Note: This method is generally reliable across different Linux distributions.

### `get_installed_packages()`:
- This function tries to make a list of all the software packages that are currently installed on the computer. It uses a command called `dpkg --get-selections` to do this.
- If the `dpkg` command is not available (not installed), the function returns an empty list because it can't get the list of packages.
- Note: This method relies on `dpkg` and may not work on distributions that use different package managers (e.g., RPM-based distributions like Fedora, CentOS).

### `get_security_updates()`:
- This function pretends to check if there are any important security updates available for the system. It does this by using `apt-get upgrade --just-print`.
- If `apt-get` (another program used to manage software) is not found, the function returns an empty list, meaning it couldn't really check for updates.
- Note: This method is specific to Debian-based distributions and may not be applicable to other Linux distributions.

### `check_update_needed()`:
- This function coordinates everything. It calls the other functions to gather all the necessary information.
- Then it prints out the Linux version, kernel version, and checks if any updates might be needed based on the information gathered.
- For example, it might say something like "Your Linux version may need an update" based on the gathered data.
- Note: This function's behavior may vary depending on the Linux distribution and system configuration.

## References

### Linux System Administration References:
- **"The Linux Command Line" by William E. Shotts Jr.:**
  - This book is a complete guidebook for using the command line in Linux. I've got `lsb_release`, `dpkg`, and `apt-get` work, from this book. 
  - Website: http://linuxcommand.org

### Python Programming References:
- **"Automate the Boring Stuff with Python" by Al Sweigart:**
  - This book teaches practical ways to program in Python. Great for learning how to make your computer to do useful things with Python.
  - Website: https://automatetheboringstuff.com
