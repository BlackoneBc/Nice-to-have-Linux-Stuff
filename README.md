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

### 9. Installing Spicetify

    sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply

### 10. creating Noctalia config

    bash -c 'mkdir -p ~/.config/noctalia &&
    cat > ~/.config/noctalia/colors.json << "EOF"
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
    cat > ~/.config/noctalia/plugins.json << "EOF"
    {
    "sources": [
        {
            "enabled": true,
            "name": "Noctalia Plugins",
            "url": "https://github.com/noctalia-dev/noctalia-plugins"
        }
    ],
    "states": {
    },
    "version": 2
    }
      EOF
    cat > ~/.config/noctalia/settings.json << "EOF"
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
        "mprisBlacklist": [
        ],
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
        "autoShowDelay": 150,
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
        "monitors": [
        ],
        "mouseWheelAction": "volume",
        "mouseWheelWrap": true,
        "outerCorners": true,
        "position": "top",
        "reverseScroll": false,
        "rightClickAction": "launcherPanel",21. [✓] io.github.revisto.drum-machine                                    stable                 i             flathub                17,2 MB / 23,0 MB
22. [✓] io.github.ecotubehq.player                                        stable                 i             flathub                33,4 MB / 34,4 MB
23. [✓] com.nuclearplayer.Nuclear                                         stable                 i             flathub                25,2 MB / 25,4 MB
24. [✓] com.jeffser.Alpaca                                                stable                 i             flathub               646,8 MB / 748,4 MB
25. [✓] org.freedesktop.Platform                                          25.08                  i             flathub               102,8 MB / 253,4 MB
26. [✓] org.onlyoffice.desktopeditors                                     stable                 i             flathub               592,1 MB / 615,5 MB
27. [✓] org.bluej.BlueJ                                                   stable                 i             flathub               143,2 MB / 145,0 MB
28. [✓] io.github.ungoogled_software.ungoogled_chromium                   stable                 i             flathub               161,2 MB / 162,0 MB
29. [✓] io.github.Geocld.PeaSyo4Desk                                      stable                 i             flathub               165,6 MB / 194,5 MB
30. [✓] dev.vencord.Vesktop                                               stable                 i             flathub               119,6 MB / 123,4 MB
31. [✓] com.valvesoftware.Steam                                           stable                 i             flathub                33,7 MB / 35,5 MB
32. [✓] com.spotify.Client                                                stable                 i             flathub               193,4 MB / 193,8 MB
33. [✓] com.lunarclient.LunarClient                                       stable                 i             flathub               133,0 MB / 143,3 MB
34. [✓] com.heroicgameslauncher.hgl                                       stable                 i             flathub               349,3 MB / 356,0 MB
35. [✓] com.github.IsmaelMartinez.teams_for_linux                         stable                 i             flathub               134,3 MB / 144,7 MB
36. [✓] com.brave.Browser                                                 stable                 i             flathub               201,8 MB / 211,4 MB
37. [✓] org.kde.Platform.Locale                                           5.15-25.08             i             flathub               580,1 KB / 400,3 MB
38. [✓] org.kde.Platform                                                  5.15-25.08             i             flathub               273,2 MB / 367,4 MB
39. [✓] org.kde.Platform.Locale                                           6.10                   i             flathub               398,9 KB / 401,3 MB
40. [✓] org.kde.Platform                                                  6.10                   i             flathub               218,4 MB / 387,3 MB
41. [✓] org.prismlauncher.PrismLauncher                                   stable                 i             flathub                40,7 MB / 41,6 MB
42. [✓] org.kde.Platform.Locale                                           6.11                   i             flathub               134,4 KB / 401,6 MB
43. [✓] org.kde.Platform                                                  6.11                   i             flathub               307,9 MB / 405,5 MB
44. [✓] com.rtosta.zapzap                                                 stable                 i             flathub               138,9 MB / 144,5 MB
45. [✓] org.videolan.VLC.Locale                                           stable                 i             flathub               251,0 KB / 14,7 MB
46. [✓] org.videolan.VLC                                                  stable                 i             flathub                45,7 MB / 52,7 MB

Installation abgeschlossen.

/usr/share/sddm/themes/silent 9m
❯ cd

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply
[sudo] Passwort für lennart: 
Warnung: unzip-6.0-23.1 ist aktuell -- Überspringe
 Es gibt nichts zu tun
Invalid option --no-marketplace

~
❯ sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s --  && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply
Warnung: unzip-6.0-23.1 ist aktuell -- Überspringe
 Es gibt nichts zu tun
FETCHING Version 2.44.0
CREATING /home/lennart/.spicetify
DOWNLOADING https://github.com/spicetify/cli/releases/download/v2.44.0/spicetify-2.44.0-linux-amd64.tar.gz
######################################################################## 100.0%
EXTRACTING /home/lennart/.spicetify/spicetify.tar.gz
SETTING EXECUTABLE PERMISSIONS TO /home/lennart/.spicetify/spicetify
REMOVING /home/lennart/.spicetify/spicetify.tar.gz
APPENDING /home/lennart/.spicetify to PATH in /home/lennart/.config/fish/config.fish

spicetify v2.44.0 was installed successfully to /home/lennart/.spicetify
Run 'spicetify --help' to get started
Do you want to install spicetify Marketplace? (Y/n)
y
Starting the spicetify Marketplace installation script..
FETCHING Version 1.0.9
MAKING FOLDER  /home/lennart/.config/spicetify/CustomApps
DOWNLOADING https://github.com/spicetify/marketplace/releases/download/v1.0.9/marketplace.zip
######################################################################## 100.0%
EXTRACTING
COPYING
INSTALLING
 error  Could not detect "prefs" file location
 success  Default config-xpui.ini generated
 warning  Config "custom_apps" unchanged: spicetify-marketplace is not on the list.
 success  Config changed: inject_css = 1
 info  Run "spicetify apply" to apply new config
 success  Config changed: replace_colors = 1
 info  Run "spicetify apply" to apply new config
No theme selected, using placeholder theme
MAKING FOLDER  /home/lennart/.config/spicetify/Themes/marketplace
######################################################################## 100.0%
 success  Config changed: current_theme = marketplace
 info  Run "spicetify apply" to apply new config
 success  Config changed: custom_apps = marketplace
 info  Run "spicetify apply" to apply new config
Added to config!
APPLYING
 error  Cannot detect Spotify "prefs" file location. Please manually set "prefs_path" in config-xpui.ini

~
❯ spicetify apply
fish: Unknown command: spicetify

~
❯ bash -c 'mkdir -p ~/.config/noctalia &&
  cat > ~/.config/noctalia/colors.json << "EOF"
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
  cat > ~/.config/noctalia/plugins.json << "EOF"
  {
  "sources": [
      {
          "enabled": true,
          "name": "Noctalia Plugins",
          "url": "https://github.com/noctalia-dev/noctalia-plugins"
      }
  ],
  "states": {
  },
  "version": 2
  }
    EOF
  cat > ~/.config/noctalia/settings.json << "EOF"
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
      "mprisBlacklist": [
      ],
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
      "autoShowDelay": 150,
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
      "monitors": [
      ],
      "mouseWheelAction": "volume",
      "mouseWheelWrap": true,
      "outerCorners": true,
      "position": "top",
      "reverseScroll": false,
      "rightClickAction": "launcherPanel",
      "rightClickCommand": "",
      "rightClickFollowMouse": true,
      "screenOverrides": [
      ],
      "showCapsule": true,
      "showOnWorkspaceSwitch": true,
      "showOutline": false,
      "useSeparateOpacity": false,
      "widgetSpacing": 6,
      "widgets": {
          "center": [
              {
                  "colorName": "primary",
                  "hideWhenIdle": false,
                  "id": "AudioVisualizer",
                  "width": 200
              },
              {
                  "clockColor": "none",
                  "customFont": "",
                  "formatHorizontal": "HH:mm ddd, MMM dd",
                  "formatVertical": "HH mm - dd MM",
                  "id": "Clock",
                  "tooltipFormat": "HH:mm ddd, MMM dd",
                  "useCustomFont": false
              },
              {
                  "compactMode": false,
                  "hideMode": "transparent",
                  "hideWhenIdle": false,
                  "id": "MediaMini",
                  "maxWidth": 145,
                  "panelShowAlbumArt": true,
                  "scrollingMode": "hover",
                  "showAlbumArt": true,
                  "showArtistFirst": true,
                  "showProgressRing": true,
                  "showVisualizer": false,
                  "textColor": "none",
                  "useFixedWidth": false,
                  "visualizerType": "linear"
              }
          ],
          "left": [
              {
                  "colorizeSystemIcon": "none",
                  "colorizeSystemText": "none",
                  "customIconPath": "",
                  "enableColorization": true,
                  "icon": "rocket",
                  "iconColor": "none",
                  "id": "Launcher",
                  "useDistroLogo": true
              },
              {
                  "compactMode": true,
                  "diskPath": "/",
                  "iconColor": "none",
                  "id": "SystemMonitor",
                  "showCpuCores": false,
                  "showCpuFreq": false,
                  "showCpuTemp": true,
                  "showCpuUsage": true,
                  "showDiskAvailable": false,
                  "showDiskUsage": false,
                  "showDiskUsageAsPercent": false,
                  "showGpuTemp": false,
                  "showLoadAverage": false,
                  "showMemoryAsPercent": false,
                  "showMemoryUsage": true,
                  "showNetworkStats": false,
                  "showSwapUsage": false,
                  "textColor": "none",
                  "useMonospaceFont": true,
                  "usePadding": false
              },
              {
                  "colorizeIcons": false,
                  "hideMode": "hidden",
                  "iconScale": 0.8,
                  "id": "Taskbar",
                  "maxTaskbarWidth": 40,
                  "onlyActiveWorkspaces": true,
                  "onlySameOutput": true,
                  "showPinnedApps": true,
                  "showTitle": false,
                  "smartWidth": true,
                  "titleWidth": 120
              }
          ],
          "right": [
              {
                  "blacklist": [
                  ],
                  "chevronColor": "none",
                  "colorizeIcons": false,
                  "drawerEnabled": true,
                  "hidePassive": false,
                  "id": "Tray",
                  "pinned": [
                  ]
              },
              {
                  "hideWhenZero": false,
                  "hideWhenZeroUnread": false,
                  "iconColor": "none",
                  "id": "NotificationHistory",
                  "showUnreadBadge": true,
                  "unreadBadgeColor": "primary"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Volume",
                  "middleClickCommand": "pwvucontrol || pavucontrol",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "KeyboardLayout",
                  "showIcon": true,
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Bluetooth",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "VPN",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Network",
                  "textColor": "none"
              },
              {
                  "iconColor": "none",
                  "id": "WallpaperSelector"
              },
              {
                  "colorizeDistroLogo": false,
                  "colorizeSystemIcon": "none",
                  "colorizeSystemText": "none",
                  "customIconPath": "",
                  "enableColorization": false,
                  "icon": "power",
                  "id": "ControlCenter",
                  "useDistroLogo": false
              }
          ]
      }
  },
  "brightness": {
      "backlightDeviceMappings": [
      ],
      "brightnessStep": 5,
      "enableDdcSupport": false,
      "enforceMinimum": true
  },
  "calendar": {
      "cards": [
          {
              "enabled": true,
              "id": "calendar-header-card"
          },
          {
              "enabled": true,
              "id": "calendar-month-card"
          },
          {
              "enabled": true,
              "id": "weather-card"
          }
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
          {
              "enabled": true,
              "id": "profile-card"
          },
          {
              "enabled": true,
              "id": "shortcuts-card"
          },
          {
              "enabled": true,
              "id": "audio-card"
          },
          {
              "enabled": false,
              "id": "brightness-card"
          },
          {
              "enabled": true,
              "id": "weather-card"
          },
          {
              "enabled": true,
              "id": "media-sysmon-card"
          }
      ],
      "diskPath": "/",
      "position": "close_to_bar_button",
      "shortcuts": {
          "left": [
              {
                  "id": "Network"
              },
              {
                  "id": "Bluetooth"
              },
              {
                  "id": "WallpaperSelector"
              },
              {
                  "id": "NoctaliaPerformance"
              },
              {
                  "id": "DarkMode"
              }
          ],
          "right": [
              {
                  "id": "Notifications"
              },
              {
                  "id": "PowerProfile"
              },
              {
                  "id": "KeepAwake"
              },
              {
                  "id": "NightLight"
              }
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
                  {
                      "clockColor": "none",
                      "clockStyle": "minimal",
                      "customFont": "Noto Sans Ethiopic Thin",
                      "format": "HH:mm\\nd MMMM yyyy",
                      "id": "Clock",
                      "roundedCorners": true,
                      "scale": 1.2535640723161134,
                      "showBackground": false,
                      "useCustomFont": true,
                      "x": 1200,
                      "y": 600
                  },
                  {
                      "hideMode": "hidden",
                      "id": "MediaPlayer",
                      "roundedCorners": true,
                      "scale": 1,
                      "showAlbumArt": true,
                      "showBackground": true,
                      "showButtons": true,
                      "showVisualizer": true,
                      "visualizerType": "linear",
                      "x": 40,
                      "y": 1320
                  },
                  {
                      "id": "Weather",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": true,
                      "x": 2280,
                      "y": 80
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "bottom",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "CPU",
                      "x": 2280,
                      "y": 1040
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "side",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "Memory",
                      "x": 2280,
                      "y": 1160
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "side",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "Network",
                      "x": 2280,
                      "y": 1280
                  },
                  {
                      "colorName": "primary",
                      "height": 150,
                      "hideWhenIdle": false,
                      "id": "AudioVisualizer",
                      "roundedCorners": true,
                      "scale": 2.697350902673208,
                      "showBackground": false,
                      "visualizerType": "linear",
                      "width": 500,
                      "x": 618,
                      "y": 1001
                  }
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
      "monitors": [
      ],
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
          "keyDown": [
              "Down"
          ],
          "keyEnter": [
              "Return",
              "Enter"
          ],
          "keyEscape": [
              "Esc"
          ],
          "keyLeft": [
              "Left"
          ],
          "keyRemove": [
              "Del"
          ],
          "keyRight": [
              "Right"
          ],
          "keyUp": [
              "Up"
          ]
      },
      "language": "",
      "lockOnSuspend": true,
      "lockScreenAnimations": false,
      "lockScreenBlur": 0,
      "lockScreenCountdownDuration": 10000,
      "lockScreenMonitors": [
      ],
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
      "monitors": [
      ],
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
      "enabledTypes": [
          0,
          1,
          2
      ],
      "location": "top_right",
      "monitors": [
      ],
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
          {
              "action": "lock",
              "enabled": true,
              "keybind": "1"
          },
          {
              "action": "suspend",
              "enabled": true,
              "keybind": "2"
          },
          {
              "action": "hibernate",
              "enabled": true,
              "keybind": "3"
          },
          {
              "action": "reboot",
              "enabled": true,
              "keybind": "4"
          },
          {
              "action": "logout",
              "enabled": true,
              "keybind": "5"
          },
          {
              "action": "shutdown",
              "enabled": true,
              "keybind": "6"
          },
          {
              "action": "rebootToUefi",
              "enabled": true,
              "keybind": "7"
          }
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
      "activeTemplates": [
      ],
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
              "paletteColors": [
                  "#cba6f7",
                  "#fab387",
                  "#94e2d5",
                  "#f38ba8"
              ],
              "path": "/home/lennart/Dokumente/Wallpaper/dark-waves.jpg",
              "useWallpaperColors": false
          }
      ],
      "fillColor": "#000000",
      "fillMode": "crop",
      "hideWallpaperFilenames": false,
      "linkLightAndDarkWallpapers": true,
      "monitorDirectories": [
      ],
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
      "transitionType": [
          "fade",
          "disc",
          "stripes",
          "wipe",
          "pixelate",
          "honeycomb"
      ],
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
   EOF'
bash: Zeile 843: Warnung: Das in der Zeile 22 beginnende Here-Dokument geht bis zum Dateiende (erwartet wird »EOF«).

~
❯ 

~
❯ source ~/.config/fish/config.fish

~
❯ which spicetify
  spicetify --version
/home/lennart/.spicetify/spicetify
2.44.0

~
❯ find ~/.var/app/com.spotify.Client -name prefs -type f 2>/dev/null
/home/lennart/.var/app/com.spotify.Client/config/spotify/Users/31e2puiwyy4vixfr54mizu3umli4-user/prefs
/home/lennart/.var/app/com.spotify.Client/config/spotify/prefs

~
❯ flatpak info --show-location com.spotify.Client
/var/lib/flatpak/app/com.spotify.Client/x86_64/stable/abf9251b20078af8b596fe0400afeda1adc7b029ee0cee30f5f3556a12059f94

~
❯ ls -la ~/.var/app/com.spotify.Client/config/spotify/
drwxr-xr-x    - lennart 12 Aug 02:54  .
drwxr-xr-x    - lennart 12 Aug 02:54  ..
drwxr-xr-x    - lennart 12 Aug 02:54  Users
.rw-r--r-- 1,1k lennart 12 Aug 02:54 󰡯 prefs

~
❯ spicetify config
Settings
inject_css                    1
spotify_launch_flags          
color_scheme                  
inject_theme_js               1
replace_colors                1
overwrite_assets              0
check_spicetify_update        1
always_enable_devtools        0
spotify_path                  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/
prefs_path                    
current_theme                 marketplace

Preprocesses
remove_rtl_rule               1
expose_apis                   1
disable_sentry                1
disable_ui_logging            1

AdditionalFeatures
extensions
custom_apps                   marketplace
sidebar_config                0
home_config                   1
experimental_features         1

Backup
version                       
with                          

~
❯ 

~
❯ spicetify config prefs_path /home/lennart/.var/app/com.spotify.Client/config/spotify/prefs
 success  Config changed: prefs_path = /home/lennart/.var/app/com.spotify.Client/config/spotify/prefs
 info  Run "spicetify apply" to apply new config

~
❯ spicetify config prefs_path
/home/lennart/.var/app/com.spotify.Client/config/spotify/prefs

~
❯ flatpak kill com.spotify.Client 2>/dev/null

~
❯ spicetify backup
spicetify v2.44.0
 success  Backed up app files                                                                                                                               
 success  Extracted backup                                                                                                                                  
Preprocessing
 success  Fetched remote CSS map                                                                                                                            
 success  Finished extracting V8 snapshot blob to local file
Patching files [250/250] █████████████████████████████████████████████ 100% | 9s
 success  Preprocessing completed
 success  Everything is ready, you can start applying!

~ 9s
❯ spicetify apply
spicetify v2.44.0
 error  Failed to copy raw assets                                                                                                                           
 fatal  unlinkat /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa: permission denied

~
❯ spicetify apply
spicetify v2.44.0
 error  Failed to copy raw assets                                                                                                                           
 fatal  unlinkat /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa: permission denied

~
❯ sudo chmod a+wr -R /var/lib/flatpak/...
[sudo] Passwort für lennart: 
chmod: Zugriff auf '/var/lib/flatpak/...' nicht möglich: Datei oder Verzeichnis nicht gefunden

~
❯ spicetify --help | grep -i flatpak

~
❯ ls -ld /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify
drwxr-xr-x - root 12 Aug 02:49  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify

~
❯ ls -l /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa
.rw-r--r-- 4,1M root  9 Jun 22:29  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa

~
❯ sudo chmod a+wr /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify
  sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps

~
❯ spicetify apply
spicetify v2.44.0
 success  Copied raw assets                                                                                                                                 
 success  Overwrote themed assets                                                                                                                           
 success  Updated theme's styles                                                                                                                            
 success  Applied additional modifications                                                                                                                  
 success  Refreshed custom apps                                                                                                                             

~
❯ 

        "rightClickCommand": "",
        "rightClickFollowMouse": true,
        "screenOverrides": [
        ],
        "showCapsule": true,
        "showOnWorkspaceSwitch": true,
        "showOutline": false,
        "useSeparateOpacity": false,
        "widgetSpacing": 6,
        "widgets": {
            "center": [
                {
                    "colorName": "primary",
                    "hideWhenIdle": false,
                    "id": "AudioVisualizer",
                    "width": 200
                },
                {
                    "clockColor": "none",
                    "customFont": "",
                    "formatHorizontal": "HH:mm ddd, MMM dd",
                    "formatVertical": "HH mm - dd MM",
                    "id": "Clock",
                    "tooltipFormat": "HH:mm ddd, MMM dd",
                    "useCustomFont": false
                },
                {
                    "compactMode": false,
                    "hideMode": "transparent",
                    "hideWhenIdle": false,
                    "id": "MediaMini",
                    "maxWidth": 145,
                    "panelShowAlbumArt": true,
                    "scrollingMode": "hover",
                    "showAlbumArt": true,
                    "showArtistFirst": true,
                    "showProgressRing": true,
                    "showVisualizer": false,
                    "textColor": "none",
                    "useFixedWidth": false,
                    "visualizerType": "linear"
                }
            ],
            "left": [
                {
                    "colorizeSystemIcon": "none",
                    "colorizeSystemText": "none",
                    "customIconPath": "",
                    "enableColorization": true,
                    "icon": "rocket",
                    "iconColor": "none",
                    "id": "Launcher",
                    "useDistroLogo": true
                },
                {
                    "compactMode": true,
                    "diskPath": "/",
                    "iconColor": "none",
                    "id": "SystemMonitor",
                    "showCpuCores": false,
                    "showCpuFreq": false,
                    "showCpuTemp": true,
                    "showCpuUsage": true,
                    "showDiskAvailable": false,
                    "showDiskUsage": false,
                    "showDiskUsageAsPercent": false,
                    "showGpuTemp": false,
                    "showLoadAverage": false,
                    "showMemoryAsPercent": false,
                    "showMemoryUsage": true,
                    "showNetworkStats": false,
                    "showSwapUsage": false,
                    "textColor": "none",
                    "useMonospaceFont": true,
                    "usePadding": false
                },
                {
                    "colorizeIcons": false,
                    "hideMode": "hidden",
                    "iconScale": 0.8,
                    "id": "Taskbar",
                    "maxTaskbarWidth": 40,
                    "onlyActiveWorkspaces": true,
                    "onlySameOutput": true,
                    "showPinnedApps": true,
                    "showTitle": false,
                    "smartWidth": true,
                    "titleWidth": 120
                }
            ],
            "right": [
                {
                    "blacklist": [
                    ],
                    "chevronColor": "none",
                    "colorizeIcons": false,
                    "drawerEnabled": true,
                    "hidePassive": false,
                    "id": "Tray",
                    "pinned": [
                    ]
                },
                {
                    "hideWhenZero": false,
                    "hideWhenZeroUnread": false,
                    "iconColor": "none",
                    "id": "NotificationHistory",
                    "showUnreadBadge": true,
                    "unreadBadgeColor": "primary"
                },
                {
                    "displayMode": "onhover",
                    "iconColor": "none",
                    "id": "Volume",
                    "middleClickCommand": "pwvucontrol || pavucontrol",
                    "textColor": "none"
                },
                {
                    "displayMode": "onhover",
                    "iconColor": "none",
                    "id": "KeyboardLayout",
                    "showIcon": true,
                    "textColor": "none"
                },
                {
                    "displayMode": "onhover",
                    "iconColor": "none",
                    "id": "Bluetooth",
                    "textColor": "none"
                },
                {
                    "displayMode": "onhover",
                    "iconColor": "none",
                    "id": "VPN",
                    "textColor": "none"
                },
                {
                    "displayMode": "onhover",
                    "iconColor": "none",
                    "id": "Network",
                    "textColor": "none"
                },
                {
                    "iconColor": "none",
                    "id": "WallpaperSelector"
                },
                {
                    "colorizeDistroLogo": false,
                    "colorizeSystemIcon": "none",
                    "colorizeSystemText": "none",
                    "customIconPath": "",
                    "enableColorization": false,
                    "icon": "power",
                    "id": "ControlCenter",
                    "useDistroLogo": false
                }
            ]
        }
    },
    "brightness": {
        "backlightDeviceMappings": [
        ],
        "brightnessStep": 5,
        "enableDdcSupport": false,
        "enforceMinimum": true
    },
    "calendar": {
        "cards": [
            {
                "enabled": true,
                "id": "calendar-header-card"
            },
            {
                "enabled": true,
                "id": "calendar-month-card"
            },
            {
                "enabled": true,
                "id": "weather-card"
            }
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
            {
                "enabled": true,
                "id": "profile-card"
            },
            {
                "enabled": true,
                "id": "shortcuts-card"
            },
            {
                "enabled": true,
                "id": "audio-card"
            },
            {
                "enabled": false,
                "id": "brightness-card"
            },
            {
                "enabled": true,
                "id": "weather-card"
            },
            {
                "enabled": true,
                "id": "media-sysmon-card"
            }
        ],
        "diskPath": "/",
        "position": "close_to_bar_button",
        "shortcuts": {
            "left": [
                {
                    "id": "Network"
                },
                {
                    "id": "Bluetooth"
                },
                {
                    "id": "WallpaperSelector"
                },
                {
                    "id": "NoctaliaPerformance"
                },
                {
                    "id": "DarkMode"
                }
            ],
            "right": [
                {
                    "id": "Notifications"
                },
                {
                    "id": "PowerProfile"
                },
                {
                    "id": "KeepAwake"
                },
                {
                    "id": "NightLight"
                }
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
                    {
                        "clockColor": "none",
                        "clockStyle": "minimal",
                        "customFont": "Noto Sans Ethiopic Thin",
                        "format": "HH:mm\\nd MMMM yyyy",
                        "id": "Clock",
                        "roundedCorners": true,
                        "scale": 1.2535640723161134,
                        "showBackground": false,
                        "useCustomFont": true,
                        "x": 1200,
                        "y": 600
                    },
                    {
                        "hideMode": "hidden",
                        "id": "MediaPlayer",
                        "roundedCorners": true,
                        "scale": 1,
                        "showAlbumArt": true,
                        "showBackground": true,
                        "showButtons": true,
                        "showVisualizer": true,
                        "visualizerType": "linear",
                        "x": 40,
                        "y": 1320
                    },
                    {
                        "id": "Weather",
                        "roundedCorners": true,
                        "scale": 1,
                        "showBackground": true,
                        "x": 2280,
                        "y": 80
                    },
                    {
                        "diskPath": "/",
                        "id": "SystemStat",
                        "layout": "bottom",
                        "roundedCorners": true,
                        "scale": 1,
                        "showBackground": false,
                        "statType": "CPU",
                        "x": 2280,
                        "y": 1040
                    },
                    {
                        "diskPath": "/",
                        "id": "SystemStat",
                        "layout": "side",
                        "roundedCorners": true,
                        "scale": 1,
                        "showBackground": false,
                        "statType": "Memory",
                        "x": 2280,
                        "y": 1160
                    },
                    {
                        "diskPath": "/",
                        "id": "SystemStat",
                        "layout": "side",
                        "roundedCorners": true,
                        "scale": 1,
                        "showBackground": false,
                        "statType": "Network",
                        "x": 2280,
                        "y": 1280
                    },
                    {
                        "colorName": "primary",
                        "height": 150,
                        "hideWhenIdle": false,
                        "id": "AudioVisualizer",
                        "roundedCorners": true,
                        "scale": 2.697350902673208,
                        "showBackground": false,
                        "visualizerType": "linear",
                        "width": 500,
                        "x": 618,
                        "y": 1001
                    }
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
        "monitors": [
        ],
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
            "keyDown": [
                "Down"
            ],
            "keyEnter": [
                "Return",
                "Enter"
            ],
            "keyEscape": [
                "Esc"
            ],
            "keyLeft": [
                "Left"
            ],
            "keyRemove": [
                "Del"
            ],
            "keyRight": [
                "Right"
            ],
            "keyUp": [
                "Up"
            ]
        },
        "language": "",
        "lockOnSuspend": true,
        "lockScreenAnimations": false,
        "lockScreenBlur": 0,
        "lockScreenCountdownDuration": 10000,
        "lockScreenMonitors": [
        ],
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
        "monitors": [
        ],
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
        "enabledTypes": [
            0,
            1,
            2
        ],
        "location": "top_right",
        "monitors": [
        ],
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
            {
                "action": "lock",
                "enabled": true,
                "keybind": "1"
            },
            {
                "action": "suspend",
                "enabled": true,
                "keybind": "2"
            },
            {
                "action": "hibernate",
                "enabled": true,
                "keybind": "3"
            },
            {
                "action": "reboot",
                "enabled": true,
                "keybind": "4"
            },
            {
                "action": "logout",
                "enabled": true,
                "keybind": "5"
            },
            {
                "action": "shutdown",
                "enabled": true,
                "keybind": "6"
            },
            {
                "action": "rebootToUefi",
                "enabled": true,
                "keybind": "7"
            }
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
        "activeTemplates": [
        ],
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
                "paletteColors": [
                    "#cba6f7",
                    "#fab387",
                    "#94e2d5",
                    "#f38ba8"
                ],
                "path": "/home/lennart/Dokumente/Wallpaper/dark-waves.jpg",
                "useWallpaperColors": false
            }
        ],
        "fillColor": "#000000",
        "fillMode": "crop",
        "hideWallpaperFilenames": false,
        "linkLightAndDarkWallpapers": true,
        "monitorDirectories": [
        ],
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
        "transitionType": [
            "fade",
            "disc",
            "stripes",
            "wipe",
            "pixelate",
            "honeycomb"
        ],
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
     EOF'


### 11. All in one:

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







































////21. [✓] io.github.revisto.drum-machine                                    stable                 i             flathub                17,2 MB / 23,0 MB
22. [✓] io.github.ecotubehq.player                                        stable                 i             flathub                33,4 MB / 34,4 MB
23. [✓] com.nuclearplayer.Nuclear                                         stable                 i             flathub                25,2 MB / 25,4 MB
24. [✓] com.jeffser.Alpaca                                                stable                 i             flathub               646,8 MB / 748,4 MB
25. [✓] org.freedesktop.Platform                                          25.08                  i             flathub               102,8 MB / 253,4 MB
26. [✓] org.onlyoffice.desktopeditors                                     stable                 i             flathub               592,1 MB / 615,5 MB
27. [✓] org.bluej.BlueJ                                                   stable                 i             flathub               143,2 MB / 145,0 MB
28. [✓] io.github.ungoogled_software.ungoogled_chromium                   stable                 i             flathub               161,2 MB / 162,0 MB
29. [✓] io.github.Geocld.PeaSyo4Desk                                      stable                 i             flathub               165,6 MB / 194,5 MB
30. [✓] dev.vencord.Vesktop                                               stable                 i             flathub               119,6 MB / 123,4 MB
31. [✓] com.valvesoftware.Steam                                           stable                 i             flathub                33,7 MB / 35,5 MB
32. [✓] com.spotify.Client                                                stable                 i             flathub               193,4 MB / 193,8 MB
33. [✓] com.lunarclient.LunarClient                                       stable                 i             flathub               133,0 MB / 143,3 MB
34. [✓] com.heroicgameslauncher.hgl                                       stable                 i             flathub               349,3 MB / 356,0 MB
35. [✓] com.github.IsmaelMartinez.teams_for_linux                         stable                 i             flathub               134,3 MB / 144,7 MB
36. [✓] com.brave.Browser                                                 stable                 i             flathub               201,8 MB / 211,4 MB
37. [✓] org.kde.Platform.Locale                                           5.15-25.08             i             flathub               580,1 KB / 400,3 MB
38. [✓] org.kde.Platform                                                  5.15-25.08             i             flathub               273,2 MB / 367,4 MB
39. [✓] org.kde.Platform.Locale                                           6.10                   i             flathub               398,9 KB / 401,3 MB
40. [✓] org.kde.Platform                                                  6.10                   i             flathub               218,4 MB / 387,3 MB
41. [✓] org.prismlauncher.PrismLauncher                                   stable                 i             flathub                40,7 MB / 41,6 MB
42. [✓] org.kde.Platform.Locale                                           6.11                   i             flathub               134,4 KB / 401,6 MB
43. [✓] org.kde.Platform                                                  6.11                   i             flathub               307,9 MB / 405,5 MB
44. [✓] com.rtosta.zapzap                                                 stable                 i             flathub               138,9 MB / 144,5 MB
45. [✓] org.videolan.VLC.Locale                                           stable                 i             flathub               251,0 KB / 14,7 MB
46. [✓] org.videolan.VLC                                                  stable                 i             flathub                45,7 MB / 52,7 MB

Installation abgeschlossen.

/usr/share/sddm/themes/silent 9m
❯ cd

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ 

~
❯ sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s -- --no-marketplace && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply
[sudo] Passwort für lennart: 
Warnung: unzip-6.0-23.1 ist aktuell -- Überspringe
 Es gibt nichts zu tun
Invalid option --no-marketplace

~
❯ sudo pacman -S --needed unzip && curl -fsSL https://raw.githubusercontent.com/spicetify/cli/main/install.sh | sh -s --  && mkdir -p ~/.config/spicetify && printf "[Settings]\nspotify_path = /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/\nprefs_path = /home/$USER/.var/app/com.spotify.Client/config/spotify/prefs\n" > ~/.config/spicetify/config-xpui.ini && sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/ && bash <(curl -sSL https://raw.githubusercontent.com/spicetify/marketplace/main/install.sh) -y && ~/.spicetify/spicetify backup apply && ~/.spicetify/spicetify apply
Warnung: unzip-6.0-23.1 ist aktuell -- Überspringe
 Es gibt nichts zu tun
FETCHING Version 2.44.0
CREATING /home/lennart/.spicetify
DOWNLOADING https://github.com/spicetify/cli/releases/download/v2.44.0/spicetify-2.44.0-linux-amd64.tar.gz
######################################################################## 100.0%
EXTRACTING /home/lennart/.spicetify/spicetify.tar.gz
SETTING EXECUTABLE PERMISSIONS TO /home/lennart/.spicetify/spicetify
REMOVING /home/lennart/.spicetify/spicetify.tar.gz
APPENDING /home/lennart/.spicetify to PATH in /home/lennart/.config/fish/config.fish

spicetify v2.44.0 was installed successfully to /home/lennart/.spicetify
Run 'spicetify --help' to get started
Do you want to install spicetify Marketplace? (Y/n)
y
Starting the spicetify Marketplace installation script..
FETCHING Version 1.0.9
MAKING FOLDER  /home/lennart/.config/spicetify/CustomApps
DOWNLOADING https://github.com/spicetify/marketplace/releases/download/v1.0.9/marketplace.zip
######################################################################## 100.0%
EXTRACTING
COPYING
INSTALLING
 error  Could not detect "prefs" file location
 success  Default config-xpui.ini generated
 warning  Config "custom_apps" unchanged: spicetify-marketplace is not on the list.
 success  Config changed: inject_css = 1
 info  Run "spicetify apply" to apply new config
 success  Config changed: replace_colors = 1
 info  Run "spicetify apply" to apply new config
No theme selected, using placeholder theme
MAKING FOLDER  /home/lennart/.config/spicetify/Themes/marketplace
######################################################################## 100.0%
 success  Config changed: current_theme = marketplace
 info  Run "spicetify apply" to apply new config
 success  Config changed: custom_apps = marketplace
 info  Run "spicetify apply" to apply new config
Added to config!
APPLYING
 error  Cannot detect Spotify "prefs" file location. Please manually set "prefs_path" in config-xpui.ini

~
❯ spicetify apply
fish: Unknown command: spicetify

~
❯ bash -c 'mkdir -p ~/.config/noctalia &&
  cat > ~/.config/noctalia/colors.json << "EOF"
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
  cat > ~/.config/noctalia/plugins.json << "EOF"
  {
  "sources": [
      {
          "enabled": true,
          "name": "Noctalia Plugins",
          "url": "https://github.com/noctalia-dev/noctalia-plugins"
      }
  ],
  "states": {
  },
  "version": 2
  }
    EOF
  cat > ~/.config/noctalia/settings.json << "EOF"
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
      "mprisBlacklist": [
      ],
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
      "autoShowDelay": 150,
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
      "monitors": [
      ],
      "mouseWheelAction": "volume",
      "mouseWheelWrap": true,
      "outerCorners": true,
      "position": "top",
      "reverseScroll": false,
      "rightClickAction": "launcherPanel",
      "rightClickCommand": "",
      "rightClickFollowMouse": true,
      "screenOverrides": [
      ],
      "showCapsule": true,
      "showOnWorkspaceSwitch": true,
      "showOutline": false,
      "useSeparateOpacity": false,
      "widgetSpacing": 6,
      "widgets": {
          "center": [
              {
                  "colorName": "primary",
                  "hideWhenIdle": false,
                  "id": "AudioVisualizer",
                  "width": 200
              },
              {
                  "clockColor": "none",
                  "customFont": "",
                  "formatHorizontal": "HH:mm ddd, MMM dd",
                  "formatVertical": "HH mm - dd MM",
                  "id": "Clock",
                  "tooltipFormat": "HH:mm ddd, MMM dd",
                  "useCustomFont": false
              },
              {
                  "compactMode": false,
                  "hideMode": "transparent",
                  "hideWhenIdle": false,
                  "id": "MediaMini",
                  "maxWidth": 145,
                  "panelShowAlbumArt": true,
                  "scrollingMode": "hover",
                  "showAlbumArt": true,
                  "showArtistFirst": true,
                  "showProgressRing": true,
                  "showVisualizer": false,
                  "textColor": "none",
                  "useFixedWidth": false,
                  "visualizerType": "linear"
              }
          ],
          "left": [
              {
                  "colorizeSystemIcon": "none",
                  "colorizeSystemText": "none",
                  "customIconPath": "",
                  "enableColorization": true,
                  "icon": "rocket",
                  "iconColor": "none",
                  "id": "Launcher",
                  "useDistroLogo": true
              },
              {
                  "compactMode": true,
                  "diskPath": "/",
                  "iconColor": "none",
                  "id": "SystemMonitor",
                  "showCpuCores": false,
                  "showCpuFreq": false,
                  "showCpuTemp": true,
                  "showCpuUsage": true,
                  "showDiskAvailable": false,
                  "showDiskUsage": false,
                  "showDiskUsageAsPercent": false,
                  "showGpuTemp": false,
                  "showLoadAverage": false,
                  "showMemoryAsPercent": false,
                  "showMemoryUsage": true,
                  "showNetworkStats": false,
                  "showSwapUsage": false,
                  "textColor": "none",
                  "useMonospaceFont": true,
                  "usePadding": false
              },
              {
                  "colorizeIcons": false,
                  "hideMode": "hidden",
                  "iconScale": 0.8,
                  "id": "Taskbar",
                  "maxTaskbarWidth": 40,
                  "onlyActiveWorkspaces": true,
                  "onlySameOutput": true,
                  "showPinnedApps": true,
                  "showTitle": false,
                  "smartWidth": true,
                  "titleWidth": 120
              }
          ],
          "right": [
              {
                  "blacklist": [
                  ],
                  "chevronColor": "none",
                  "colorizeIcons": false,
                  "drawerEnabled": true,
                  "hidePassive": false,
                  "id": "Tray",
                  "pinned": [
                  ]
              },
              {
                  "hideWhenZero": false,
                  "hideWhenZeroUnread": false,
                  "iconColor": "none",
                  "id": "NotificationHistory",
                  "showUnreadBadge": true,
                  "unreadBadgeColor": "primary"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Volume",
                  "middleClickCommand": "pwvucontrol || pavucontrol",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "KeyboardLayout",
                  "showIcon": true,
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Bluetooth",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "VPN",
                  "textColor": "none"
              },
              {
                  "displayMode": "onhover",
                  "iconColor": "none",
                  "id": "Network",
                  "textColor": "none"
              },
              {
                  "iconColor": "none",
                  "id": "WallpaperSelector"
              },
              {
                  "colorizeDistroLogo": false,
                  "colorizeSystemIcon": "none",
                  "colorizeSystemText": "none",
                  "customIconPath": "",
                  "enableColorization": false,
                  "icon": "power",
                  "id": "ControlCenter",
                  "useDistroLogo": false
              }
          ]
      }
  },
  "brightness": {
      "backlightDeviceMappings": [
      ],
      "brightnessStep": 5,
      "enableDdcSupport": false,
      "enforceMinimum": true
  },
  "calendar": {
      "cards": [
          {
              "enabled": true,
              "id": "calendar-header-card"
          },
          {
              "enabled": true,
              "id": "calendar-month-card"
          },
          {
              "enabled": true,
              "id": "weather-card"
          }
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
          {
              "enabled": true,
              "id": "profile-card"
          },
          {
              "enabled": true,
              "id": "shortcuts-card"
          },
          {
              "enabled": true,
              "id": "audio-card"
          },
          {
              "enabled": false,
              "id": "brightness-card"
          },
          {
              "enabled": true,
              "id": "weather-card"
          },
          {
              "enabled": true,
              "id": "media-sysmon-card"
          }
      ],
      "diskPath": "/",
      "position": "close_to_bar_button",
      "shortcuts": {
          "left": [
              {
                  "id": "Network"
              },
              {
                  "id": "Bluetooth"
              },
              {
                  "id": "WallpaperSelector"
              },
              {
                  "id": "NoctaliaPerformance"
              },
              {
                  "id": "DarkMode"
              }
          ],
          "right": [
              {
                  "id": "Notifications"
              },
              {
                  "id": "PowerProfile"
              },
              {
                  "id": "KeepAwake"
              },
              {
                  "id": "NightLight"
              }
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
                  {
                      "clockColor": "none",
                      "clockStyle": "minimal",
                      "customFont": "Noto Sans Ethiopic Thin",
                      "format": "HH:mm\\nd MMMM yyyy",
                      "id": "Clock",
                      "roundedCorners": true,
                      "scale": 1.2535640723161134,
                      "showBackground": false,
                      "useCustomFont": true,
                      "x": 1200,
                      "y": 600
                  },
                  {
                      "hideMode": "hidden",
                      "id": "MediaPlayer",
                      "roundedCorners": true,
                      "scale": 1,
                      "showAlbumArt": true,
                      "showBackground": true,
                      "showButtons": true,
                      "showVisualizer": true,
                      "visualizerType": "linear",
                      "x": 40,
                      "y": 1320
                  },
                  {
                      "id": "Weather",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": true,
                      "x": 2280,
                      "y": 80
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "bottom",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "CPU",
                      "x": 2280,
                      "y": 1040
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "side",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "Memory",
                      "x": 2280,
                      "y": 1160
                  },
                  {
                      "diskPath": "/",
                      "id": "SystemStat",
                      "layout": "side",
                      "roundedCorners": true,
                      "scale": 1,
                      "showBackground": false,
                      "statType": "Network",
                      "x": 2280,
                      "y": 1280
                  },
                  {
                      "colorName": "primary",
                      "height": 150,
                      "hideWhenIdle": false,
                      "id": "AudioVisualizer",
                      "roundedCorners": true,
                      "scale": 2.697350902673208,
                      "showBackground": false,
                      "visualizerType": "linear",
                      "width": 500,
                      "x": 618,
                      "y": 1001
                  }
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
      "monitors": [
      ],
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
          "keyDown": [
              "Down"
          ],
          "keyEnter": [
              "Return",
              "Enter"
          ],
          "keyEscape": [
              "Esc"
          ],
          "keyLeft": [
              "Left"
          ],
          "keyRemove": [
              "Del"
          ],
          "keyRight": [
              "Right"
          ],
          "keyUp": [
              "Up"
          ]
      },
      "language": "",
      "lockOnSuspend": true,
      "lockScreenAnimations": false,
      "lockScreenBlur": 0,
      "lockScreenCountdownDuration": 10000,
      "lockScreenMonitors": [
      ],
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
      "monitors": [
      ],
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
      "enabledTypes": [
          0,
          1,
          2
      ],
      "location": "top_right",
      "monitors": [
      ],
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
          {
              "action": "lock",
              "enabled": true,
              "keybind": "1"
          },
          {
              "action": "suspend",
              "enabled": true,
              "keybind": "2"
          },
          {
              "action": "hibernate",
              "enabled": true,
              "keybind": "3"
          },
          {
              "action": "reboot",
              "enabled": true,
              "keybind": "4"
          },
          {
              "action": "logout",
              "enabled": true,
              "keybind": "5"
          },
          {
              "action": "shutdown",
              "enabled": true,
              "keybind": "6"
          },
          {
              "action": "rebootToUefi",
              "enabled": true,
              "keybind": "7"
          }
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
      "activeTemplates": [
      ],
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
              "paletteColors": [
                  "#cba6f7",
                  "#fab387",
                  "#94e2d5",
                  "#f38ba8"
              ],
              "path": "/home/lennart/Dokumente/Wallpaper/dark-waves.jpg",
              "useWallpaperColors": false
          }
      ],
      "fillColor": "#000000",
      "fillMode": "crop",
      "hideWallpaperFilenames": false,
      "linkLightAndDarkWallpapers": true,
      "monitorDirectories": [
      ],
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
      "transitionType": [
          "fade",
          "disc",
          "stripes",
          "wipe",
          "pixelate",
          "honeycomb"
      ],
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
   EOF'
bash: Zeile 843: Warnung: Das in der Zeile 22 beginnende Here-Dokument geht bis zum Dateiende (erwartet wird »EOF«).

~
❯ 

~
❯ source ~/.config/fish/config.fish

~
❯ which spicetify
  spicetify --version
/home/lennart/.spicetify/spicetify
2.44.0

~
❯ find ~/.var/app/com.spotify.Client -name prefs -type f 2>/dev/null
/home/lennart/.var/app/com.spotify.Client/config/spotify/Users/31e2puiwyy4vixfr54mizu3umli4-user/prefs
/home/lennart/.var/app/com.spotify.Client/config/spotify/prefs

~
❯ flatpak info --show-location com.spotify.Client
/var/lib/flatpak/app/com.spotify.Client/x86_64/stable/abf9251b20078af8b596fe0400afeda1adc7b029ee0cee30f5f3556a12059f94

~
❯ ls -la ~/.var/app/com.spotify.Client/config/spotify/
drwxr-xr-x    - lennart 12 Aug 02:54  .
drwxr-xr-x    - lennart 12 Aug 02:54  ..
drwxr-xr-x    - lennart 12 Aug 02:54  Users
.rw-r--r-- 1,1k lennart 12 Aug 02:54 󰡯 prefs

~
❯ spicetify config
Settings
inject_css                    1
spotify_launch_flags          
color_scheme                  
inject_theme_js               1
replace_colors                1
overwrite_assets              0
check_spicetify_update        1
always_enable_devtools        0
spotify_path                  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/
prefs_path                    
current_theme                 marketplace

Preprocesses
remove_rtl_rule               1
expose_apis                   1
disable_sentry                1
disable_ui_logging            1

AdditionalFeatures
extensions
custom_apps                   marketplace
sidebar_config                0
home_config                   1
experimental_features         1

Backup
version                       
with                          

~
❯ 

~
❯ spicetify config prefs_path /home/lennart/.var/app/com.spotify.Client/config/spotify/prefs
 success  Config changed: prefs_path = /home/lennart/.var/app/com.spotify.Client/config/spotify/prefs
 info  Run "spicetify apply" to apply new config

~
❯ spicetify config prefs_path
/home/lennart/.var/app/com.spotify.Client/config/spotify/prefs

~
❯ flatpak kill com.spotify.Client 2>/dev/null

~
❯ spicetify backup
spicetify v2.44.0
 success  Backed up app files                                                                                                                               
 success  Extracted backup                                                                                                                                  
Preprocessing
 success  Fetched remote CSS map                                                                                                                            
 success  Finished extracting V8 snapshot blob to local file
Patching files [250/250] █████████████████████████████████████████████ 100% | 9s
 success  Preprocessing completed
 success  Everything is ready, you can start applying!

~ 9s
❯ spicetify apply
spicetify v2.44.0
 error  Failed to copy raw assets                                                                                                                           
 fatal  unlinkat /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa: permission denied

~
❯ spicetify apply
spicetify v2.44.0
 error  Failed to copy raw assets                                                                                                                           
 fatal  unlinkat /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa: permission denied

~
❯ sudo chmod a+wr -R /var/lib/flatpak/...
[sudo] Passwort für lennart: 
chmod: Zugriff auf '/var/lib/flatpak/...' nicht möglich: Datei oder Verzeichnis nicht gefunden

~
❯ spicetify --help | grep -i flatpak

~
❯ ls -ld /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify
drwxr-xr-x - root 12 Aug 02:49  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify

~
❯ ls -l /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa
.rw-r--r-- 4,1M root  9 Jun 22:29  /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps/login.spa

~
❯ sudo chmod a+wr /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify
  sudo chmod a+wr -R /var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/Apps

~
❯ spicetify apply
spicetify v2.44.0
 success  Copied raw assets                                                                                                                                 
 success  Overwrote themed assets                                                                                                                           
 success  Updated theme's styles                                                                                                                            
 success  Applied additional modifications                                                                                                                  
 success  Refreshed custom apps                                                                                                                             

~
❯ 
