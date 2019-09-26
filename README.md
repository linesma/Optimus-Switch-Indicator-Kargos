# Optimus-Switch-Kargos-Manjaro
Indicator for Optimus-Switch in KDE using the Kargos Widget


![Optimus-Switch-Indicator-Argos-Manjaro](https://github.com/linesma/Optimus-Switch-Indicator-Argos-Manjaro/blob/master/screenshots/optimus-switcher-intel.jpg)     ![Optimus-Switch-Indicator-Argos-Manjaro](https://github.com/linesma/Optimus-Switch-Indicator-Argos-Manjaro/blob/master/screenshots/optimus-switcher-nvidia.jpg)

This is a fork of argos-indicator-nvidia-prime by cyberalex4life located here: https://github.com/cyberalex4life/argos-indicator-nvidia-prime

It has been updated to switch between the nVidia and Intel graphics cards on Optimus laptops running Manjaro KDE by using the Optimus-Switch program by dglt1 located here: https://github.com/dglt1/optimus-switch-sddm

This is a "port" of my Optimus-Switch-Indicator-Argos-Manjaro, located here: https://github.com/linesma/Optimus-Switch-Indicator-Argos-Manjaro to KDE using the Kargos widget. Kargos is a port of the Argos Extnsion for Gnome to KDE. This projest can be found here: https://github.com/lipido/kargos

Thank you to the authors of all the programs used here.

#### Requirements
- [Kargos](https://github.com/lipido/kargos) Kargos Plasma Widget.
- Optimus-Switch-SDDM located here: https://github.com/dglt1/optimus-switch-sddm
- [pkroot](https://github.com/cyberalex4life/pkroot) - minimum already provided in this repository

#### Installation
Install [Optimus-Switch-SDDM](https://github.com/dglt1/optimus-switch-sddm)

Install [Kargos](https://github.com/lipido/kargos) Plasma widget. You can also install this widget directly from yoour desktop by choosing "Get New Widgets".

Create directory `~/.local/share/icons` if it does not exist:
```
! [ -d "~/.local/share/icons" ] && mkdir --parents ~/.local/share/icons || trueg
```

Then:
```
git clone https://github.com/linesma/Optimus-Switch-Indicator-Argos-Manjaro.git
cd Optimus-Switch-Indicator-Argos-Manjaro

# copy icons
cp -v icons/* ~/.local/share/icons/

# copy 'optimus-switcher.sh' to 'argos' folder
cp -v optimus-switcher.sh ~/.config/argos/

# backup the default Argos configuration
cp ~/.config/argos/argos.sh ~/Documents

# delete the default Argos configuration
rm ~/.config/argos/argos.sh

# change the permissions of optimus-switcher.sh so Argos can read it
sudo chmod +777 ~/.config/argos/optimus-switcher.sh

# copy polkit policy in place
sudo cp org.freedesktop.policykit.pkexec.prime-select.policy /usr/share/polkit-1/actions/

# copy pkroot to '/usr/local/bin' and make sure it is executable
sudo cp pkroot /usr/local/bin
sudo chmod a+x /usr/local/bin/pkroot
```
#### Uninstall
```
# remove icons
rm ~/.local/share/icons-to-delete/{nvidia-active-symbolic.svg,nvidia-inactive-symbolic.svg,prime-indicator-intel.svg,prime-indicator-intel-symbolic.svg,prime-indicator-nvidia.svg}

# remove policy
sudo rm org.freedesktop.policykit.pkexec.prime-select.policy /usr/share/polkit-1/actions/

# remove argos extension script
rm ~/.config/argos/optimus-switcher.sh

# remove pkroot script
sudo rm /usr/local/bin/pkroot

```
Then uninstall Argos if you don't need it anymore.
