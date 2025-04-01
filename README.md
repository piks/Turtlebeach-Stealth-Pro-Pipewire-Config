# Turtlebeach-Stealth-Pro-Pipewire-Config
This config allows the Turtlebech Stealth Pro headset to show as two devices to allow for proper usage of it's chat and game mix. 


Setup:
  You need to change the api.alsa.path for each output to be the card number + device number listed in aplay -l for your devices, for example mine shows:
  ```
  **** List of PLAYBACK Hardware Devices ****
card 0: Xbox [Stealth Pro Xbox], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Xbox [Stealth Pro Xbox], device 1: USB Audio [USB Audio #1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
Which would be hw:0,0 and hw:0,1. 

If these numbers constantly change on you, you can set up a udev rule to force it to be a specific index. 
