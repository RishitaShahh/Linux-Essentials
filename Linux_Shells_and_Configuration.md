# Linux Shells and Configuration

## Overview

In Linux, a shell is a command-line interface that allows users to interact with the operating system. It acts as an intermediary between the user and the kernel, enabling the execution of commands, scripting, and automation. Various shells exist, each offering unique features and capabilities.

---

## Common Linux Shells

### 1. **sh (Bourne Shell)**

- Designed for executing commands and basic scripting.
- Minimal interactive features.
- Supports variables, loops, conditionals, and redirection.

### 2. **Bash (Bourne Again Shell)**

- Default shell in most Linux distributions.
- Enhances `sh` with additional features.
- Supports scripting, command history, tab completion, and more.

### 3. **Ksh (Korn Shell)**

- Combines features of `sh` and `csh` (C Shell).
- Known for scripting capabilities and efficiency in programming environments.

### 4. **Tcsh (TENEX C Shell)**

- An improved version of `csh`.
- Provides command-line editing and spelling correction.

### 5. **Fish (Friendly Interactive Shell)**

- Focuses on user-friendliness and interactive usage.
- Features syntax highlighting, auto-suggestions, and built-in commands.

### 6. **Zsh (Z Shell)**

- Highly customizable and powerful.
- Features shared history, spell-checking, themes, and Bash compatibility.

### 7. **Dash (Debian Almquist Shell)**

- Lightweight and optimized for scripting efficiency.
- Used as the default `/bin/sh` in some Linux distributions.

---

## Checking Installed Shells

- To display a list of installed shells:
  ```bash
  cat /etc/shells
  ```
- To check the current default shell:
  ```bash
  echo $SHELL
  ```

---

## Package Management Commands

### Searching and Installing Packages with `yum`

1. **Search for Bash-related packages:**
   ```bash
   yum search Bash
   ```
2. **Install all Bash-related packages:**
   ```bash
   yum install Bash*
   ```

#### Resolving Missing Packages in `yum search`

If some packages are not listed in `yum search`, try:

1. **Enable additional repositories:**
   ```bash
   yum install epel-release
   ```
2. **Update repository cache:**
   ```bash
   yum makecache
   ```
3. **Perform a broader search:**
   ```bash
   yum search color prompt
   ```

---

## Installing and Configuring `grc` (Generic Colourizer)

`grc` is a tool that enhances terminal output by adding color to command results, making them easier to read.

### **Installation Steps**

1. ***Navigate to the Downloads directory:***
   ```bash
   cd Downloads
   ```
2. ***Download the source code:***
   ```bash
   wget https://github.com/garabik/grc/archive/refs/tags/v1.13.tar.gz
   ```
3. ***Extract the downloaded archive:***
   ```bash
   tar -xvf v1.13.tar.gz
   ```
4. ***Remove the archive to save space:***
   ```bash
   rm -rf v1.13.tar.gz
   ```
5. ***Move the extracted folder to `/opt/` for system-wide installation:***
   ```bash
   mv -v grc-1.13 /opt/
   ```
6. ***Navigate to the installation directory:***
   ```bash
   cd /opt/grc-1.13
   ```
7. ***Run the installation script:***
   ```bash
   ./install.sh
   ```

### **Using `grc`**

- Example usage:
  ```bash
  grc ping 8.8.8.8
  ```

### **Enable Persistent Colorized Output**

1. **Copy the `grc.sh` script to `/etc`:**
   ```bash
   cp -v /opt/grc-1.13/grc.sh /etc
   ```
2. **Edit `.bashrc` to enable aliases:**
   ```bash
   vim ~/.bashrc
   ```
3. **Add the following lines to `.bashrc`:**
   ```bash
   GRC_ALIASES=true
   [[ -s "/etc/profile.d/grc.sh" ]] && source /etc/grc.sh
   ```
4. **Apply the changes:**
   ```bash
   source ~/.bashrc
   ```

---

## Installing and Configuring Zsh

### **Installation Steps**

1. **Install Zsh:**
   ```bash
   yum install zsh*
   ```
2. **Verify installation:**
   ```bash
   cat /etc/shells
   ```
3. **Edit the `.zshrc` configuration file:**
   ```bash
   vim /root/.zshrc
   ```
4. **Download and apply the configuration from GitHub:**
   ```bash
   wget -O ~/.zshrc https://github.com/InfoSecWarrior/Kali-Linux-Configuration/blob/main/.zshrc
   ```
5. **Add additional environment variables and settings:**
   ```bash
   echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> ~/.zshrc
   echo 'export GOROOT=/usr/local/go' >> ~/.zshrc
   echo '[[ -s "/etc/grc.zsh" ]] && source /etc/grc.zsh' >> ~/.zshrc
   ```
6. **Change the default shell to Zsh:**
   ```bash
   chsh -s $(which zsh)
   ```
7. **Apply the new configuration:**
   ```bash
   source ~/.zshrc
   ```

---

## Conclusion

This guide covers the various Linux shells, their features, and how to install and configure `grc` and `zsh`. By following these steps, you can enhance your command-line experience with colorized output and a feature-rich shell environment.

