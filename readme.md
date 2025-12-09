## Cloud Seed Fix
The original VST Plugin can be found [**here**](https://github.com/ValdemarOrn/CloudSeed), as well as information about where to get the latest CloudSeed 2.  
This project is an unofficial fork of the original CloudSeed 1 open-source plugin that fixes some bugs that prevent me from using it, as well as fixing the build process by unbreaking and providing the dependencies.

## How to build
### Prerequisites
- Visual Studio 2017 (https://aka.ms/vs/15/release/vs_community.exe)
- .NET Framework 4.5 devtools, last available with Visual Studio 2017. Make sure to check ".NET Desktop development" and "Desktop development with C++"
- Windows SDK (10.0.19041.0 was used)
- \* 7-zip to archive the built plugin

### Build
Clone this repository:
```
git clone https://github.com/fnpngn/CloudSeedFix.git
```
Clone the dependency repositories:
```
git submodule update
```

Look for and open "Developer Command Prompt for VS 2017" in your Start menu  
Navigate to repository folder:
```
cd C:\path\to\CloudSeedFix\
```
Run the build script:
```
Build.bat
```

If successful, the output should be under `.\Builds`:  
`Current` is the latest build result, which is also inside the timestamped archive.   
CloudSeedFix.dll is the VST. Place the contents of the archive in your VSTPlugins folder and you are done.  

### Installation
The raw VST `CloudSeedFix.dll` in the paragraph above is the final product, copy its folder to the VST plugin location (ex: `C:\Program Files\Steinberg\VstPlugins\`).   
Packaging the entire project into an installer is untested and the dependencies for that are currently missing.
That said, here are the dependencies:
- [.NET Framework 4.5 Runtime](https://dotnet.microsoft.com/en-us/download/dotnet-framework)
- [Microsoft Visual C Runtime 2017](https://aka.ms/vc14/vc_redist.x64.exe)
 
## Name changes
To avoid many issues with name collision I decided to rename this plugin version (`CloudSeedFix.dll`). This makes it possible to load the original and this version separately so you don't have to uninstall CloudSeed 1 to try this.

- - -

Following is the original readme for CloudSeed 1


**NOTE: This is a legacy repository**

For the Cloud Seed open source algorithm, visit:

https://github.com/GhostNoteAudio/CloudSeedCore

To download the latest plugin version, visit:

https://ghostnoteaudio.uk/products/cloudseed

The content in the repository is preserved only for legacy reasons. Please use the new version of Cloud Seed from Ghost Note Audio.


---


## Cloud Seed VST

Cloud Seed is an algorithmic reverb plugin built in C# and C++ for emulating huge, endless spaces and modulated echoes. The algorithms are based on the same principles as manu classic studio reverb units from the 1980's, but Cloud Seed does not attempt to model any specific device, or even to be a general-purpose reverb plugin at all. It is best employed as a special effect, for creating thick, lush pads out of simple input sounds. 

![](Documentation/Screenshot.png)

## Download & Install

1. Download the latest version of Cloud Seed from the [**Releases Page**](https://github.com/ValdemarOrn/CloudSeed/releases).
2. Please read the **[Installation Instructions](https://github.com/ValdemarOrn/CloudSeed/tree/master/Installation%20Instructions)**

**If you get errors about either "vcruntime140.dll" or 
"msvcp140.dll", you need to install the Microsoft Visual C Runtime Redistributable as described in the Installation Instructions.**

## System Requirements

* Microsoft Windows 7, 8, 8.1, 10 or above
* 64 Bit Processor and operating system (support for 32 bit removes as of v1.0)
* .NET Framework 4.5. This can be installed using the provided installer. **Please make sure to check all the required dependencies on your system.** If you're not sure, leave them checked, the installer will automatically determine whether you already have the required libraries installed.

## Documentation

See the [**Documentation Page**](https://github.com/ValdemarOrn/CloudSeed/tree/master/Documentation) for an overview of the user interface and an explanation of the reverberation kernel.

## Reverb Kernel Architecture (for developers)

![](Documentation/CloudSeed.png)

the code was originally developed in C# and then ported over to C++. The current version contains a full implementation of the reverb kernel in CPU-efficient C++ code. The user interface is built using WPF (Windows Presentation Foundation), and the plugin uses [SharpSoundDevice](https://github.com/ValdemarOrn/SharpSoundDevice) to communicate with a VST host.