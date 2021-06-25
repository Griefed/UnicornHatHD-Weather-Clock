# UnicornHat HD Weather Clock

[[_TOC_]]

Binary clock with weather API integration designed for Pimoroni's UnicornHat HD.

Displays hours, minutes and seconds in binary format, as well as providing weather status (rainy, cloudy, sunny, etc), humidity and temperature.

Humidity is shown on the top bar in units of 10%; temperature is shown on the bottom bar in units of 5degC.

## Dependencies
Requires [pytz](https://pypi.python.org/pypi/pytz), [pyowm](https://github.com/csparpa/pyowm) and [unicornhathd](https://github.com/pimoroni/unicorn-hat-hd)

## Usage
In order for the weather API to function properly you'll need to sign up and get an API key from openweathermap.org and insert it on line 11 of weatherclock.py. Next, enter your location on line 12.

If you want to use a different timezone, enter that on line 16.

## Run after boot
If you want to run the clock right after booting up your Pi, 
copy unicornhathd.timer && unicornhathd.service to /etc/systemd/system
followed by 
sudo systemctl enable unicornhathd.timer
##### Note that the service expects the file to be in /home/pi/Downloads/weatherclock/


## Automate the whole thing because we're lazy
```
#!/bin/bash
#Downloads the clock and enables run after boot

cd ~/Downloads && git clone https://github.com/Griefed/UnicornHatHD-Weather-Clock.git ./weatherclock
sudo cp ~/Downloads/weatherclock/unicornhathd.timer /etc/systemd/system/ && sudo cp ~/Downloads/weatherclock/unicornhathd.service /etc/systemd/system/
sudo systemctl enable unicornhathd.timer
print("To test, run: sudo reboot")
```

