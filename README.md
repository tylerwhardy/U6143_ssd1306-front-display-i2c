# U6143_ssd1306-front-display-i2c
This runs the required service to use UCTRONICS Ultimate Rack with PoE Functionality for Raspberry Pi 4 OLED display. This was required as a workaround because the vendor software assumes you are running Raspbian which we are not. Instead, we're using Ubuntu 20 or so. We are not using rc.local because that's not how we do things anymore. 

# Update the repos
sudo apt update

# Get your I2C drivers installed and prepare to make some source code
sudo apt install python3-lgpio make gcc

# Get the vendor drivers 
git clone https://github.com/UCTRONICS/U6143_ssd1306.git

# Make vendor drivers
cd /home/ubuntu/U6143_ssd1306/C

make 

chmod +x display

# Validate the display comes on 
sudo ./display 

# Install front-display.service where it belongs in /etc/systemd/system/
sudo mv front-display.service /etc/systemd/system/front-display.service

# Enable service
systemctl enable front-display.service

# Reboot into service
sudo reboot
