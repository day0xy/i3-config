# i3-config  :)



| [Install](#Install)         |
| --------------------------- |
| [Screenshot](Screenshot)    |
| [Shortcuts](Shortcuts)      |
| [Problem fix](#Problem fix) |

```
Pure i3-gaps with polybar,without DE.
```

```
Modified from someone's dotfiles 
```

```
:)
```

with round  corners and terminal blur,screenshots are following





## Install

To install,following the steps:

* move `.*sh` to your $HOME
* move `config folders` to $HOME/.config/
* move `.wallpaper and /wallpaper_nsfw` to $HOME

and:

copy `content` of `picom.conf` to `/etc/xdg/picom.conf`





## Softwares

for archlinux user

```
yay -S i3-gaps picom breeze-icons lxappearance-gtk3 qt5ct nerd-fonts-complete

yay -S termite feh rofi ranger ueberzug dolphin  polybar twmn-git xidlehook

yay -S betterlockscreen networkmanager-dmenu-git  imagemagick  xfce4-power-manager xfce4-clipman-plugin

yay -S polkit-kde-agent  ark autotiling
```





## Screenshot

![](screenshots/Screenshot_20221209_122553.png)



![](screenshots/Screenshot_20221209_120219.png)

## Shortcuts

| ctrl+$mod+s | SFW mode  |
| ----------- | --------- |
| ctrl+$mod+n | NSFW mode |
| $mod+return | terminal  |
| alt+e       | dolphin   |

two mode,check wallpaper folders

##  Problem fix

some problems fix

### 1.terminal font

```
yay -S ttf-hack
```

### 2.polybar

[miscphone config]

check `.config/polybar/config`

```
[module/mic-volume]
type = custom/script
interval = 1
format = Mic:<label>
exec = bash ~/.config/polybar/mic-volume/mic-volume.sh show-vol alsa_input.pci-0000_04_00.6.analog-stereo

; Control actions (using pactl)
; Example supplying the name of the source
click-left = bash ~/.config/polybar/mic-volume/mic-volume.sh mute-vol alsa_input.pci-0000_04_00.6.analog-stereo
; Example supplying the index of the source
scroll-up = bash ~/.config/polybar/mic-volume/mic-volume.sh inc-vol 
; Example leaving the MICROPHONE_NAME blank and using the default source
scroll-down = bash ~/.config/polybar/mic-volume/mic-volume.sh dec-vol 
```

you can delete `alsa_input.pci-0000_04_00.6.analog-stereo`  to use default 



or:

```
pactl list | grep input 
```

get you device id

```
Name: alsa_input.pci-0000_04_00.6.analog-stereo
```

### 3.dolphin inner terminal

```
The default terminal is konsole,but it has white border,now follow steps to change to termite
```

`check` https://wiki.archlinux.org/title/Dolphin#Open_terminal to change it.

### 4.dolphin icons 

Ways to change dolphin icon themes

```
yay -S qt5ct
```

```
$sudoedit /etc/environment
```

add these

```
export QT_QPA_PLATFORMTHEME="qt5ct"
```

or

add `export QT_QPA_PLATFORMTHEME="qt5ct"` to ~/.xprofile

```
reboot
```



```
yay -S flat-remix
```



open qt5ct with rofi



you can change icon theme through the GUI 

![](screenshots/Screenshot_20221207_170847.png)

### 5.touchpad

#### 

```
yay -S xf86-input-synaptics
```

```
sudoedit /etc/X11/xorg.conf.d/70-synaptics.conf
```



```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"

        Option "TapButton1" "1"            #单指敲击产生左键事件
        Option "TapButton2" "3"            #双指敲击产生中键事件

        Option "VertEdgeScroll" "on"       #滚动操作：横向、纵向、环形
        Option "VertTwoFingerScroll" "on"
        Option "VertScrollDelta"          "-111"	#natural scrolling
        Option "HorizScrollDelta"         "-111"
        Option "HorizEdgeScroll" "on"		
        Option "HorizTwoFingerScroll" "on"
        Option "CircularScrolling" "on"  
        Option "CircScrollTrigger" "2"
EndSection

```

### 6.systemtray icon

1.install `lxappearance-gtk3` and `qt5ct`



2.download your icon the to `~/.icons/`



3.open the two programs to set



4.set icon size

edit polybar/config   

```
tray-maxsize = 22
```

###  7.dolphin background

if you like `dark` theme 

when you use  `qt5ct` to change the palette,the dolphin background is white and you can't see the text under icons

to solve it , check the kdeglobals 

```
vim .config/kdeglobals
```

insert these

```
[ColorEffects:Disabled]
ChangeSelectionColor=
Color=56,56,56
ColorAmount=0
ColorEffect=0
ContrastAmount=0.65
ContrastEffect=1
Enable=
IntensityAmount=0.1
IntensityEffect=2

[ColorEffects:Inactive]
ChangeSelectionColor=true
Color=112,111,110
ColorAmount=0.025
ColorEffect=2
ContrastAmount=0.1
ContrastEffect=2
Enable=false
IntensityAmount=0
IntensityEffect=0

[Colors:Button]
BackgroundAlternate=30,87,116
BackgroundNormal=49,54,59
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:Complementary]
BackgroundAlternate=30,87,116
BackgroundNormal=42,46,50
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:Header]
BackgroundAlternate=42,46,50
BackgroundNormal=49,54,59
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:Header][Inactive]
BackgroundAlternate=49,54,59
BackgroundNormal=42,46,50
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:Selection]
BackgroundAlternate=30,87,116
BackgroundNormal=61,174,233
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=252,252,252
ForegroundInactive=161,169,177
ForegroundLink=253,188,75
ForegroundNegative=176,55,69
ForegroundNeutral=198,92,0
ForegroundNormal=252,252,252
ForegroundPositive=23,104,57
ForegroundVisited=155,89,182

[Colors:Tooltip]
BackgroundAlternate=42,46,50
BackgroundNormal=49,54,59
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:View]
BackgroundAlternate=35,38,41
BackgroundNormal=27,30,32
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182

[Colors:Window]
BackgroundAlternate=49,54,59
BackgroundNormal=42,46,50
DecorationFocus=61,174,233
DecorationHover=61,174,233
ForegroundActive=61,174,233
ForegroundInactive=161,169,177
ForegroundLink=29,153,243
ForegroundNegative=218,68,83
ForegroundNeutral=246,116,0
ForegroundNormal=252,252,252
ForegroundPositive=39,174,96
ForegroundVisited=155,89,182
```



