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




#### 10. Noctalia Config

    # ── Zielverzeichnisse anlegen ──
mkdir -p ~/.config/noctalia/colorschemes/"Catppuccin Macchiato Lavender"

# ── Vorhandene settings.json sichern ──
[ -f ~/.config/noctalia/settings.json ] && cp ~/.config/noctalia/settings.json ~/.config/noctalia/settings.json.bak

# ── settings.json ──
cat > ~/.config/noctalia/settings.json << 'EOF'
{
  "appLauncher": {
    "autoPasteClipboard": false,
    "clipboardWatchImageCommand": "wl-paste --type image --watch cliphist store",
    "clipboardWatchTextCommand": "wl-paste --type text --watch cliphist store",
    "clipboardWrapText": true,
    "customLaunchPrefix": "",
    "customLaunchPrefixEnabled": false,
    "density": "default",
    "enableClipPreview": true,
    "enableClipboardChips": true,
    "enableClipboardHistory": false,
    "enableClipboardSmartIcons": true,
    "enableSessionSearch": true,
    "enableSettingsSearch": true,
    "enableWindowsSearch": true,
    "iconMode": "tabler",
    "ignoreMouseInput": false,
    "overviewLayer": false,
    "pinnedApps": [
      "firefox",
      "org.gnome.Nautilus",
      "Alacritty",
      "discord",
      "org.gnome.Software",
      "org.manjaro.pamac.manager",
      "org.gnome.DiskUtility",
      "steam",
      "com.valvesoftware.Steam",
      "com.spotify.Client",
      "org.gnome.Terminal"
    ],
    "position": "center",
    "screenshotAnnotationTool": "",
    "showCategories": true,
    "showIconBackground": false,
    "sortByMostUsed": true,
    "terminalCommand": "alacritty -e",
    "viewMode": "list"
  },
  "audio": {
    "mprisBlacklist": [],
    "preferredPlayer": "",
    "spectrumFrameRate": 30,
    "spectrumMirrored": true,
    "visualizerType": "wave",
    "volumeFeedback": false,
    "volumeFeedbackSoundFile": "",
    "volumeOverdrive": false,
    "volumeStep": 5
  },
  "bar": {
    "autoHideDelay": 500,
    "autoShowDelay": 150,1. installing YAY and PARU

YAY

sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si

Paru

sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/paru.git && cd paru && makepkg -si

2. installing Flatpak and Gnome Software

sudo pacman -S flatpak gnome-software gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

3. installing Bibata Cursor

yay -S bibata-cursor-theme-bin
wget https://raw.githubusercontent.com/J3sven/wayland-cursor-theme-utility/refs/heads/main/cursor-utility.sh -O cursor-utility.sh && chmod +x cursor-utility.sh
./cursor-utility.sh

4. installing Noctalia Shell

yay -S noctalia-shell

5. Display layout, Keyboard Layout and making Noctalia v4 to an auostart Application

mkdir -p ~/.config/labwc
echo 'setxkbmap de; qs -c noctalia-shell &; wlr-randr --output DP-1 --mode 2560x1440@179.959000 --scale 1 --pos 1440,560 --output HDMI-A-1 --mode 2560x1440@59.951000 --transform 90     --scale 1 --pos 0,0' > ~/.config/labwc/autostart
chmod +x ~/.config/labwc/autostart

6. installing a Wallpaper Collection /Dokumente/Wallpaper

    sudo pacman -S git-lfs && git lfs install
    mkdir -p ~/Dokumente/Wallpaper && \
    git clone https://github.com/BlackoneBc/walls-catppuccin-mocha.git && \
    cd walls-catppuccin-mocha && \
    git lfs install && \
    git lfs pull && \
    cp *.png *.jpg ~/Dokumente/Wallpaper/ 2>/dev/null && \
    cd .. && \
    rm -rf walls-catppuccin-mocha

7. Installing and activating a SDDM Theme

yay -S --needed sddm-silent-theme 
sudo sh -c "echo -e '[General]\nInputMethod=qtvirtualkeyboard\nGreeterEnvironment=QML2_IMPORT_PATH=/usr/share/sddm/themes/silent/components/,QT_IM_MODULE=qtvirtualkeyboard\n\n[Theme]\nCurrent=silent' >> /etc/sddm.conf"

Test before reboot!!!

cd /usr/share/sddm/themes/silent/ && ./test.sh

8. Installing nice to have Flatpak Applications

flatpak install -y com.brave.Browser com.github.IsmaelMartinez.teams_for_linux com.heroicgameslauncher.hgl com.jeffser.Alpaca com.lunarclient.LunarClient com.nuclearplayer.Nuclear com.rtosta.zapzap com.spotify.Client com.valvesoftware.Steam dev.vencord.Vesktop io.github.Geocld.PeaSyo4Desk io.github.ecotubehq.player io.github.revisto.drum-machine io.github.ungoogled_software.ungoogled_chromium io.gitlab.adhami3310.Impression io.missioncenter.MissionCenter org.bluej.BlueJ org.gnome.Decibels org.gnome.Showtime org.gnome.TextEditor org.onlyoffice.desktopeditors org.prismlauncher.PrismLauncher org.videolan.VLC 

9. Installing Spicetify

sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply

All in one:

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

    "backgroundOpacity": 0.93,
    "barType": "simple",
    "capsuleColorKey": "none",
    "capsuleOpacity": 1,
    "contentPadding": 2,
    "density": "spacious",
    "displayMode": "always_visible",
    "enableExclusionZoneInset": true,
    "fontScale": 1,
    "frameRadius": 12,
    "frameThickness": 8,
    "hideOnOverview": false,
    "marginHorizontal": 4,
    "marginVertical": 4,
    "middleClickAction": "settings",
    "middleClickCommand": "",
    "middleClickFollowMouse": true,
    "monitors": [],
    "mouseWheelAction": "volume",
    "mouseWheelWrap": true,
    "outerCorners": true,
    "position": "top",
    "reverseScroll": false,
    "rightClickAction": "launcherPanel",
    "rightClickCommand": "",
    "rightClickFollowMouse": true,
    "screenOverrides": [],
    "showCapsule": true,
    "showOnWorkspaceSwitch": true,
    "showOutline": false,
    "useSeparateOpacity": false,
    "widgetSpacing": 6,
    "widgets": {
      "center": [
        { "colorName": "primary", "hideWhenIdle": false, "id": "AudioVisualizer", "width": 200 },
        { "clockColor": "none", "customFont": "", "formatHorizontal": "HH:mm ddd, MMM dd", "formatVertical": "HH mm - dd MM", "id": "Clock", "tooltipFormat": "HH:mm ddd, MMM dd", "useCustomFont": false },
        { "compactMode": false, "hideMode": "transparent", "hideWhenIdle": false, "id": "MediaMini", "maxWidth": 145, "panelShowAlbumArt": true, "scrollingMode": "hover", "showAlbumArt": true, "showArtistFirst": true, "showProgressRing": true, "showVisualizer": false, "textColor": "none", "useFixedWidth": false, "visualizerType": "linear" }
      ],
      "left": [
        { "colorizeSystemIcon": "none", "colorizeSystemText": "none", "customIconPath": "", "enableColorization": true, "icon": "rocket", "iconColor": "none", "id": "Launcher", "useDistroLogo": true },
        { "compactMode": true, "diskPath": "/", "iconColor": "none", "id": "SystemMonitor", "showCpuCores": false, "showCpuFreq": false, "showCpuTemp": true, "showCpuUsage": true, "showDiskAvailable": false, "showDiskUsage": false, "showDiskUsageAsPercent": false, "showGpuTemp": false, "showLoadAverage": false, "showMemoryAsPercent": false, "showMemoryUsage": true, "showNetworkStats": false, "showSwapUsage": false, "textColor": "none", "useMonospaceFont": true, "usePadding": false },
        { "colorizeIcons": false, "hideMode": "hidden", "iconScale": 0.8, "id": "Taskbar", "maxTaskbarWidth": 40, "onlyActiveWorkspaces": true, "onlySameOutput": true, "showPinnedApps": true, "showTitle": false, "smartWidth": true, "titleWidth": 120 }
      ],
      "right": [
        { "blacklist": [], "chevronColor": "none", "colorizeIcons": false, "drawerEnabled": true, "hidePassive": false, "id": "Tray", "pinned": [] },
        { "hideWhenZero": false, "hideWhenZeroUnread": false, "iconColor": "none", "id": "NotificationHistory", "showUnreadBadge": true, "unreadBadgeColor": "primary" },
        { "displayMode": "onhover", "iconColor": "none", "id": "Volume", "middleClickCommand": "pwvucontrol || pavucontrol", "textColor": "none" },
        { "displayMode": "onhover", "iconColor": "none", "id": "KeyboardLayout", "showIcon": true, "textColor": "none" },
        { "displayMode": "onhover", "iconColor": "none", "id": "Bluetooth", "textColor": "none" },
        { "displayMode": "onhover", "iconColor": "none", "id": "VPN", "textColor": "none" },
        { "displayMode": "onhover", "iconColor": "none", "id": "Network", "textColor": "none" },
        { "iconColor": "none", "id": "WallpaperSelector" },
        { "colorizeDistroLogo": false, "colorizeSystemIcon": "none", "colorizeSystemText": "none", "customIconPath": "", "enableColorization": false, "icon": "power", "id": "ControlCenter", "useDistroLogo": false }
      ]
    }
  },
  "brightness": {
    "backlightDeviceMappings": [],
    "brightnessStep": 5,
    "enableDdcSupport": false,
    "enforceMinimum": true
  },
  "calendar": {
    "cards": [
      { "enabled": true, "id": "calendar-header-card" },
      { "enabled": true, "id": "calendar-month-card" },
      { "enabled": true, "id": "weather-card" }
    ]
  },
  "colorSchemes": {
    "darkMode": true,
    "generationMethod": "tonal-spot",
    "manualSunrise": "06:30",
    "manualSunset": "18:30",
    "monitorForColors": "",
    "predefinedScheme": "Catppuccin",
    "schedulingMode": "off",
    "syncGsettings": true,
    "useWallpaperColors": false
  },
  "controlCenter": {
    "cards": [
      { "enabled": true, "id": "profile-card" },
      { "enabled": true, "id": "shortcuts-card" },
      { "enabled": true, "id": "audio-card" },
      { "enabled": false, "id": "brightness-card" },
      { "enabled": true, "id": "weather-card" },
      { "enabled": true, "id": "media-sysmon-card" }
    ],
    "diskPath": "/",
    "position": "close_to_bar_button",
    "shortcuts": {
      "left": [
        { "id": "Network" },
        { "id": "Bluetooth" },
        { "id": "WallpaperSelector" },
        { "id": "NoctaliaPerformance" },
        { "id": "DarkMode" }
      ],
      "right": [
        { "id": "Notifications" },
        { "id": "PowerProfile" },
        { "id": "KeepAwake" },
        { "id": "NightLight" }
      ]
    }
  },
  "desktopWidgets": {
    "enabled": true,
    "gridSnap": false,
    "gridSnapScale": false,
    "monitorWidgets": [
      {
        "name": "DP-1",
        "widgets": [
          { "clockColor": "none", "clockStyle": "minimal", "customFont": "Noto Sans Ethiopic Thin", "format": "HH:mm\\nd MMMM yyyy", "id": "Clock", "roundedCorners": true, "scale": 1.2535640723161134, "showBackground": false, "useCustomFont": true, "x": 1200, "y": 600 },
          { "hideMode": "hidden", "id": "MediaPlayer", "roundedCorners": true, "scale": 1, "showAlbumArt": true, "showBackground": true, "showButtons": true, "showVisualizer": true, "visualizerType": "linear", "x": 40, "y": 1320 },
          { "id": "Weather", "roundedCorners": true, "scale": 1, "showBackground": true, "x": 2280, "y": 80 },
          { "diskPath": "/", "id": "SystemStat", "layout": "bottom", "roundedCorners": true, "scale": 1, "showBackground": false, "statType": "CPU", "x": 2280, "y": 1040 },
          { "diskPath": "/", "id": "SystemStat", "layout": "side", "roundedCorners": true, "scale": 1, "showBackground": false, "statType": "Memory", "x": 2280, "y": 1160 },
          { "diskPath": "/", "id": "SystemStat", "layout": "side", "roundedCorners": true, "scale": 1, "showBackground": false, "statType": "Network", "x": 2280, "y": 1280 },
          { "colorName": "primary", "height": 150, "hideWhenIdle": false, "id": "AudioVisualizer", "roundedCorners": true, "scale": 2.697350902673208, "showBackground": false, "visualizerType": "linear", "width": 500, "x": 618, "y": 1001 }
        ]
      }
    ],
    "overviewEnabled": true
  },
  "dock": {
    "animationSpeed": 1,
    "backgroundOpacity": 0.87,
    "colorizeIcons": false,
    "deadOpacity": 0.6,
    "displayMode": "auto_hide",
    "dockType": "attached",
    "enabled": true,
    "floatingRatio": 1,
    "groupApps": false,
    "groupClickAction": "cycle",
    "groupContextMenuMode": "extended",
    "groupIndicatorStyle": "dots",
    "inactiveIndicators": true,
    "indicatorColor": "primary",
    "indicatorOpacity": 0.5,
    "indicatorThickness": 6,
    "launcherIcon": "",
    "launcherIconColor": "none",
    "launcherPosition": "start",
    "launcherUseDistroLogo": true,
    "monitors": [],
    "onlySameOutput": false,
    "pinnedApps": [
      "org.gnome.Terminal",
      "Alacritty",
      "firefox",
      "org.gnome.Nautilus",
      "org.gnome.Software",
      "org.manjaro.pamac.manager",
      "com.heroicgameslauncher.hgl",
      "steamwebhelper",
      "discord",
      "com.spotify.Client",
      "DesktopEditors"
    ],
    "pinnedStatic": false,
    "position": "bottom",
    "showDockIndicator": true,
    "showLauncherIcon": true,
    "sitOnFrame": false,
    "size": 1.1
  },
  "general": {
    "allowPanelsOnScreenWithoutBar": true,
    "allowPasswordWithFprintd": false,
    "animationDisabled": false,
    "animationSpeed": 1,
    "autoStartAuth": false,
    "avatarImage": "/home/lennart/Dokumente/Wallpaper/3d-model.jpg",
    "boxRadiusRatio": 1,
    "clockFormat": "hh\\nmm",
    "clockStyle": "custom",
    "compactLockScreen": false,
    "dimmerOpacity": 0.2,
    "enableBlurBehind": true,
    "enableLockScreenCountdown": true,
    "enableLockScreenMediaControls": false,
    "enableShadows": true,
    "forceBlackScreenCorners": false,
    "iRadiusRatio": 1,
    "keybinds": {
      "keyDown": ["Down"],
      "keyEnter": ["Return", "Enter"],
      "keyEscape": ["Esc"],
      "keyLeft": ["Left"],
      "keyRemove": ["Del"],
      "keyRight": ["Right"],
      "keyUp": ["Up"]
    },
    "language": "",
    "lockOnSuspend": true,
    "lockScreenAnimations": false,
    "lockScreenBlur": 0,
    "lockScreenCountdownDuration": 10000,
    "lockScreenMonitors": [],
    "lockScreenTint": 0,
    "passwordChars": false,
    "radiusRatio": 1.6,
    "reverseScroll": false,
    "scaleRatio": 1.05,
    "screenRadiusRatio": 1,
    "shadowDirection": "bottom_right",
    "shadowOffsetX": 2,
    "shadowOffsetY": 3,
    "showChangelogOnStartup": true,
    "showHibernateOnLockScreen": false,
    "showScreenCorners": false,
    "showSessionButtonsOnLockScreen": true,
    "smoothScrollEnabled": true,
    "telemetryEnabled": false
  },
  "hooks": {
    "colorGeneration": "",
    "darkModeChange": "",
    "enabled": false,
    "performanceModeDisabled": "",
    "performanceModeEnabled": "",
    "screenLock": "",
    "screenUnlock": "",
    "session": "",
    "startup": "",
    "wallpaperChange": ""
  },
  "idle": {
    "customCommands": "[]",
    "enabled": false,
    "fadeDuration": 5,
    "lockCommand": "",
    "lockTimeout": 660,
    "resumeLockCommand": "",
    "resumeScreenOffCommand": "",
    "resumeSuspendCommand": "",
    "screenOffCommand": "",
    "screenOffTimeout": 600,
    "suspendCommand": "",
    "suspendTimeout": 1800
  },
  "location": {
    "analogClockInCalendar": false,
    "autoLocate": false,
    "firstDayOfWeek": -1,
    "hideWeatherCityName": false,
    "hideWeatherTimezone": false,
    "name": "Bünde",
    "showCalendarEvents": true,
    "showCalendarWeather": true,
    "showWeekNumberInCalendar": false,
    "use12hourFormat": false,
    "useFahrenheit": false,
    "weatherEnabled": true,
    "weatherShowEffects": true,
    "weatherTaliaMascotAlways": false
  },
  "network": {
    "bluetoothAutoConnect": true,
    "bluetoothDetailsViewMode": "grid",
    "bluetoothHideUnnamedDevices": false,
    "bluetoothRssiPollIntervalMs": 60000,
    "bluetoothRssiPollingEnabled": false,
    "disableDiscoverability": false,
    "networkPanelView": "wifi",
    "wifiDetailsViewMode": "grid"
  },
  "nightLight": {
    "autoSchedule": true,
    "dayTemp": "6500",
    "enabled": false,
    "forced": false,
    "manualSunrise": "06:30",
    "manualSunset": "18:30",
    "nightTemp": "4000"
  },
  "noctaliaPerformance": {
    "disableDesktopWidgets": true,
    "disableWallpaper": true
  },
  "notifications": {
    "backgroundOpacity": 1,
    "clearDismissed": true,
    "criticalUrgencyDuration": 15,
    "density": "default",
    "enableBatteryToast": true,
    "enableKeyboardLayoutToast": true,
    "enableMarkdown": false,
    "enableMediaToast": false,
    "enabled": true,
    "location": "top_right",
    "lowUrgencyDuration": 3,
    "monitors": [],
    "normalUrgencyDuration": 8,
    "overlayLayer": true,
    "respectExpireTimeout": false,
    "saveToHistory": {
      "critical": true,
      "low": true,
      "normal": true
    },
    "sounds": {
      "criticalSoundFile": "",
      "enabled": false,
      "excludedApps": "discord,firefox,chrome,chromium,edge",
      "lowSoundFile": "",
      "normalSoundFile": "",
      "separateSounds": false,
      "volume": 0.5
    }
  },
  "osd": {
    "autoHideMs": 2000,
    "backgroundOpacity": 1,
    "enabled": true,
    "enabledTypes": [0, 1, 2],
    "location": "top_right",
    "monitors": [],
    "overlayLayer": true
  },
  "plugins": {
    "autoUpdate": false,
    "notifyUpdates": true
  },
  "sessionMenu": {
    "countdownDuration": 10000,
    "enableCountdown": true,
    "largeButtonsLayout": "single-row",
    "largeButtonsStyle": true,
    "position": "center",
    "powerOptions": [
      { "action": "lock", "enabled": true, "keybind": "1" },
      { "action": "suspend", "enabled": true, "keybind": "2" },
      { "action": "hibernate", "enabled": true, "keybind": "3" },
      { "action": "reboot", "enabled": true, "keybind": "4" },
      { "action": "logout", "enabled": true, "keybind": "5" },
      { "action": "shutdown", "enabled": true, "keybind": "6" },
      { "action": "rebootToUefi", "enabled": true, "keybind": "7" }
    ],
    "showHeader": true,
    "showKeybinds": true
  },
  "settingsVersion": 59,
  "systemMonitor": {
    "batteryCriticalThreshold": 5,
    "batteryWarningThreshold": 20,
    "cpuCriticalThreshold": 90,
    "cpuWarningThreshold": 80,
    "criticalColor": "",
    "diskAvailCriticalThreshold": 10,
    "diskAvailWarningThreshold": 20,
    "diskCriticalThreshold": 90,
    "diskWarningThreshold": 80,
    "enableDgpuMonitoring": true,
    "externalMonitor": "resources || missioncenter || jdsystemmonitor || corestats || system-monitoring-center || gnome-system-monitor || plasma-systemmonitor || mate-system-monitor || ukui-system-monitor || deepin-system-monitor || pantheon-system-monitor",
    "gpuCriticalThreshold": 90,
    "gpuWarningThreshold": 80,
    "memCriticalThreshold": 90,
    "memWarningThreshold": 80,
    "swapCriticalThreshold": 90,
    "swapWarningThreshold": 80,
    "tempCriticalThreshold": 90,
    "tempWarningThreshold": 80,
    "useCustomColors": false,
    "warningColor": ""
  },
  "templates": {
    "activeTemplates": [],
    "enableUserTheming": false
  },
  "ui": {
    "boxBorderEnabled": false,
    "fontDefault": "Sans Serif",
    "fontDefaultScale": 1,
    "fontFixed": "monospace",
    "fontFixedScale": 1,
    "panelBackgroundOpacity": 0.85,
    "panelsAttachedToBar": true,
    "scrollbarAlwaysVisible": true,
    "settingsPanelMode": "attached",
    "settingsPanelSideBarCardStyle": false,
    "tooltipsEnabled": true,
    "translucentWidgets": false
  },
  "wallpaper": {
    "automationEnabled": false,
    "directory": "/home/lennart/Pictures/Wallpapers",
    "enableMultiMonitorDirectories": false,
    "enabled": true,
    "favorites": [
      {
        "appearance": "dark",
        "colorScheme": "Catppuccin",
        "darkMode": true,
        "generationMethod": "tonal-spot",
        "paletteColors": ["#cba6f7", "#fab387", "#94e2d5", "#f38ba8"],
        "path": "/home/lennart/Dokumente/Wallpaper/dark-waves.jpg",
        "useWallpaperColors": false
      }
    ],
    "fillColor": "#000000",
    "fillMode": "crop",
    "hideWallpaperFilenames": false,
    "linkLightAndDarkWallpapers": true,
    "monitorDirectories": [],
    "overviewBlur": 0.4,
    "overviewEnabled": false,
    "overviewTint": 0.6,
    "panelPosition": "follow_bar",
    "randomIntervalSec": 300,
    "setWallpaperOnAllMonitors": true,
    "showHiddenFiles": false,
    "skipStartupTransition": false,
    "solidColor": "#1a1a2e",
    "sortOrder": "name",
    "transitionDuration": 1500,
    "transitionEdgeSmoothness": 0.05,
    "transitionType": ["fade", "disc", "stripes", "wipe", "pixelate", "honeycomb"],
    "useOriginalImages": false,
    "useSolidColor": false,
    "useWallhaven": false,
    "viewMode": "single",
    "wallhavenApiKey": "",
    "wallhavenCategories": "111",
    "wallhavenOrder": "desc",
    "wallhavenPurity": "100",
    "wallhavenQuery": "",
    "wallhavenRatios": "",
    "wallhavenResolutionHeight": "",
    "wallhavenResolutionMode": "atleast",
    "wallhavenResolutionWidth": "",
    "wallhavenSorting": "relevance",
    "wallpaperChangeMode": "random"
  }
}
EOF

# ── colors.json ──
cat > ~/.config/noctalia/colors.json << 'EOF'
{
  "mError": "#f38ba8",
  "mHover": "#94e2d5",
  "mOnError": "#11111b",
  "mOnHover": "#11111b",
  "mOnPrimary": "#11111b",
  "mOnSecondary": "#11111b",
  "mOnSurface": "#cdd6f4",
  "mOnSurfaceVariant": "#a3b4eb",
  "mOnTertiary": "#11111b",
  "mOutline": "#4c4f69",
  "mPrimary": "#cba6f7",
  "mSecondary": "#fab387",
  "mShadow": "#11111b",
  "mSurface": "#1e1e2e",
  "mSurfaceVariant": "#313244",
  "mTertiary": "#94e2d5"
}
EOF

# ── plugins.json ──
cat > ~/.config/noctalia/plugins.json << 'EOF'
{
  "sources": [
    { "enabled": true, "name": "Noctalia Plugins", "url": "https://github.com/noctalia-dev/noctalia-plugins" }
  ],
  "states": {},
  "version": 2
}
EOF

# ── Farbschema (Catppuccin Macchiato Lavender) ──
cat > ~/.config/noctalia/colorschemes/"Catppuccin Macchiato Lavender"/"Catppuccin Macchiato Lavender.json" << 'EOF'
{
  "dark": {
    "mPrimary": "#b7bdf8",
    "mOnPrimary": "#24273a",
    "mSecondary": "#f5bde6",
    "mOnSecondary": "#24273a",
    "mTertiary": "#c6a0f6",
    "mOnTertiary": "#24273a",
    "mError": "#ed8796",
    "mOnError": "#24273a",
    "mSurface": "#24273a",
    "mOnSurface": "#cad3f5",
    "mSurfaceVariant": "#363a4f",
    "mOnSurfaceVariant": "#a5adcb",
    "mOutline": "#6e738d",
    "mShadow": "#181926",
    "mHover": "#494d64",
    "mOnHover": "#cad3f5",
    "terminal": {
      "normal": {
        "black": "#494d64",
        "red": "#ed8796",
        "green": "#a6da95",
        "yellow": "#eed49f",
        "blue": "#8aadf4",
        "magenta": "#f5bde6",
        "cyan": "#8bd5ca",
        "white": "#b8c0e0"
      },
      "bright": {
        "black": "#5b6078",
        "red": "#ed8796",
        "green": "#a6da95",
        "yellow": "#eed49f",
        "blue": "#8aadf4",
        "magenta": "#f5bde6",
        "cyan": "#8bd5ca",
        "white": "#a5adcb"
      },
      "foreground": "#cad3f5",
      "background": "#24273a",
      "selectionFg": "#cad3f5",
      "selectionBg": "#5b6078",
      "cursorText": "#24273a",
      "cursor": "#b7bdf8"
    }
  },
  "light": {
    "mPrimary": "#7287fd",
    "mOnPrimary": "#eff1f5",
    "mSecondary": "#1e66f5",
    "mOnSecondary": "#eff1f5",
    "mTertiary": "#8839ef",
    "mOnTertiary": "#eff1f5",
    "mError": "#d20f39",
    "mOnError": "#eff1f5",
    "mSurface": "#eff1f5",
    "mOnSurface": "#4c4f69",
    "mSurfaceVariant": "#ccd0da",
    "mOnSurfaceVariant": "#6c6f85",
    "mOutline": "#9ca0b0",
    "mShadow": "#dce0e8",
    "mHover": "#bcc0cc",
    "mOnHover": "#4c4f69",
    "terminal": {
      "normal": {
        "black": "#5c5f77",
        "red": "#d20f39",
        "green": "#40a02b",
        "yellow": "#df8e1d",
        "blue": "#1e66f5",
        "magenta": "#ea76cb",
        "cyan": "#179299",
        "white": "#acb0be"
      },
      "bright": {
        "black": "#6c6f85",
        "red": "#d20f39",
        "green": "#40a02b",
        "yellow": "#df8e1d",
        "blue": "#1e66f5",
        "magenta": "#ea76cb",
        "cyan": "#179299",
        "white": "#bcc0cc"
      },
      "foreground": "#4c4f69",
      "background": "#eff1f5",
      "selectionFg": "#4c4f69",
      "selectionBg": "#acb0be",
      "cursorText": "#eff1f5",
      "cursor": "#7287fd"
    }
  }
}
EOF

# ── Pfade anpassen (ersetzt /home/lennart durch $HOME) ──
sed -i "s|/home/lennart|$HOME|g" ~/.config/noctalia/settings.json

# ── Wallpaper‑Verzeichnis auf $HOME/Dokumente/Wallpaper setzen ──
sed -i 's|"directory": ".*Pictures/Wallpapers"|"directory": "'"$HOME/Dokumente/Wallpaper"'"|g' ~/.config/noctalia/settings.json

# ── Favoriten‑Pfad ebenfalls korrigieren ──
sed -i 's|"path": ".*/Dokumente/Wallpaper/dark-waves.jpg"|"path": "'"$HOME/Dokumente/Wallpaper/dark-waves.jpg"'"|g' ~/.config/noctalia/settings.json

echo "✅ Noctalia‑Konfiguration wurde in ~/.config/noctalia/ installiert und an dein System angepasst."
echo "Starte Noctalia neu (z.B. mit 'pkill -f noctalia-shell && qs -c noctalia-shell &'), um die Änderungen zu übernehmen."

















































All in one:

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
