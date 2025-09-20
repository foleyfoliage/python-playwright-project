Environment Setup on Debian 12

Install Snap (for PyCharm)
# Update package lists
sudo apt update

# Install Snap
sudo apt install snapd

# Enable classic Snap support
sudo snap install core
sudo snap refresh core

# Install PyCharm Community Edition
sudo snap install pycharm-community --classic

Install Homebrew (Linuxbrew)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# Homebrew can be used to install Python, Node.js, and other dependencies easily on Debian.
