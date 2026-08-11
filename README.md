# Nice-to-have-Linux-Stuff

### 1 ### installing YAY and PARU ###
YAY:    sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si

PARU:   sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/paru.git && cd paru && makepkg -si


### 2 ### installing Flatpak and Gnome Software ###

sudo pacman -S flatpak gnome-software
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
gnome-software --replace &

### 3 ### installing Bibata Cursor ###

Step 1: yay -S bibata-cursor-theme-bin

Step 2: wget https://raw.githubusercontent.com/J3sven/wayland-cursor-theme-utility/refs/heads/main/cursor-utility.sh -O cursor-utility.sh && chmod +x cursor-utility.sh

Step 3: ./cursor-utility.sh

### 4 ### installing Noctalia Shell ###

yay -S noctalia-shell

### 5 ### Display layout, Keyboard Layout and making Noctalia v4 to an auostart Application ###

mkdir -p ~/.config/labwc && echo 'setxkbmap de; qs -c noctalia-shell &; wlr-randr --output DP-1 --mode 2560x1440@179.959000 --scale 1 --pos 1440,560 --output HDMI-A-1 --mode 2560x1440@59.951000 --transform 90 --scale 1 --pos 0,0' > ~/.config/labwc/autostart && chmod +x ~/.config/labwc/autostart

### 6 ### installing a Wallpaper Collection /Dokumente/Wallpaper ###

Step 1: sudo pacman -S git-lfs && git lfs install
Step 2: mkdir -p ~/Dokumente/Wallpaper && git clone https://github.com/BlackoneBc/walls-catppuccin-mocha.git && cd walls-catppuccin-mocha && git lfs install && git lfs pull && cp *.png *.jpg ~/Dokumente/Wallpaper/ && cd .. && rm -rf walls-catppuccin-mocha



