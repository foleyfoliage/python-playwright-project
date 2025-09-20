#!/bin/bash
# Full Environment Setup and Recommended Project Structure for Python Playwright Project on Debian 12

set -e  # Exit immediately if any command fails

echo "=== Updating package lists ==="
sudo apt update

echo "=== Installing Snap ==="
sudo apt install -y snapd

echo "=== Enabling classic Snap support ==="
sudo snap install core
sudo snap refresh core

echo "=== Installing PyCharm Community Edition ==="
sudo snap install pycharm-community --classic
# Optional: sudo snap install pycharm-professional --classic

echo "=== Installing Homebrew (Linuxbrew) ==="
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

echo "=== Installing Python3 and pip ==="
sudo apt install -y python3 python3-pip

echo "=== Checking Python and pip versions ==="
python3 --version
pip3 --version

# -------------------------
# Recommended Project Directory Structure
# -------------------------
# python-playwright-project/
# ├── tests/                  # Your test cases
# │   ├── test_login.py
# │   ├── test_checkout.py
# │   └── ...
# ├── pages/                  # Page Object Models
# │   ├── login_page.py
# │   ├── home_page.py
# │   └── ...
# ├── utils/                  # Utility/helper functions
# │   ├── logger.py
# │   ├── config_reader.py
# │   └── ...
# ├── reports/                # Test reports
# ├── screenshots/            # Screenshots on failure
# ├── requirements.txt        # Python dependencies
# ├── playwright.config.py    # Playwright configuration
# ├── pytest.ini              # Pytest configuration
# └── .gitignore              # Ignored files

echo "=== Creating Python project directory and virtual environment ==="
PROJECT_DIR=~/PycharmProjects/python-playwright-project
mkdir -p "$PROJECT_DIR"
cd "$PROJECT_DIR"

python3 -m venv venv

echo "=== Activating virtual environment ==="
source venv/bin/activate

echo "=== Installing project dependencies ==="
if [ -f requirements.txt ]; then
    pip install -r requirements.txt
else
    echo "requirements.txt not found! Creating a default one..."
    cat <<EOL > requirements.txt
playwright
pytest
pytest-html
pytest-xdist
EOL
    pip install -r requirements.txt
fi

echo "=== Creating standard directories ==="
mkdir -p tests pages utils reports screenshots

echo "=== Installing Playwright browsers ==="
python -m playwright install

echo "=== Setup Complete ==="
echo "Activate your virtual environment with: source venv/bin/activate"
echo "Follow the recommended project structure for organizing tests, pages, and utilities."
echo "Run tests using pytest or your preferred method."
