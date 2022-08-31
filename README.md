# **NEOVIM SETUP WINDOWS**

- [**NEOVIM SETUP WINDOWS**](#neovim-setup-windows)
  - [**Install**](#install)
  - [**References**](#references)

## **Install**

- Download from [here](https://github.com/neovim/neovim/releases/download/nightly/nvim-win64.zip) and extract to ***%LOCALAPPDATA%\Programs\Neovim***. Run the script below in powershell to execute this.

    ```powershell
    $Url = "https://github.com/neovim/neovim/releases/download/nightly/nvim-win64.zip"
    $DownloadZipFile = "$env:LOCALAPPDATA\Programs\" + $(Split-Path -Path $Url -Leaf)
    Invoke-WebRequest -URI $Url -OutFile $DownloadZipFile
    $ExtractPath = "$env:LOCALAPPDATA\Programs\"
    $ExtractShell = New-Object -ComObject Shell.Application
    $ExtractFiles = $ExtractShell.Namespace($DownloadZipFile).Items()
    $ExtractShell.NameSpace($ExtractPath).CopyHere($ExtractFiles)
    Remove-Item -Path $DownloadZipFile
    Start-Process $ExtractPath
    ```

- Add neovim to user environment.

    ```powershell
    [System.Environment]::SetEnvironmentVariable('path', [System.Environment]::GetEnvironmentVariable('path', "User") + $env:LOCALAPPDATA + "\Program\nvim-win64\bin;","User")
    ```

- Download ***packer*** plugin.

    ```powershell
    git clone https://github.com/wbthomason/packer.nvim "$env:LOCALAPPDATA\nvim-data\site\pack\packer\start\packer.nvim"
    ```

- Create nvim folder to store configuration files.

    ```powershell
    New-Item -ItemType Directory -Path $env:LOCALAPPDATA\nvim
    ```

- Shortcut: Clone this repo:

    ```powershell
    git clone https://github.com/mhafiz87/neovim_setup_windows.git $env:LOCALAPPDATA\nvim
    ```

## **References**

1. [neovim](https://github.com/neovim/neovim/)
2. [Neovim from scratch](https://github.com/LunarVim/Neovim-from-scratch)
3. [Packer](https://github.com/wbthomason/packer.nvim)
