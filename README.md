# Turtlebeach-Stealth-Pro-Pipewire-Config
This config allows the Turtlebeach Stealth Pro headset to show as two devices to allow for proper usage of it's chat and game mix. 

## Setup:
  This file shares the same directory structure as where the files should go, for example `etc/asound.conf` would go in `/etc/asound.conf` (or optionally the appropriate the local directory equivalent[asound.conf would be either `~/.asoundrc` or `~/.config/asound.conf`])
   
This project contains three files, one required and two optional but recommended files:
  * Required
    1. `etc/pipewire/pipewire.conf.d/turtlebeach_dual_output.conf` This file actually splits the two devices so they appear in the audio manager as two separate outputs.
  * optional
    1. `etc/udev/rules.d/99-stealthpro.rules` which statically assigns the headset to a device named TBStealthPro
    1. `etc/asound.conf` which will assign convert the two subdevices that use the same device name, to two separate named devices stealthpro_game and stealthpro_chat for easier labeling. 
## Applying Config

  After Configuring the files, rebooting is the best way to test if it works right, but you can also potentially do the following commands(modify to match existing system setup):
  
   1. sudo udevadm control --reload-rules
   1. sudo udevadm trigger
   1. systemctl --user restart pipewire pipewire-pulse wireplumber

  
  ## Hardcoded Setup(Not Recommended)
  If you only have one audio device, or if your devices don't change indexes every boot and want to skip the two optiona files you can do `aplay -l` and then set the both `api.alsa.path` variables in `etc/pipewire/pipewire.conf.d/turtlebeach_dual_output.conf` to their appropriate subdevices
   ```
  **** List of PLAYBACK Hardware Devices ****
card 0: Xbox [Stealth Pro Xbox], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Xbox [Stealth Pro Xbox], device 1: USB Audio [USB Audio #1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
For example in this output, the two paths would be `hw:0,0` and `hw:0,1`
