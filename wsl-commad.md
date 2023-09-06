
## Table of Contents

- [Install Linux Distribution on Windows 11](#how-to-setup-wsl-on-windows-11)
- [Basic commands for WSL](#Basic-commands-for-WSL)

## How to setup wsl on windows 11

1. Prerequisites to Install Linux on Windows 11

To do that, open Windows 11 Task manager (Ctrl + Shift + Esc) and go to the ‘Performance’ page on the left panel. Then ensure ‘Virtualization’ is ‘Enabled’ at the bottom of the right side page.

2. First, open the Start menu and search for ‘Windows features’. Then, select the ‘Turn Windows features on and off’ control panel option from the search result.

    In the Windows Features dialog box, tick the ‘Windows Subsystem for Linux’ and ‘Virtual Machine Platform’ option and click ‘OK’

3. Before setting up WSL 2 as your default version for all Linux distributions, download the WSL Linux kernel package update for x64 systems from this link. 

4. Then, run the ‘.msi’ installer you downloaded and install it. Click ‘Next’ in the wizard to continue.

5. Enable WSL 1 via PowerShell

````bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
````
6. Enable WSL 2 via PowerShell
````bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
````

````bash
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
````

7. To set WSL 2 as your default version when installing a new Linux distribution, open PowerShell and run the following command:

````bash
wsl –set-default-version 2
````
Then restart your system to switch the feature from WSL 1 to WSL 2.

8. Install WSL from Microsoft Store

You can also download and install WSL from the Microsoft Store. Launch the Microsoft Store app and search for ‘Windows Subsystem for Linux’. Then, click the ‘Get’ button on Windows Subsystem for Linux Preview’

![Alt text](image.png)

Microsoft Store will automatically download and install the required files.

9. In the Microsoft Store, you can search ‘Linux’ to get the list of Linux distros available and select your desired distro. 

![Alt text](image-1.png)

10. When the Windows Terminal opens, type the following command and press Enter to install WSL:

````bash
wsl --install
````

11. Then, enter the new username and password to complete the setup. This username doesn’t necessarily need to be the same as the Windows account.

12. After setting up the username and password, the Ubuntu terminal will launch in a separate terminal window as shown below.

![Alt text](image-2.png)

## Basic commands for WSL

To get the list of other available distributions of Linux via the command line, type either of the following commands:

```
wsl --list --online

or

wsl -l -o
```

To install a new distro, use the below command:

```
wsl --install -d <Distro>
```

to update and upgrade apt 

```
sudo apt update && apt upgrade
```

To create a new user account

```
sudo adduser <username>

```

To remove a specific user account from the WSL Linux distro

```
sudo deluser <username>
```