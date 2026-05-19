# Alibaba USRP Firmware Guide (B200 ↔ B210)

This repository contains commands for switching a USRP B200 to behave like a B210, and for reverting it back.

## Prerequisites

- UHD tools installed (`usrp_burn_mb_eeprom`, `uhd_usrp_probe`)
- `sudo` access
- Correct FPGA image file (`b210_fpga.bin`)

---

## Convert B200 to B210

1. Back up the original FPGA firmware:

```bash
sudo cp /usr/share/uhd/images/usrp_b210_fpga.bin /usr/share/uhd/images/usrp_b210_fpga.bin-back
```

2. Copy the new FPGA firmware for your UHD version:

```bash
sudo cp b210_fpga.bin /usr/share/uhd/images/usrp_b210_fpga.bin
```

3. Update motherboard EEPROM product value to B210 (`product=2`):

```bash
sudo ./usrp_burn_mb_eeprom --args="type=b200" --values="product=2"
```

---

## Revert B210 back to B200

Set motherboard EEPROM product value back to B200 (`product=1`):

```bash
sudo ./usrp_burn_mb_eeprom --args="type=b200" --values="product=1"
```

---

## Utility Commands

Find `usrp_burn_mb_eeprom` on your system:

```bash
find /usr /usr/local -name usrp_burn_mb_eeprom 2>/dev/null
```

Show current UHD version and image path information:

```bash
uhd_usrp_probe
```
