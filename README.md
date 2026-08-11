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

### 5. Display layout, Keyboard Layout and making Noctalia v4 to an auostart Application 

    mkdir -p ~/.config/labwc
    echo 'setxkbmap de; qs -c noctalia-shell &; wlr-randr --output DP-1 --mode 2560x1440@179.959000 --scale 1 --pos 1440,560 --output HDMI-A-1 --mode 2560x1440@59.951000 --transform 90     --scale 1 --pos 0,0' > ~/.config/labwc/autostart
    chmod +x ~/.config/labwc/autostart

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

    flatpak install -y com.brave.Browser com.github.IsmaelMartinez.teams_for_linux com.heroicgameslauncher.hgl com.jeffser.Alpaca com.lunarclient.LunarClient com.nuclearplayer.Nuclear com.rtosta.zapzap com.spotify.Client com.valvesoftware.Steam dev.vencord.Vesktop io.github.Geocld.PeaSyo4Desk io.github.ecotubehq.player io.github.revisto.drum-machine io.github.ungoogled_software.ungoogled_chromium io.gitlab.adhami3310.Impression io.missioncenter.MissionCenter org.bluej.BlueJ org.gnome.Decibels org.gnome.Showtime org.gnome.TextEditor org.onlyoffice.desktopeditors org.prismlauncher.PrismLauncher org.videolan.VLC 

#### 9. Installing Spicetify

    sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply









    #!/bin/bash
    set -e

    # --- Configuration ---
    AUR_HELPER="yay"   # or "paru"
    MONITOR_MAIN="DP-1"
    MONITOR_SEC="HDMI-A-1"
    WALLPAPER_DIR="$HOME/Dokumente/Wallpaper"
    SDDM_THEME="silent"

    # --- Helper functions ---
    confirm() {
    read -p "$1 (y/N) " -n 1 -r
    echo
    [[ $REPLY =~ ^[Yy]$ ]]
    }
    
    # --- Step 1: AUR Helper ---
    if ! command -v $AUR_HELPER &> /dev/null; then
    echo "Installing $AUR_HELPER..."
    sudo pacman -S --needed git base-devel
    git clone https://aur.archlinux.org/$AUR_HELPER.git
    cd $AUR_HELPER && makepkg -si --noconfirm
    cd ..
    rm -rf $AUR_HELPER
    fi

    # --- Step 2: Flatpak & GNOME Software ---
    echo "Installing Flatpak and GNOME Software..."
    sudo pacman -S --needed flatpak gnome-software gnome-software-plugin-flatpak
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

    # --- Step 3: Bibata Cursor ---
    if confirm "Install Bibata cursor and set it?"; then
    $AUR_HELPER -S --needed bibata-cursor-theme-bin
    gsettings set org.gnome.desktop.interface cursor-theme 'Bibata-Modern-Classic'
    gsettings set org.gnome.desktop.interface cursor-size 24
    mkdir -p ~/.config/labwc
    echo "XCURSOR_THEME=Bibata-Modern-Classic" >> ~/.config/labwc/environment
    echo "XCURSOR_SIZE=24" >> ~/.config/labwc/environment
    fi

    # --- Step 4: Noctalia Shell ---
    if confirm "Install Noctalia Shell?"; then
    $AUR_HELPER -S --needed noctalia-shell
    fi

    # --- Step 5: Autostart for Labwc ---
    if confirm "Configure Labwc autostart?"; then
    cat > ~/.config/labwc/autostart << 'EOF'
    #!/bin/sh
    # Keyboard layout
    setxkbmap de 2>/dev/null || true
    # Noctalia shell helper
    qs -c noctalia-shell &
    # Displays (adjust to your monitors)
    wlr-randr --output $MONITOR_MAIN --auto --pos 1440,560 2>/dev/null || \
    wlr-randr --output $MONITOR_SEC --auto --transform 90 --pos 0,0 2>/dev/null
    EOF
    chmod +x ~/.config/labwc/autostart
    fi

    # --- Step 6: Wallpaper Collection ---
    if confirm "Clone and copy wallpapers?"; then
    sudo pacman -S --needed git-lfs
    git lfs install
    mkdir -p "$WALLPAPER_DIR"
    git clone https://github.com/BlackoneBc/walls-catppuccin-mocha.git
    cd walls-catppuccin-mocha
    git lfs pull
    find . -type f \( -name "*.png" -o -name "*.jpg" \) -exec cp {} "$WALLPAPER_DIR/" \;
    cd ..
    rm -rf walls-catppuccin-mocha
    fi

    # --- Step 7: SDDM Theme ---
    if confirm "Install and configure SDDM Silent theme?"; then
    $AUR_HELPER -S --needed sddm-silent-theme
    # Backup existing config
    sudo cp /etc/sddm.conf /etc/sddm.conf.bak 2>/dev/null || true
    # Overwrite with our settings
    sudo tee /etc/sddm.conf > /dev/null << 'EOF'
    [General]
    InputMethod=qtvirtualkeyboard
    GreeterEnvironment=QML2_IMPORT_PATH=/usr/share/sddm/themes/silent/components/,QT_IM_MODULE=qtvirtualkeyboard

    [Theme]
    Current=silent
    EOF
    echo "Test the theme with: cd /usr/share/sddm/themes/silent/ && ./test.sh"
    fi

    # --- Step 8: Flatpak Applications ---
    FLATPAK_APPS=(
    com.brave.Browser
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
    org.bluej.BlueJ
    org.gnome.Decibels
    org.gnome.Showtime
    org.gnome.TextEditor
    org.onlyoffice.desktopeditors
    org.prismlauncher.PrismLauncher
    org.videolan.VLC
    )
    if confirm "Install Flatpak applications?"; then
    for app in "${FLATPAK_APPS[@]}"; do
        flatpak install -y flathub "$app" || echo "Failed to install $app, skipping."
    done
    fi

    # --- Step 9: Spicetify ---
    if confirm "Install Spicetify for Spotify?"; then
    sudo pacman -S --needed unzip
    curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace
    mkdir -p ~/.config/spicetify
    # Determine Spotify flatpak path (user or system)
    SPOTIFY_PATH=$(flatpak info com.spotify.Client --show-location 2>/dev/null || echo "")
    if [[ -z "$SPOTIFY_PATH" ]]; then
        echo "Spotify flatpak not found. Install it first."
    else
        SPOTIFY_FILES="$SPOTIFY_PATH/extra/share/spotify"
        printf "[Settings]\nspotify_path = $SPOTIFY_FILES\nprefs_path = $HOME/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini
        # Grant write permissions only to the current user (safer)
        sudo chown -R "$USER":"$USER" "$SPOTIFY_FILES"
        # Apply spicetify
        ~/.spicetify/spicetify backup apply
        ~/.spicetify/spicetify apply
    fi
    fi

    echo "All done! Some changes may require a restart or logout."
