# Development Environment

This repository contains a summarized tutorial for setting up my development environment with WSL, Chocolatey, Zsh, Oh My Zsh, NVM (Node Version Manager), and various productivity tools. Below are the detailed steps for setting up the environment and recommended extensions for VSCode.

## Table of Contents

1. [Requirements](#requirements)
2. [Install WSL](#install-wsl)
3. [Install Chocolatey](#install-chocolatey)
4. [Install Hyper](#install-hyper)
5. [Update Linux System (WSL)](#update-linux-system-wsl)
6. [Install Zsh and Oh My Zsh](#install-zsh-and-oh-my-zsh)
7. [Install and Configure NVM](#install-and-configure-nvm-node-version-manager)
8. [Install Powerlevel10k Theme](#install-powerlevel10k-theme)
9. [VSCode Extensions](#vscode-extensions)

## Requirements

Before starting the setup, make sure you have the following items:

- **Windows 10 or 11** (for using WSL)
- **Hyper** (recommended terminal for WSL)
- **Git**
- **VSCode**
- **WSL 2** (Windows Subsystem for Linux)

## Install WSL

1. **Enable WSL and Virtual Machine Platform:**

    In PowerShell (as Administrator), run the following commands:

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
    ```

    Restart the computer after running these commands.

2. **Install a Linux Distribution:**

    - After installing WSL, you can install a Linux distribution from the Microsoft Store (e.g., Ubuntu).

3. **Update WSL to version 2 (if not automatically done):**

    Run the command:

    ```bash
    wsl --set-default-version 2
    ```

4. **Initial Setup:**

    - After installation, open your Linux distribution and configure it as needed (username, password, etc.).

## Install Chocolatey

In PowerShell (as Administrator), run:

```powershell
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## Install Hyper

**Hyper** is the recommended terminal for using with WSL. To install it, follow the steps below:

1. **Download and Install Hyper:**

    - Visit the official [Hyper website](https://hyper.is/) and download the installer for your system.
    - After downloading, follow the installation process.

2. **Configure Hyper to use WSL:**

    - Hyper comes preconfigured to use WSL by default, but you can customize the `.hyper.js` configuration file. To configure the font and shell, follow these steps:

    1. Open the configuration file of Hyper located at `~/.hyper.js`. If you’re unsure where the file is, it’s usually in the user folder, such as `C:\Users\<YourName>\AppData\Roaming\Hyper\`.

    2. Modify the `.hyper.js` file to set the font to **FiraCode Nerd Font** and the shell to **WSL**. Add or modify the following lines:

    ```javascript
    module.exports = {
      config: {
        // Font for the terminal
        fontFamily: 'FiraCode Nerd Font',

        // Set shell to WSL
        shell: 'C:\\Windows\\System32\\wsl.exe',
        shellArgs: ['~'],

        // Other settings you may want to add
        // Example of colors or additional adjustments
      }
    };
    ```

    3. Save the file and restart **Hyper** for the changes to take effect.

### Fonts in Hyper:

To ensure the **FiraCode Nerd Font** is available, you’ll need to install it first. If you don’t have the font installed, follow these steps:

- **Install FiraCode Nerd Font**:
  1. Visit the [Nerd Fonts website](https://www.nerdfonts.com/) and download **FiraCode Nerd Font**.
  2. After downloading, extract the file and install the font on your system.

With these configurations, **Hyper** will be ready to use **FiraCode Nerd Font** and the **WSL** shell, creating a more comfortable environment for terminal-based development.

## Update Linux System (WSL)

In the WSL terminal (Linux), run:

```bash
sudo apt update && sudo apt upgrade -y
```

## Install Zsh and Oh My Zsh

For a more powerful and customizable shell, install **Zsh** and **Oh My Zsh**.

1. **Install Zsh:**

    In the WSL terminal (Linux), run:

    ```bash
    sudo apt install zsh -y
    ```

2. **Install Oh My Zsh:**

    In the WSL terminal (Linux), run:

    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    ```

## Install and Configure NVM (Node Version Manager)

**NVM** is an essential tool for managing different versions of Node.js. To install and configure it, follow these steps:

1. **Install NVM:**

    In the WSL terminal (Linux), run:

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.0/install.sh | bash
    ```

2. **Configure NVM in Zsh:**

    After installation, add the NVM configurations to your `~/.zshrc` file:

    ```bash
    echo "export NVM_DIR=\"$HOME/.nvm\"\n[ -s \"$NVM_DIR/nvm.sh\" ] && . \"$NVM_DIR/nvm.sh\"\n[ -s \"$NVM_DIR/bash_completion\" ] && . \"$NVM_DIR/bash_completion\"" >> ~/.zshrc
    source ~/.zshrc
    ```

## Install Powerlevel10k Theme

To improve the terminal appearance, install **Powerlevel10k**.

1. **Install Powerlevel10k:**

    In the WSL terminal (Linux), run:

    ```bash
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    ```

2. **Change the theme in Zsh:**

    Edit the `~/.zshrc` file and set the theme to `powerlevel10k/powerlevel10k`:

    ```bash
    ZSH_THEME="powerlevel10k/powerlevel10k"
    ```

3. **Apply the changes:**

    To apply the changes, reload Zsh:

    ```bash
    source ~/.zshrc
    ```

## VSCode Extensions

Here are my main extensions for VSCode, organized by functionality:

### Essential

- **Apc Customize UI++**: Advanced customization of the VSCode interface.
- **WSL**: Support for integrating WSL directly into VSCode.

### Theme/Decoration

- **Houston** (modified): This theme has been customized to better suit my visual preferences. You can check the modified file [here](https://github.com/Leugz/Setup/blob/main/houston.json) for details on the changes. You can find the Houston theme in the official VSCode themes repository or check out the [official Houston GitHub repository](https://github.com/withastro/houston-vscode)
- **Symbols**: For custom icons and visual improvements.

### Key Functions

- **Auto Close Tag**: Automatically closes HTML/JSX tags.
- **Auto Rename Tag**: Automatically renames opening/closing HTML/JSX tags.
- **Highlight Matching Tag**: Highlights the matching tag while editing.
- **Auto Import**: Automatically adds imports for modules and packages.
- **AutoPrefixer**: Automatically adds CSS prefixes.
- **Color Highlight**: Highlights colors in the code.

### General

- **Discord Presence**: Shows your activity in Discord.
- **GitLens — Git supercharged**: Enhances Git integration in VSCode.
- **ESLint**: Linter for JavaScript and TypeScript.
- **Prettier**: Auto-formatting of code.
- **Pretty TypeScript Errors**: Improves TypeScript error readability.

### Support

- **HTML CSS Support**: Full support for HTML and CSS.
- **JavaScript and TypeScript Nightly**: Latest versions of JavaScript/TypeScript.

---

In addition to the extensions, the `settings.json` file of VSCode also contains my personal configurations. The file I share is a customization based on the settings of **Diego Fernandes**, an instructor at **Rocketseat**. You can view the file and adapt it as needed by accessing it [here](https://github.com/Leugz/Setup/blob/main/settings.json).
