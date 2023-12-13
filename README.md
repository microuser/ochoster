# ochoster
A lab report with procedure and observations during the learning process by building of a raspberry pi cluster, of rpi4B, rpi4, cm4.
Ocho is spanish for 8. And it is a silent computer like a toaster. Thus; Ocho-Toaster shortened to ochoster. The secret contained within the Ocho(tm) techniques contained within this document are to be revealed. 

#Equipment
Apple Macintosh, M1 16GB, Sonoma 14.1.2

#Procedure

##Setup project.
Have fun creating this boilterplate and setting  the License and stats for github to track this project.

##Re
A very nice guide was reviewed for what I should expect. I'm particularrly confused by the emmc and sdcard. I think I need to visually verify.
-

### A review of birds eyeview over ubuntu https://www.waveshare.com/wiki/CM4_Openwrt onto a Raspberry Pi CM4 Seeed router.
- https://www.waveshare.com/wiki/CM4_Openwrt
###A review of some old nix code for not my situations; yet relivent. 
- https://github.com/pinpox/nixos-raspberrypi-router

###A review of an online discussion bears fruit.
Read the following taken from site...
```txt
I run NixOS on a couple Pi 4s. The trick to avoiding those system hangs is to build the system closure on a more powerful machine and then nixos-rebuild --target-host it to the Pi. It turns out that evaluating and building Nix expressions takes a lot of resources, and the Pis often can't do it.
For installation, you can build an SD card image on a different host as well, and avoid using the installer entirely.
```
implies that what I want is a nixos computer with enough cpu and ram to complete a nixos-rebuild. I expect little pushback; all my pi are 4GB or 8GB. I heed the warning of this wind, such that we do not sail headstrong into the wind.

####Step -1, because of setbacks.
Get nixos on a system with enough ram to be confortable. Make sure you have a sd writer around.

I've contemplated that I would like to avoid using brew or nix on the Mac, bcause python and other nasties in my userspace. But rather use a enumerator, or emulator to create a fast compiler virtual machine. I would need network storage for this. Interesting. It seems choices for compilation box are 1) Macos with emulator of raspberry pi. I don't like macs and USB though, but networks are ok.  2) a linuxbox with dedicated nixos build. 3) some clustered vm that you start and writes. hard mode to boot strap. But could be done with pxe booting.... 





