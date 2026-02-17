# open DaVinci tools
Free tools to upgrade your experience and results with DaVinci Resolve



# Installation of DaVinci Resolve
- [Windows](https://github.com/ArmerAlex/open-davinci-tools/edit/main/README.md#windows)
- [Mac](https://github.com/ArmerAlex/open-davinci-tools/edit/main/README.md#mac)
- [Linux](https://github.com/ArmerAlex/open-davinci-tools/edit/main/README.md#linux-tested-on-fedora-workstation-43)


## Windows ##
1. Install the latest version of DaVinci Resolve ([Download here](https://www.blackmagicdesign.com/products/davinciresolve)) for Windows x86
2. Locate the .zip File in your Downloads Folder
3. Right Click on the File and press Extract All
4. Open the extracted folder and double-click the .exe file to start the installation.
5. Go through the installation and accept the License Agreement
6. DaVinci Resolve should be on your Computer!
## Mac
## Linux (tested on Fedora Workstation 43) ##
#### 1. Install the latest version of DaVinci Resolve ([Download here](https://www.blackmagicdesign.com/products/davinciresolve)) for Linux and unzip ####
#### 2. Install missing dependencies (some may already be installed) ####
- For Fedora use
  `sudo dnf install [name of dependency]` (optionally with -y)
- Dependencies: 
```
libxcrypt-compat \
mesa-libGLU \
alsa-plugins-pulseaudio \
apr apr-util \
fuse-libs \
python3.11 python3.11-libs
```
#### 3. Run the installer ####
#### 3.1 add executable permission:
   - with Terminal:
     - `chmod +x Path/to/installer.run (e.g. ~/Downloads/DaVinci_Resolve_20.3.2_Linux/DaVinci_Resolve_20.3.2_Linux.run`
   - or use the File explorer (GUI):
     - select *.run file
     - Right click > properties
     - enable "Executable as Program"
#### 3.2 Run Installer
- in the Terminal use this command to start the Installer (you may need to change the path to the file)
- optional:
`cd ~/Downloads/DaVinci_Resolve_20.3.2_Linux.run (change version no. or path if applicable)`
```
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.3.2_Linux.run
```
- Install DaVinci Resolve with the Installer
#### 4 Configuration (without this DaVinci Resolve will not open)
##### First: #####
Run 
```
cd /opt/resolve/libs
sudo mkdir disabled
sudo mv libglib* disabled
sudo mv libgio* disabled
sudo mv libgmodule* disabled
```
##### Second: #####
- make a new file called '`resolve`' at `/usr/local/bin`
  - `sudo nano /usr/local/bin/resolve`
- Paste this: (Ctrl + Shift + V)
```
#!/bin/bash
export LD_PRELOAD=/usr/lib64/libpython3.11.so.1.0
export QT_QPA_PLATFORM=xcb
export __GL_THREADED_OPTIMIZATIONS=0
/opt/resolve/bin/resolve "$@"
```
- and save file
  - `Ctrl + X`
  - `Y`
  - `Enter`
##### Lastly: #####
- make 'resolve' executable and run it from the command line (see 3.1)

Now you should have DaVinci Resolve on Linux (yes i know it's stupidly complicated)
