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

### 4 ### Gnome-Disk-Utility ###

