# Running Sagemath/Fpylll on Windows

Heads up: all these methods take some time to complete. These methods were tried on Windows 8.1 and 10, some should also run on Windows 7.

## The official Sagemath Windows installer

Supports:
- Windows 7+

Pros:
- Does not require virtualisation.
- Should support most versions of Windows.

Cons: 
- Results in a slower install.

Istructions:
1. Get a copy of the installer from https://github.com/sagemath/sage-windows/releases.
2. When running the installer, Windows Defender may complain. Choose to run anyway.
3. Once setup is done, there should be three links on your desktop:
   - `Sagemath` will open a console with Sage inside (it will take a while to start).
   - `Sagemath` shell will open a shell into the Cygwin system that Sage is installed into. Run `sage`.
   - `Sagemath notebook` will first setup an interactive notebook. Then a browser window should open directing you to the notebook (or a Word document with a link to the right internal url, use `Ctrl + click` to open).

## Windows Subsystem for Linux

Supports:
- Windows 10

Pros:
- Native virtualisation method for Windows 10.

Cons:
- First need to enable WSL.

Instructions:
1. Enable WSL: https://docs.microsoft.com/en-us/windows/wsl/install-win10.
2. Install a Linux distribution from the Microsoft Store, Ubuntu should be fine.
3. Once Linux is running, run `sudo apt install sagemath` to get Sage.
4. Run `sage`.

Notes:
- You can access your Windows file system at `/mnt/c/`.

## Docker Desktop

Supports: 
- Windows 10 Pro or Enterprise

Pros:
- Easy to use, results in a fast install of Sage.

Cons:
- Limited Windows compatibility.
- Requires virtualisation.
  
What could go wrong: 
- Machines running Windows 8+ may have virtualisation (VT-X/AMD-v) disabled by default. Enabling that can be a little tricky.

Instructions:
1. Get the Docker Desktop for Windows installer from https://hub.docker.com/editions/community/docker-ce-desktop-windows/.
2. Run the installer. Default configuration should work. It will require to restart.
3. Run Docker Desktop. Once it's up, setup should be done.
4. Run Powershell/CMD.exe. Try running `docker run hello-world`. It should successfully run.
5. Run `docker pull martinralbrecht/sagemath-g6k`.
6. Run Sage with `docker run -it martinralbrecht/sagemath-g6k`.

## Virtual Box

Supports:
- OS X
- Windows 7+

Pros:
- You'll be running Linux directly.

Cons:
- Requires installing Linux, then Sage inside.

What could go wrong: 
- Machines running Windows 8+ may have virtualisation (VT-X/AMD-v) disabled by default. Enabling that can be a little tricky.

Instructions:
1. Get and install a copy of VirtualBox on https://www.virtualbox.org/wiki/Downloads depending on your machine's (host) operating system. Note: if running Windows 7, you may want to use an older build of VirtualBox from https://www.virtualbox.org/wiki/Download_Old_Builds, say 5.2 or earlier.
2. Get a Linux distribution install image. A graphically lightweight is recommended when virtualising. Say, get the latest iso file for Xubuntu 19.10 from any of the mirrors on https://xubuntu.org/download/.
3. Create a virtual machine and install Linux. In the case of Xubuntu 19.10, a VM with 1024MB of ram and 20GB of hard drive should suffice, but feel free to be more generous.
4. Follow the default instructions to install Xubuntu.
5. Once that's done, log into your Xubuntu install, and run `sudo apt update; sudo apt install sagemath`.
6. Run `sage` in your terminal.

