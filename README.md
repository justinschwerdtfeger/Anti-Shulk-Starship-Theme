# Install instructions (mostly for me)
## Install FiraMono Nerd Font
https://www.nerdfonts.com/font-downloads
## Install Starship
https://starship.rs/guide/#%F0%9F%9A%80-installation
### Windows Powershell Setup
#### Install Starship
Install WInget
```powershell
$progressPreference = 'silentlyContinue'
Write-Information "Downloading WinGet and its dependencies..."
Invoke-WebRequest -Uri https://aka.ms/getwinget -OutFile Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle
Invoke-WebRequest -Uri https://aka.ms/Microsoft.VCLibs.x64.14.00.Desktop.appx -OutFile Microsoft.VCLibs.x64.14.00.Desktop.appx
Invoke-WebRequest -Uri https://github.com/microsoft/microsoft-ui-xaml/releases/download/v2.7.3/Microsoft.UI.Xaml.2.7.x64.appx -OutFile Microsoft.UI.Xaml.2.7.x64.appx
Add-AppxPackage Microsoft.VCLibs.x64.14.00.Desktop.appx
Add-AppxPackage Microsoft.UI.Xaml.2.7.x64.appx
Add-AppxPackage Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle
```
Install Starship
```powershell
winget install Starship.Starship
```
#### Add Starship with Transient Prompt to $PROFILE
Create $PROFILE (if it does not already exist)
```powershell
New-Item -Path $PROFILE -Type File -Force
```

Open Profile with notepad
```powershell
notepad $PROFILE
```
Add this to $PROFILE and save
```
function Invoke-Starship-TransientFunction {
  &starship module character
}

Invoke-Expression (&starship init powershell)

Enable-TransientPrompt
```
Enable powershell script execution in Administator Powershell
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```
#### Clone this Repository
Install Git if it is not already installed
```powershell
winget instal Git.Git
```
Clone this repository into AppData Local folder
```powershell
git clone https://github.com/Anti-Shulk/Anti-Shulk-Starship-Theme.git $env:LOCALAPPDATA/Anti-Shulk-Starship-Theme
```
Create a .config directory (if it does not alreayd exist)
```powershell
New-Item -ItemType Directory -Force ~/.config
```
Copy the theme file into the .config directory
```powershell
cp $env:LOCALAPPDATA/Anti-Shulk-Starship-Theme/starship.toml ~/.config
```
