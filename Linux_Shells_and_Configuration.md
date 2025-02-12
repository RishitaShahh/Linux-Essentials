# Configuring `grc` and `zsh` in Linux

## Overview

This guide provides step-by-step instructions on installing and configuring `grc` (Generic Colourizer) and `zsh` (Z Shell) to enhance your Linux terminal experience with colorized output and advanced shell features.

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

This guide covers the installation and configuration of `grc` and `zsh` to enhance the Linux command-line experience. By following these steps, you can enable colorized command output and leverage the advanced features of `zsh` for better usability and efficiency.

