# U6143_ssd1306-front-display-i2c
This runs the required service to use UCTRONICS Ultimate Rack with PoE Functionality for Raspberry Pi 4 OLED display. This was required as a workaround because the vendor software assumes you are running Raspbian which we are not. Instead, we're using Ubuntu 20 or so. We are not using rc.local because that's not how we do things anymore. 

# Update the repos
sudo apt update

# Get your I2C drivers installed and prepare to make some source code
sudo apt install python3-lgpio make gcc

# Get the vendor drivers 
git clone https://github.com/UCTRONICS/U6143_ssd1306.git

# Make vendor drivers
cd U6143_SSD1306/C 

make 

# Validate the display comes on 
sudo ./display 

