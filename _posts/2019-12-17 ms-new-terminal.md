---
layout:     post
title:      "Get a linux terminal under win10"
subtitle:   "using microsoft new Windows Terminal and WSL2"
author:     "Mengxin"
lang:       en
date:       2019-12-16
tags:
 - Tools
 - Dev
---


## Getting a Linux Distro

### Install the Windows Terminal:

The new Windows Terminal is now available on the windows store:

![1576541907180](C:\Users\untra\AppData\Roaming\Typora\typora-user-images\1576541907180.png)

### Install the WSL:

Open PowerShell as **Administrator** and run:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Then restart your computer

### Install a Linux Distribution:

Enter `wsl` or any distribution's name such as `ubuntu` in the research bar of windows store :

![1576511441463](C:\Users\untra\AppData\Roaming\Typora\typora-user-images\1576511441463.png)

Chose a Linux distribution and install it.

### Initialize the distro

1. Launch a new instance by enter the distro's name ( for instance, `Ubuntu`) in bash ( which can be called by pressing`win+R` ) :

   ![1576548899202](C:\Users\untra\AppData\Roaming\Typora\typora-user-images\1576548899202.png)

2. Set up a new Linux account :

   ![1576511773849](C:\Users\untra\AppData\Roaming\Typora\typora-user-images\1576511773849.png)

3. update & upgrade your distro by :

   ```bash
   sudo apt update && sudo apt upgrade
   ```



## Installing WSL2

### Check your windows builds version

As of now, WSL2 is only available for windows10 builds **18917** or higher.

To check your windows builds version, run `ver` in cmd :

![1576512833093](C:\Users\untra\AppData\Roaming\Typora\typora-user-images\1576512833093.png)

In this case, check this link to get the most recent windows builds: https://insider.windows.com/en-us/how-to-pc/

### Enable WSL

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### Set your distro

```bash
wsl --set-version <Distro> 2
```



## Adding the distro into the Windows Terminal

Pressing `cltr+,` to open the setting page, which correspond to a JSON file.

In the `profiles` object, Powershell, cmd and Azure are already registered, use the same pattern to register the newly installed WSL. 

**Create your own guid for your distribution. Visual Studio provides a guid generator in `Tools->Creat GUID`**

You can customize your Terminal by adding `colorScheme` , some colorScheme are proposed as below:

```json

// To view the default settings, hold "alt" while clicking on the "Settings" button.
// For documentation on these settings, see: https://aka.ms/terminal-documentation

{
    "$schema": "https://aka.ms/terminal-profiles-schema",

    "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",

    "profiles":
    [
      {
        // Make changes here to the powershell.exe profile

        "acrylicOpacity": 0.75,
        "closeOnExit": true,
        //"colorScheme": "Campbell",
        "colorScheme": "Solarized Dark",
        "cursorColor": "#657B83",
        "cursorShape": "bar",
        "fontFace": "Sarasa Term SC",
        "fontSize": 12,

        "historySize": 9001,


        "padding": "0, 0, 0, 0",
        "snapOnInput": true,
        "startingDirectory": "%USERPROFILE%",
        "useAcrylic": true,
        "tabTitle": "PowerShell",

        "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
        "name": "PowerShell",
        "commandline": "powershell.exe",
        "hidden": false
      },
      {
        // Make changes here to the cmd.exe profile
        //"colorScheme": "Solarized Dark",
        "acrylicOpacity": 0.75,
        "useAcrylic": true,
        "colorScheme": "Campbell",
        "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
        "name": "cmd",
        "commandline": "cmd.exe",
        "hidden": false
      },



      {
        "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
        "hidden": false,
        "name": "Azure Cloud Shell",
        "source": "Windows.Terminal.Azure"
      },



      {
        "acrylicOpacity": 0.85,
        "closeOnExit": false,
        "colorScheme": "UbuntuLegit",
        "commandline": "wsl ~",
        "cursorColor": "#4A4543",
        "cursorShape": "bar",
        "fontFace": "Sarasa Term SC",
        "fontSize": 12,

        "historySize": 9001,
        "icon": "ms-appdata:///roaming/ubuntu_32px.png",

        "padding": "0, 0, 0, 0",
        "snapOnInput": true,
        "useAcrylic": true,


        "guid": "{2c4de342-38b7-51cf-b940-2309a097f518}",
        "hidden": false,
        "name": "Ubuntu",
        "source": "Windows.Terminal.Wsl"
      }
    ],

    // Add custom color schemes to this array
  "schemes": [
    {
      "background": "#0C0C0C",
      "black": "#0C0C0C",
      "blue": "#0037DA",
      "brightBlack": "#767676",
      "brightBlue": "#3B78FF",
      "brightCyan": "#61D6D6",
      "brightGreen": "#16C60C",
      "brightPurple": "#B4009E",
      "brightRed": "#E74856",
      "brightWhite": "#F2F2F2",
      "brightYellow": "#F9F1A5",
      "cyan": "#3A96DD",
      "foreground": "#A7B191",
      "green": "#13A10E",
      "name": "Campbell",
      "purple": "#881798",
      "red": "#C50F1F",
      "white": "#CCCCCC",
      "yellow": "#C19C00"
    },
    {
      "background": "#073642",
      "black": "#073642",
      "blue": "#268BD2",
      "brightBlack": "#002B36",
      "brightBlue": "#839496",
      "brightCyan": "#93A1A1",
      "brightGreen": "#586E75",
      "brightPurple": "#6C71C4",
      "brightRed": "#CB4B16",
      "brightWhite": "#FDF6E3",
      "brightYellow": "#657B83",
      "cyan": "#2AA198",
      "foreground": "#FDF6E3",
      "green": "#859900",
      "name": "Solarized Dark",
      "purple": "#D33682",
      "red": "#D30102",
      "white": "#EEE8D5",
      "yellow": "#B58900"
    },
    {
      "background": "#FDF6E3",
      "black": "#073642",
      "blue": "#268BD2",
      "brightBlack": "#002B36",
      "brightBlue": "#839496",
      "brightCyan": "#93A1A1",
      "brightGreen": "#586E75",
      "brightPurple": "#6C71C4",
      "brightRed": "#CB4B16",
      "brightWhite": "#FDF6E3",
      "brightYellow": "#657B83",
      "cyan": "#2AA198",
      "foreground": "#073642",
      "green": "#859900",
      "name": "Solarized Light",
      "purple": "#D33682",
      "red": "#D30102",
      "white": "#EEE8D5",
      "yellow": "#B58900"
    },
    {
      "background": "#2C001E",
      "black": "#EEEEEC",
      "blue": "#268BD2",
      "brightBlack": "#002B36",
      "brightBlue": "#839496",
      "brightCyan": "#93A1A1",
      "brightGreen": "#586E75",
      "brightPurple": "#6C71C4",
      "brightRed": "#CB4B16",
      "brightWhite": "#FDF6E3",
      "brightYellow": "#657B83",
      "cyan": "#2AA198",
      "foreground": "#EEEEEC",
      "green": "#729FCF",
      "name": "Ubuntu",
      "purple": "#D33682",
      "red": "#16C60C",
      "white": "#EEE8D5",
      "yellow": "#B58900"
    },
    {
      "background": "#2C001E",
      "black": "#4E9A06",
      "blue": "#3465A4",
      "brightBlack": "#555753",
      "brightBlue": "#729FCF",
      "brightCyan": "#34E2E2",
      "brightGreen": "#8AE234",
      "brightPurple": "#AD7FA8",
      "brightRed": "#EF2929",
      "brightWhite": "#EEEEEE",
      "brightYellow": "#FCE94F",
      "cyan": "#06989A",
      "foreground": "#EEEEEE",
      "green": "#300A24",
      "name": "UbuntuLegit",
      "purple": "#75507B",
      "red": "#CC0000",
      "white": "#D3D7CF",
      "yellow": "#C4A000"
    },
    {
      "background": "#F7F7F7",
      "black": "#090300",
      "blue": "#01A0E4",
      "brightBlack": "#5C5855",
      "brightBlue": "#807D7C",
      "brightCyan": "#CDAB53",
      "brightGreen": "#3A3432",
      "brightPurple": "#D6D5D4",
      "brightRed": "#E8BBD0",
      "brightWhite": "#F7F7F7",
      "brightYellow": "#4A4543",
      "cyan": "#B5E4F4",
      "foreground": "#4A4543",
      "green": "#01A252",
      "name": "3024 Day",
      "purple": "#A16A94",
      "red": "#DB2D20",
      "white": "#A5A2A2",
      "yellow": "#FDED02"
    },
    {
      "background": "#FFFFFF",
      "black": "#011627",
      "blue": "#4876D6",
      "brightBlack": "#7A8181",
      "brightBlue": "#5CA7E4",
      "brightCyan": "#00C990",
      "brightGreen": "#49D0C5",
      "brightPurple": "#697098",
      "brightRed": "#F76E6E",
      "brightWhite": "#989FB1",
      "brightYellow": "#DAC26B",
      "cyan": "#08916A",
      "foreground": "#403F53",
      "green": "#2AA298",
      "name": "Night Owlish Light",
      "purple": "#403F53",
      "red": "#D3423E",
      "white": "#7A8181",
      "yellow": "#DAAA01"
    },
    {
      "background": "#FFFFFF",
      "black": "#000000",
      "blue": "#4271AE",
      "brightBlack": "#000000",
      "brightBlue": "#4271AE",
      "brightCyan": "#3E999F",
      "brightGreen": "#718C00",
      "brightPurple": "#8959A8",
      "brightRed": "#C82829",
      "brightWhite": "#FFFFFF",
      "brightYellow": "#EAB700",
      "cyan": "#3E999F",
      "foreground": "#4D4D4C",
      "green": "#718C00",
      "name": "Tomorrow",
      "purple": "#8959A8",
      "red": "#C82829",
      "white": "#FFFFFF",
      "yellow": "#EAB700"
    }
  ],

    // Add any keybinding overrides to this array.
    // To unbind a default keybinding, set the command to "unbound"
    "keybindings": []
}

```



## Reference

1. <https://docs.microsoft.com/en-us/windows/wsl/initialize-distro>
2. <https://docs.microsoft.com/en-us/windows/wsl/install-win10>
3. <https://docs.microsoft.com/en-us/windows/wsl/wsl2-install>
4. <https://insider.windows.com/en-us/how-to-pc/>

   ## 

