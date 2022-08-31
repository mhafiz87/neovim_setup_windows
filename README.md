# **NEOVIM SETUP WINDOWS**

- [**NEOVIM SETUP WINDOWS**](#neovim-setup-windows)
  - [**Install**](#install)
  - [**References**](#references)

## **Install**

- Download from [here](https://github.com/neovim/neovim/releases/download/nightly/nvim-win64.zip) and extract to ***%localappdata%\Programs\Neovim***. Run the script below in powershell to execute this.

    ```powershell
    $Url = "https://github.com/neovim/neovim/releases/download/nightly/nvim-win64.zip"
    $DownloadZipFile = "$env:localappdata\Programs\" + $(Split-Path -Path $Url -Leaf)
    Invoke-WebRequest -URI $Url -OutFile $DownloadZipFile
    $ExtractPath = "$env:localappdata\Programs\"
    $ExtractShell = New-Object -ComObject Shell.Application
    $ExtractFiles = $ExtractShell.Namespace($DownloadZipFile).Items()
    $ExtractShell.NameSpace($ExtractPath).CopyHere($ExtractFiles)
    Remove-Item -Path $DownloadZipFile
    Start-Process $ExtractPath
    ```

- Add neovim to user environment

    ```powershell
    [System.Environment]::SetEnvironmentVariable('path', [System.Environment]::GetEnvironmentVariable('path', "User") + $env:localappdata + "\Program\nvim-win64\bin;","User")
    ```

## **References**

1. [neovim](https://github.com/neovim/neovim/)
2. [Neovim from scratch](https://github.com/LunarVim/Neovim-from-scratch)
3. [Packer](https://github.com/wbthomason/packer.nvim)
