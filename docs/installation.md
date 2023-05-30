<h1 align="center">Installation</h1>

## Application Executables

Application Executables are created and uploaded to the [releases](https://github.com/DIP-Editor/DIP-dev/releases) page on GitHub. There are three releases:
 - [`Latest Windows Build`](https://github.com/DIP-Editor/DIP-dev/releases/latest-windows-build)
 - [`Latest Linux Build`](https://github.com/DIP-Editor/DIP-dev/releases/latest-linux-build)
 - [`Latest Mac Build`](https://github.com/DIP-Editor/DIP-dev/releases/latest-mac-build)

These can all be downloaded and run like native applications on their respective operating systems. They are also much smaller than the executable created on ones own machine, as they are stripped of all unnecessary files and libraries. These files were created using [PyInstaller](https://www.pyinstaller.org/) and the files used to create these builds are as shown:
 - Windows:
   - [`WindowsBuild.yaml`](../.github/workflows/WindowsBuild.yaml)
   - [`windows-DIP.spec`](../windows-DIP.spec)
 - MacOS:
   - [`MacBuild.yaml`](../.github/workflows/MacBuild.yaml)
   - [`DIP.spec`](../DIP.spec)
 - Linux:
   - [`LinuxBuild.yaml`](../.github/workflows/LinuxBuild.yaml)
   - [`DIP.spec`](../DIP.spec)

## Application Source

The application source be from either a git clone [here](https://github.com/DIP-Editor/DIP-dev.git) or from a zip file [here](https://github.com/DIP-Editor/DIP-dev/archive/refs/heads/main.zip). Either way, the code is still runnable and usable. Once the source has been downloaded, use `pip install -r requirements.txt` to install all the dependencies. Then, run `python3 DIP.py` to start the application. If you would like to create an executable, use `pyinstaller DIP.spec` or `PyInstaller windows-DIP.spec` if you are a Windows user.

## [Next: Using `DIP`](./use-dip.md) | [Previous: Overview](../overview.md) | [Back to Overview](./overview.md)