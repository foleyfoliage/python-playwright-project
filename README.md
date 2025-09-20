# Python Playwright Automation Framework

A Python automation framework using Playwright and Pytest, featuring a Page Object Model (POM), test reporting, and organized structure for scalable web UI testing.

---

## Environment Setup on Debian 12

### 1. Install Snap and PyCharm
sudo apt update
sudo apt install -y snapd
sudo snap install core
sudo snap refresh core
sudo snap install pycharm-community --classic
# Optional: sudo snap install pycharm-professional --classic

### 2. Install Homebrew (Linuxbrew)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

### 3. Install Python3 and pip
sudo apt install -y python3 python3-pip
python3 --version
pip3 --version

### 4. Create and Activate Virtual Environment
cd ~/PycharmProjects/python-playwright-project
python3 -m venv venv
source venv/bin/activate

### 5. Install Project Dependencies
pip install -r requirements.txt

Example requirements.txt:
playwright
pytest
pytest-html
pytest-xdist

### 6. Install Playwright Browsers
python -m playwright install

### 7. Run Tests
source venv/bin/activate
pytest
pytest --html=reports/report.html

Notes:
- Keep credentials or sensitive data out of the repo; use environment variables or .env files.
- Organize tests and page objects according to the recommended directory structure for scalability.
- Use conftest.py to define reusable fixtures like browser setup/teardown.
