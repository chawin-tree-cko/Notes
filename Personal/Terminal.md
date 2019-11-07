# Terminal

## [Windows Terminal](https://github.com/microsoft/terminal)

1. Get the repository and update submodules

    ```cmd
    git clone https://github.com/microsoft/terminal
    git submodule update --init --recursive
    ```

1. Build the repository

    ```powershell
    Import-Module .\tools\OpenConsole.psm1
    Set-MsBuildDevEnvironment
    Invoke-OpenConsoleBuild
    ```

1. Deploy `CascadiaPackage` (Release / x64) to install **Windows Terminal (Preview) Windows app

## Customisation

1. Install [Posh Git](https://github.com/dahlbyk/posh-git) and [Oh My Posh](https://github.com/JanDeDobbeleer/oh-my-posh)

    ```powershell
    Install-Module posh-git -Scope CurrentUser
    Install-Module oh-my-posh -Scope CurrentUser
    ```

1. Run `notepad $PROFILE` and append the following to set the theme (themes can be found in the [repository README](https://github.com/JanDeDobbeleer/oh-my-posh#themes))

    ```cmd
    Import-Module posh-git
    Import-Module oh-my-posh
    Set-Theme Agnoster
    ```

1. Update `profiles.json` to include the relevant font in the profile

    ```json
        {
            // Make changes here to the powershell.exe profile
            "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
            "name": "Windows PowerShell",
            "commandline": "powershell.exe",
            "fontFace": "Delugia Nerd Font",
            "hidden": false
        },
    ```