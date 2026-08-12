# Nice-to-have-Linux-Stuff

### 1. installing YAY and PARU 

YAY
    
    sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
Paru
     
    sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/paru.git && cd paru && makepkg -si


### 2. installing Flatpak and Gnome Software 

    sudo pacman -S flatpak gnome-software gnome-software-plugin-flatpak
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

### 3. installing Bibata Cursor 

    yay -S bibata-cursor-theme-bin
    wget https://raw.githubusercontent.com/J3sven/wayland-cursor-theme-utility/refs/heads/main/cursor-utility.sh -O cursor-utility.sh && chmod +x cursor-utility.sh
    ./cursor-utility.sh

### 4. installing Noctalia Shell 

    yay -S noctalia-shell

### 5. Display layout and making Noctalia v4 to an auostart Application 

    mkdir -p ~/.config/labwc
    qs -c noctalia-shell &; wlr-randr --output DP-1 --mode 2560x1440@179.959000 --scale 1 --pos 1440,560 --output HDMI-A-1 --mode 2560x1440@59.951000 --transform 90     --scale 1 --pos 0,0' > ~/.config/labwc/autostart;
    chmod +x ~/.config/labwc/autostart

### 5.5. Changing Keyboardlayout to "de"

   mkdir -p ~/.config/labwc && echo -e "XKB_DEFAULT_LAYOUT=de\nXKB_DEFAULT_VARIANT=nodeadkeys" >> ~/.config/labwc/environment

### 6.  installing a Wallpaper Collection /Dokumente/Wallpaper

        sudo pacman -S git-lfs && git lfs install
        mkdir -p ~/Dokumente/Wallpaper && \
        git clone https://github.com/BlackoneBc/walls-catppuccin-mocha.git && \
        cd walls-catppuccin-mocha && \
        git lfs install && \
        git lfs pull && \
        cp *.png *.jpg ~/Dokumente/Wallpaper/ 2>/dev/null && \
        cd .. && \
        rm -rf walls-catppuccin-mocha

### 7. Installing and activating a SDDM Theme 

    yay -S --needed sddm-silent-theme 
    sudo sh -c "echo -e '[General]\nInputMethod=qtvirtualkeyboard\nGreeterEnvironment=QML2_IMPORT_PATH=/usr/share/sddm/themes/silent/components/,QT_IM_MODULE=qtvirtualkeyboard\n\n[Theme]\nCurrent=silent' >> /etc/sddm.conf"

Test before reboot!!! 

    cd /usr/share/sddm/themes/silent/ && ./test.sh

### 8. Installing nice to have Flatpak Applications

    flatpak install -y com.brave.Browser
    com.github.IsmaelMartinez.teams_for_linux 
    com.heroicgameslauncher.hgl 
    com.jeffser.Alpaca 
    com.lunarclient.LunarClient
    com.nuclearplayer.Nuclear 
    com.rtosta.zapzap 
    com.spotify.Client
    com.valvesoftware.Steam 
    dev.vencord.Vesktop
    io.github.Geocld.PeaSyo4Desk
    io.github.ecotubehq.player
    io.github.revisto.drum-machine 
    io.github.ungoogled_software.ungoogled_chromium
    io.gitlab.adhami3310.Impression 
    io.missioncenter.MissionCenter 
    org.bluej.BlueJ org.gnome.Decibels 
    org.gnome.Showtime org.gnome.TextEditor
    org.onlyoffice.desktopeditors 
    org.prismlauncher.PrismLauncher 
    org.videolan.VLC 

### 9. Installing Spicetify

    sudo pacman -S --needed unzip
    flatpak kill com.spotify.Client 2>/dev/null
    curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s --
    mkdir -p ~/.config/spicetify
    SPOTIFY_PATH=$(flatpak info com.spotify.Client --show-location 2>/dev/null || echo "")
    if [[ -z "$SPOTIFY_PATH" ]]; then
        echo "Spotify Flatpak nicht gefunden – bitte zuerst installieren."
    else
        SPOTIFY_FILES="$SPOTIFY_PATH/extra/share/spotify"
        PREFS_PATH="$HOME/.var/app/com.spotify.Client/config/spotify/prefs"
        cat > ~/.config/spicetify/config-xpui.ini <<EOF
    [Settings]
    spotify_path = $SPOTIFY_FILES
    prefs_path = $PREFS_PATH
    EOF
        sudo chmod a+wr -R "$SPOTIFY_FILES"
        sudo chmod a+wr -R "$SPOTIFY_FILES/Apps"
        ~/.spicetify/spicetify backup apply
        ~/.spicetify/spicetify apply
    echo "Spicetify wurde erfolgreich eingerichtet."
    fi


    
### 10. creating Noctalia config


