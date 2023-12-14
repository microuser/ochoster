# ochoster
A lab report with procedure and observations during the learning process by building of a raspberry pi cluster, of rpi4B, rpi4, cm4.
Ocho is spanish for 8. And it is a silent computer like a toaster. Thus; Ocho-Toaster shortened to ochoster. The secret contained within the Ocho(tm) techniques contained within this document are to be revealed. 

# Equipment
Apple Macintosh, M1 16GB, Sonoma 14.1.2
Raspberry Pi Seeed Studio CM4 

# Procedure

##Setup project.
Have fun creating this boilterplate and setting  the License and stats for github to track this project.

## Words 
A very nice guide was reviewed for what I should expect. I'm particularrly confused by the emmc and sdcard. I think I need to visually verify.
-

### A review of birds eyeview over ubuntu https://www.waveshare.com/wiki/CM4_Openwrt onto a Raspberry Pi CM4 Seeed router.
- https://www.waveshare.com/wiki/CM4_Openwrt
### A review of some old nix code for not my situations; yet relivent. 
- https://github.com/pinpox/nixos-raspberrypi-router

### some nix pi?
- https://ipetkov.dev/blog/nixos-on-the-pibox/
### A review of an online discussion bears fruit.
Read the following taken from site...

```txt
I run NixOS on a couple Pi 4s. The trick to avoiding those system hangs
 is to build the system closure on a more powerful machine and then
nixos-rebuild --target-host it to the Pi. It turns out that evaluating
and building Nix expressions takes a lot of resources, and the Pis often
can't do it.
For installation, you can build an SD card image on a
different host as well, and avoid using the installer entirely.
```

implies that what I want is a nixos computer with enough cpu and ram to complete a nixos-rebuild. I expect little pushback; all my pi are 4GB or 8GB. I heed the warning of this wind, such that we do not sail headstrong into the wind.

#### Step -1, because of setbacks.
Get nixos on a system with enough ram to be confortable. Make sure you have a sd writer around.

I've contemplated that I would like to avoid using brew or nix on the Mac, because python and other nasties in my userspace. But rather use a enumerator, or emulator to create a fast compiler virtual machine. I would need network storage for this. Interesting. It seems choices for compilation box are 1) Macos with emulator of raspberry pi. I don't like macs and USB though, but networks are ok.  2) a linuxbox with dedicated nixos build. 3) some clustered vm that you start and writes. hard mode to bootstrap. But could be done with pxe booting.... 

Some setbacks occur during the writing of this article. Two old computers have become unbootable recently. So a switch of hardware is in order. A changing development environment is a new consideration. 
A seeed studio is found with running emmc boot.  A debian bullseye install was found to be fresh, and unused. Although the brave repository needed a removal from the /etc/apt/sources.d folders. 


The default install using debian is outdated. Going to attempt a dist-upgrade, since it might be rolling as I have very litle installed and configured. 
```sh 
sudo apt-get dist-upgrade && sudo apt-get update && sudo apt-get upgrade
``` 

I download the installer script from the website 

```sh 
curl -L https://nixos.org/nix/install > ~/nix.sh
```
 to download the file. I then make it execuitable. 
 ```sh
 sudo chmod +x nix.sh
```
. I then run it in with the daemon parameter. 
```sh
sh sudo ~/nix.sh --daemon
```

I do the install, while enabling flakes ```nix search``` .  I run the following command to enable flakes 
```sh 
mkdir ~/.config -p && mkdir ~/.config/nix && \
   ( echo "experimenal-features = nix-command flakes" > ~/.config/nix/nix.conf ) \
   && echo success || echo failed

```

I restart my system. Then attempt ```nix search nixpkgs tutor vi```to which the CPU gets cooking hot at 30% usage. The 4GB, or specificially 3794MB available might be a concern. A fan was placed on the heat spreader and fins. The system is at max memory and crashes, until the system stops responding. It looks fully locked up. Perhaps I need to specify a swap. Lets restart and attempt that again. For reference, I suggest that 4GB of ram is not enough. I will adjust my own approach again.

```hint
today i learned that 4GB is not enough ram for nix flakes.
```



