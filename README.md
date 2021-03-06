# pi_video_looper
Application to turn your Raspberry Pi into a dedicated looping video playback device, good for art installations, information displays, or just playing cat videos all day.

Video_looper guide: https://learn.adafruit.com/raspberry-pi-video-looper?view=all

Configuration of Pi: https://www.raspberrypi.org/documentation/configuration/

### **REMEMBER TO SET THE CORRECT LOCAL TIME (Timezone) ON THE RASPBERRY PI**
Local time and keyboard-layout can be changed using the following code
```
sudo raspi-config
```
Use the following to set date and time, if it does not automatically (often because of no internet connection)
```
sudo date -s "23 May 2018 10:30:00"
```

## Installation
Update and clone repository
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -y git
git clone https://github.com/itblf/pi_video_looper.git
```

Install, requires internet
```
cd pi_video_looper
sudo ./install.sh
```

Program should automatically start loading video-files from USB.

## Usage
Stop/start looper from SSH
```
sudo supervisorctl stop video_looper
```

To disable it entirely to not start on boot
```
cd pi_video_looper
sudo ./disable.sh
```
To enable again, simply run install script
```
sudo ./install.sh
```

## Change time-interval for volume-ON
In file: Adafruit_Video_Looper/video_looper.py change the variables on line 71-72
```
_START_TIME = "08:00"
_END_TIME = "20:00"
```
Reinstall may be necessary after changing the times.

## Debugging
Logs and standard error output can be seen with the following:
```
sudo supervisorctl tail -f video_looper
sudo supervisorctl tail -f video_looper stderr
```

## Remote Access
To utilize remote acces use https://remot3.it
- Setup on rPi: https://remot3it.zendesk.com/hc/en-us/articles/115006015367-Installing-the-remot3-it-weavedconnectd-daemon-on-your-Raspberry-Pi
- Using SSH/SFTP: https://remot3it.zendesk.com/hc/en-us/articles/115000150232-Using-remot3-it-with-Third-Party-SSH-SCP-Applications
