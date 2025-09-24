# Commands for configuring B200 to B210
# Back up original B210 fpga firmware
sudo cp /usr/share/uhd/images/usrp_b210_fpga.bin /usr/share/uhd/images/usrp_b210_fpga.bin-back
# Copy new fpga firmware for UHD version
sudo cp b210_fpga.bin /usr/share/uhd/images/usrp_b210_fpga.bin
# Modify board to run as a B210
sudo ./usrp_burn_mb_eeprom --args="type=b200" --values="product=2"

# Commands for returning B210 to B200
# Modify board back to a B200
sudo ./usrp_burn_mb_eeprom --args="type=b200" --values="product=1"

# Utility commands
# Find usrp_burn_mb_eeprom
find
# Show current UHD version and fpga firmware path
uhd_usrp_probe
