
# Personal DWM config

## Required software
```sudo apt install build-essential libx11-dev libxft-dev libxinerama-dev libfreetype6-dev libfontconfig1-dev```

## After installation

### Create a xsession for DWM
`/usr/xsessions/dwm.desktop`
```
[Desktop Entry]
Name=dwm
Comment=dynamic window manager
Exec=dwm
Icon=dwm
Type=Application
```

### Enable touchpad
Create a file on `/etc/X11/xorg.conf.d/30-touchpad.conf`
```
Section "InputClass"
    Identifier "touchpado catchall"
    Driver "libinput"
    Option "Tapping" "on"
EndSection
```

### Enable xbacklight commands
Create a file on `/etc/X11/xorg.conf.d/40-backlight.conf`
```
Section "Device"
    Identifier  "Intel Graphics" 
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection
```

## Diffs from original dwm-6.2

- MODKEY = windows button
- Can open browser on any tag

## Changed bindings

- MOD|Shift	+ w - nmtui
- MOD 	  	+ d - dmenu_run
- MOD 		+ q - killclient
- MOD 		+ e - lf
- MOD|Shift	+ e - htop
- MOD		+ p - slock
- Brightness up	    - xbacklight -inc 5
- Brightness down   - xbacklight -dec 5
- Audio up	    - pactl set-sink-volume <> +5%
- Audio down	    - pactl set-sink-volume <> -5%





dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.


Requirements
------------
In order to build dwm you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
