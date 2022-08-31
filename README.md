# **NEOVIM SETUP WINDOWS**

## **Install**

- Download from [here](https://github.com/neovim/neovim/releases/download/nightly/nvim-win64.zip) and extract to ***%localappdata%\Programs\Neovim***

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
