**SteamTinkerLaunch** (kurz **stl**) ist ein Linux Programm für den Steam Client
welches einem ermöglicht Programme und Einstellungen für Spiele schnell und komfortabel zu konfigurieren *(siehe [Features](#Features))*

Aufgrund der vielseitigen Konfigurations Struktur ist es sowohl einfach einzurichten als auch sehr flexibel.

## Verwendung

### Generelle Verwendung
**stl funktioniert sowohl mit linux nativen Spielen als auch mit Spielen die Proton verwenden**
*(Einige Features (z.B. [ReShade](#ReShade)) sind nur für Spiele die Proton verwenden verfügbar)*

#### Steam Startoption
Um **stl** als Steam Startoption zu verwenden genügt es **stl** folgendermaßen in die Startoption Kommandozeile einzutragen:
'stl %command%'

![stl starter](https://github.com/frostworx/repo-assets/blob/master/gifs/stl-command.gif)

*Ein kleines Script, welches diesen Eintrag für jedes Spiel in der Steam Bibliothek setzt kann man [hier finden](https://gist.github.com/frostworx/36bd76e705a0c87af523fa57cfeebaf8)*

#### Steam Kompatibilitätswerkzeug
**stl** kann auch als Kompatibilitätswerkzeug eingerichtet werden, indem man einfach folgende **stl** Kommandozeilenoption verwendet:

`stl compat add` *(fügt stl unter compatibilitytools.d/SteamTinkerLaunch hinzu)*
`stl compat del` *(enfernt stl von compatibilitytools.d/SteamTinkerLaunch)*
`stl compat (get)` *(überprüft den aktuellen Status von compatibilitytools.d/SteamTinkerLaunch)*

Wenn `add`  gewählt wird und stl von einem anderen Pfad als ursprünglich ausgeführt wird, wird der Symlink automatisch aktualisiert.

*(Wie immer wenn ein a Kompatibilitätswerkzeug hinzugefügt wurd, muss Steam neugestartet werden damit das Werkzeug verfügbar ist)*

![stl steam compat](https://github.com/frostworx/repo-assets/blob/master/gifs/stl-steam-compat.gif)

*(Es ergibt zwar keinerlei Sinn, aber ein Spiel startet auch wenn stl sowohl als Startoption als auch als Kompatibilitätswerkzeug konfiguriert ist)*

### Spiel-spezifische Verwendung:
Wenn ein Spiel gestartet wird, erscheint ein kleiner Requester.
Wird innerhalb der konfigurierten Wartenzeit (default 2 Sekunden) die Leertaste gedrückt, öffnet sich das [Settings Menü](#Settings-Menu) wo alles bequem konfiguriert werden kann.
Ist man mit Konfigurieren fertig (oder wenn der Requester timeouted) startet das Spiel normal mit allen Tools und Werkzeugen die man eingestellt hat.

## Installation
Dies ist nur ein einzelnes Bash Script. Einfach nach Belieben irgendwohin kopieren (z.B. '/usr/local/bin/') und ausführbar machen:
`chmod +x stl`
Die beiliegenden Order mit optionalen Konfigurationsdateien können entweder nach '/usr/share/stl/' kopiert (bevorzugter Ort)
oder aber auch automatisch mit git heruntergeladen werden (default wenn '/usr/share/stl/' nicht existiert).

Auf Arch Linux kann stl einfach über [AUR](https://aur.archlinux.org/packages/steamtinkerlaunch) installiert werden *(z.B. mit yay)*:

`yay -S steamtinkerlaunch`

[![Packaging status](https://repology.org/badge/vertical-allrepos/steamtinkerlaunch.svg)](https://repology.org/project/steamtinkerlaunch/versions)

## Schnellstart
Wenn **stl** zum ersten Mal gestartet wird, erstellt es seine Standard [Konfiguration](#Configuration) Struktur.
Nahezu alles kann mit dem eingebauten [Settings Menü](#Settings-Menu) konfiguriert werden, optional aber auch mit einem grafischen Editor.
Es ist ratsam mit dem individuellen Einrichten im [Settings Menü](#Settings-Menu) anzufangen
*(für eine grundlegende Konfiguration sind die beiden Tabs [Default Settings](#Default-Template-Config)und [Globale Einstellungen](#Global-Config))*.

## Features

*(keine spezielle Reihenfolge)*

* **[ENV Variables](#ENV-Variables)** können ganz einfach für jedes einzelne Spiel gesetzt werden (z.B. `PROTON`* , `DXVK`* , `MANGOHUD`, `RADV_PERFTEST`, `WINE`...)
* **[Custom Program](#Custom-Program)** benutzerdefinierte Programme können vor oder statt dem eigentlichen Spiel gestartet werden (auch Windows Exen)
* **[winetricks](#Winetricks)** startet winetricks kann vor dem Spiel *(GUI oder auch silent)*
* **[winecfg](#Winecfg)** startet winecfg vor dem Spiel
* **[GameMode](#GameMode)** Starte/Stoppe gamemoderun pro Spiel
* **[Notifier](#Notifier)** Starte/Stope Desktop Benachrichtigungen pro Spiel
* **[Strace](#Strace)** zum einfachen Debuggen von Spielen
* **[Editor Hotkey](#Editor)** zum Bearbeiten der Spielekonfiguration
* **[Editor URL](#Editor)** öffnet automatisch eine URL zu dem gestarteten Spiel wenn der Editor geöffnet wird
* **[ReShade](#ReShade)** automatische Installation und Konfiguration
* **[Depth3D](#Depth3D)** automatische Shader Installation
* **[vkBasalt](#vkBasalt)** grundlegende vkBasalt Konfiguration
* **[SBS-VR](#Side-by-Side-VR)** startet automatisch reguläre Spiele im Stereo3D Modus in VR!
* **[Tweaks](#Tweaks)** community Mini Konfigurationdateien (sogenannte [Tweakfiles](#Tweakfiles)) um automatisch problematische Spiele sofort starten zu können - können auch [Tweak Commands](#Tweak-Commands) ausführen
* **[Auto Tweaks](#Auto-Tweaks)** Automatischer Import von Spielekonfigurationen aus anderen Platformen
* **[Nyrna](#Nyrna)** Starte/Stoppe Nyrna pro Spiel
* **[ReplaySorcery](#ReplaySorcery)** Starte/Stoppe ReplaySorcery pro Spiel
* **[NetMon](#Network-Monitoring)** rudimentäres Netzwerk Monitoring
* **[Boxtron](#Boxtron)** kann direkt mit einer Steam `DOSBox` Kategorie verwendet werden
* **[Roberta](#Roberta)** kann direkt mit einer Steam `ScummVM` Kategorie verwendet werden
* **[Luxtorpeda](#Luxtorpeda)** kann direkt mit einer Steam `Luxtorpeda` Kategorie verwendet werden
* **[Vortex Mod Manager](#Vortex)** kann direkt mit einer Steam `Vortex` Kategorie verwendet werden. Siehe [Video of usage](#stl-Vortex-gif)
* **[GFWL/xlive](#GFWL)** Automatische Unterstützung für Spiele die GFWL benötigen
* **[WMP10](#WMP10)** Automatische Unterstützung für WMP10 Installation
* **[self maintaining configs](#self-maintaining-configs)** klont optional dieses Repo als Ersatz für eine systemweite Installation
* **[GameConqueror](#GameConqueror)** öffnet automatisch im gameconqueror (scanmem gui) die Spiele Exe beim Start des Spiels
* **[Custom User Start/Stop scripts](#Start-Stop-Scripts)** optionales Starten von benutzerdefinierten Scripten wenn das Spiel startet und endet
* **[GameScope](#GameScope)** Starte/Stoppe gamescope pro Spiel
* **[Settings Menu](#Settings-Menu)** einfache Konfiguration von nahezu allen Einstellungsmöglichkeiten im eingebauten Settings Menü
* **[native Support](#Native-Games)** Unterstützung von Linux nativen Spielen
* **[Steam Compatibility Tool](#Steam Compatibility Tool)** kann als [Steam Kompatibilitätswerkzeug](#Steam-Launch-Option) and as [Steam Compatibility Tool](#Steam-Compatibility-Tool) verwendet werden
* **[Proton Selection](#Proton-Selection)** zwischen verschiedenen Proton-Versionen wechseln, automatisch benutzerdefinierte Proton Versionen runterladen...
* **[Multi Language](#Multi-Language-Support)** Multi-Language Unterstützung


## Requirements
*(keine spezielle Reihenfolge)*

Programme die für eine grundlegende Funktionalität benötigt werden:
- bash *(die einzige getestete Shell)*
- git
- unzip
- wget
- wmctrl
- xdotool
- xprop
- xrandr
- xwininfo
- [Yad](https://github.com/v1cont/yad). Das *(standardmäßig verwendete)* [Settings Menü](#Settings-Menu) und das [Tray Icon](#Tray-Icon) funktionieren ausschliesslich mit yad.
  Der [Editor Dialog](#Editor-Dialog), der als eingeschränkte Alternative zum [Settings Menü](#Settings-Menu) verwendet werden kann funktioniert auch mit zenity.
  *(demnach sollte das bei Distributions Paketen eine `oder-Abhängigkeit` sein)*
  Getestet wurde nur yad 7.2 auf Arch linux *(zumindest Debian (-Derivate) liefern standardmäßig eine sehr alte yad Version aus, die nicht funktioniert - siehe #98)*
   
Programme die für optionale zusätzliche Features benötigt werden *(keine spezielle Reihenfolge)*:
- [strace](#Strace)
- [Gamemode](#GameMode)
- [MangoHud](#MangoHud)
- [winetricks](#Winetricks)
- vr-video-player um reguläre Spiele in Stereo3D in VR ([SBS-VR](#Side-by-Side-VR) spielen zu können)
- ein grafischer Text Editor und optional einen Internetbrowser. Siehe [global.conf](#Global-Config)
- [vkBasalt](#vkBasalt)
- [Nyrna](#Nyrna)
- [ReplaySorcery](#ReplaySorcery)
- netstat aus dem net-tools Paket für rudimentäres Netzwerk-Monitoring
- [Boxtron](#Boxtron) und dosbox um dos Spiele optional mit einem linux nativen dosbox zu starten
- ScummVM um optional unterstützte Spiele nativ mit [Roberta](https://github.com/dreamer/roberta) zu starten
- [luxtorpeda-dev](https://github.com/luxtorpeda-dev/luxtorpeda) or [Luxtorpeda](https://github.com/dreamer/luxtorpeda) um optional unterstützte Spiele mit einer Linux nativen Binary zu starten
- optional wine für optionalen [Vortex](#Vortex) Support
- [GameConqueror/scanmem](#GameConqueror) zum optionalen Cheaten
- [GameScope](#GameScope)
- zenity *(siehe Beschreibung für yad weiter oben)*
- cabextract *(zur Zeit nur benötigt um die [WMP10](#WMP10) setup exe auszupacken)*
- lsusb *(für einen optionalen [SBS-VR](#Side-by-Side-VR) Check ob ein VR Headset gefunden wurde)*


## Configuration
Alle Konfigurations Dateien sind in sich geschlossen dokumentiert und wachsen ständig, daher ist hier nicht jede Option extra dokumentiert.
Für einen groben Überblock empfiehlt es sich die [Features](#Features) anzuschauen oder einfach mal durch das
[Settings Menü](#Settings-Menu) zu blättern, was so ziemlich alles abdeckt was verfügbar ist.

### Settings Menu
Nahezu alles kann mit dem eingebauten Settings Menü konfiguriert werden *(benötigt [Yad](https://github.com/v1cont/yad))*
Jeder Eintrag hat einen Tooltip mit einer knappen Beschreibung.

Das Menü hat *(momentan)* folgende Tabs:

 - Tab 1 ist das **SPIELE EINSTELLUNGEN** Menü für das ausgewählte Spiel (entweder über Steam gestartet oder über Kommandozeile) *([`$STLGAMECFG`](#Game-Configurations))*
 - Tab 2 ist das **STANDARD EINSTELLUNGEN** Menü, die Vorlage für alle neu erstellten **SPIELE EINSTELLUNGEN** *([`$STLDEFGAMECFG`](#Default-Template-Config))*
 - Tab 3 ist das **GLOBALE EINSTELLUNGEN** Menü, in dem alle grundlegenden Einstellungen vorgenommen werden können *([`$STLDEFGLOBALCFG`](#Global-Config))*
 - Tab 4 ist das **VORTEX EINSTELLUNGEN** Menü, für die Vortex Konfiguration *([`$STLVORTEXCFG`](#Vortex-Configuration))*

Die Menü Optionen werden für **alle Tabs** gleichzeitig angewandt!:
- **BEENDEN** - schließt das Settings Menü ohne irgendetwas zu speichern
- **EDITOR MENÜ** - Öffnet ein kleines Editor Menü von wo aus alle bearbeitbaren relevanten Konfigurations Dateien mit dem [Editor](#Editor) geöffnet werden können
- **NEU LADEN** - verwirft alle Änderungen und lädt die Konfigurations Dateien neu 
- **SPEICHERN UND NEU LADEN** - speichert alle Änderungen und lädt die Konfiguration neu
- **SPEICHERN UND BEENDEN** - speichert alle Änderungen und beendet das Settings Menü

#### Disable Settings Menu
Wenn man es vorzieht einen Texteditor zu benutzen, oder wenn man Probleme mit 'yad' hat, kann man im **GLOBALE EINSTELLUNGEN** Tab oder in der [global.conf](#Global-Config) `USEGUI` auf "zenity" setzen.
**stl** verwendet dann zenity statt yad.
Statt dem [Settings Menü](#Settings-Menu) öffnet zenity den [Editor Dialog](#Editor-Dialog), in welchem man wählen kann, welche Konfigurations Dateien man bearbeiten möchte.
Dies trifft ebenfalls auf die [command line](#via Command Line) zu.

#### Settings Menu Theme

![stl Settings Menu](https://github.com/frostworx/repo-assets/blob/master/gifs/stl-2.0-settings.gif)

Wenn man das beiliegende selbstgestrickte stl-steam gtk-css theme aktiviert, wird es nach `~/share/themes/stl-steam/gtk-3.0/gtk.css` installiert.
Um sich so gut wie möglich optisch einzugliedern, versuchtes das Steam Theme nachzuahmen.
De- aktiveren kann man es im [Settings Menü](#Settings-Menu).
Jedes gtk Programm welches von **stl** aus aufgerufen wird, verwendet das Theme ebenfalls (z.B. winetricks).
Das css ist kein vollständiges Theme und sieht in anderen gtk Programmen wahrscheinlich unfertig aus.
Verbesserungen können gerne beigetragen werden.

#### Opening the Settings Menu

##### On Game Launch
Wenn ein Spiel gestartet wird, öffnet sich ein kleines Fenster und wartet `WAITEDITOR` Sekunden auf eine Benutzereingabe *(entweder Leertaste drücken oder `OK` klicken)*.
Reagiert man entsprechend, öffnet sich das Settings Menü direkt mit den Einstellungen für das gestartete Spiel im Tab 1 (siehe [Settings Menü](#Settings-Menu))
Setzt man `WAITEDITOR` auf 0, start **stl** das ausgewählte Spiel sofort ohne Fenster.

Ist der Wert `MAXASK` definiert ([global.conf](#Global-Config)), kann man den Requester `MAXASK` Mal wegklicken
bevor `WAITEDITOR` für das Spiel automatisch auf 0 gesetzt wird.
Lässt man den Requester timeouten, zählt das nicht als wegklicken.

Der "Wegklick Zähler" wird direkt im [Game specific configuration file](#User-Configurations) als `ASKCNT` gespeichert
und wird auf 0 resettet sobald `MAXASK`erreicht und `WAITEDITOR` auf 0 gesetzt wurde.

Verwendet man als `USEGUI` "zenity" öffnet sich der [Editor Dialog](#Editor-Dialog) statt dem [Settings Menü](#Settings-Menu), aber die Parameter sind dieselben.

##### via Command Line
Das Settings Menü kann auch direkt per Kommandozeile geöffnet werden:
`stl settings` öffnet das Menü mit dem Platzhalter SteamAppID `31337` als Standard.
Ein weiterer optionaler Kommandozeilen parameter kann entweder eine SteamAppID sein, oder `last` um das zuletzt gespielte Spiel, welches in `LASTRUN` gespeichert wurde zu öffnen.
Verwendet man als `USEGUI` "zenity" öffnet sich der [Editor Dialog](#Editor-Dialog) statt dem [Settings Menü](#Settings-Menu), aber die Parameter sind dieselben.

#### Gui Window Size
Ist `SAVESETSIZE` im **GLOBALE EINSTELLUNGEN** Tab oder in der [global.conf](#Global-Config) aktiviert *(standardmäßig aktiviert)*,
werden sämtliche Änderungen an **stl** Fenstergrößen beim Schließen des entsprechenden Fensters gespeichert.
Diese Funktion benötigt xwininfo. Alle Auflösungen werden in die [gui config file](#Gui-Config) geschrieben.

### Tray Icon
Verwendet man yad hat **stl** auch über ein Tray Icon, welches automatisch startet und so lange verfügbar ist wie **stl** (oder das gestartete Spiel) läuft.
Das Tray Icon kann im **GLOBALE EINSTELLUNGEN** Tab oder in der [global.conf](#Global-Config) deaktivert werden *(standardmäßig aktiviert)*.
Rechts Klick öffnet das Menü
Mittlerer Mausklick beendet das Tray Icon.

#### Tray Icon Buttons
- "Pick Window Name" *(pick the window name and save it into the [Game Config](#Game-Configurations))*
- "Get Active Window Name" *(waits 5 seconds and saves the window name of the active window into the [Game Config](#Game-Configurations))*
- "Kill Proton Game" *(kills the currently running Proton game by killing its wineserver)*
- "Pause/Unpause active window" *(waits 5 seconds and un-/pauses the process of the window which is currently active)*

### Configuration Locations

#### User Configuration

The main user configuration directory `STLCFGDIR` can be found under
`$HOME/.config/stl` (or `XDG_CONFIG_HOME/stl` if `XDG_CONFIG_HOME` is set).

When started for the first time **stl** will initially create a default configuration structure in its configdir `STLCFGDIR`


#### Systemwide Configuration
The systemwide configuration directory `SYSTEMSTLCFGDIR` can be found under `/usr/share/$PROGCMD` *(/usr/share/stl/)*

All configs used here are read first, so user configs override them if required.
System-wide configs help to keep configuration easy and get things to work ootb.
f.e. there are preconfigured [Steam Category](#Steam-Categories),
custom per-game [registry](#Registry) files, which are autodetected and applied *(when `REGEDIT` is 1)*,
*community contributed* [tweaks](#Tweaks) which make sure specific games work ootb using the provided configuration options,
*community contributed* [sbs tweaks](#SBS-Tweaks) which make sure specific games work ootb in [SBS-VR](#Side-by-Side-VR) mode using the provided configuration options

##### self maintaining configs
With the variable `DLGLOBAL` being set to 1 (it is by default) **stl**
uses systemwide configurations from the directory `STLDLDIR/stl` and also git pulls this repo into there (max once per day).
This **only** is used when the systemwide configuration directory `SYSTEMSTLCFGDIR` does not exist at all!
As almost no distro provides a stl package, the idea is that the user only has to copy stl into `$PATH`
and still can make use of the bundled config files without having to install them manually.
No executable files will be used from here!

Auto-generated [auto tweaks](#Auto Tweaks) imported from other platform will be loaded before global configs, so global configs override them by default.


### Default Template Config
`STLDEFGAMECFG` *(`$STLCFGDIR/default_template.conf`)*

Contains the default configurations options used as template for every new game specific configfile.
Most options are disabled by default. To deploy appropriate global options early this file should be adjusted early.

### Global Config
`STLDEFGLOBALCFG` *(`$STLCFGDIR/global.conf`)*

Contains universal configuration options used all games, f.e.
file paths, command line options for supported 3rd party programs, but also general "behavior" settings
*(f.e. [Logs](#Logs) mode or timeout for the [Settings Menu](#Settings-Menu) and [Editor](#Editor)WAITEDITOR)*

### Gui Config
`STLGUICFG` *(`$STLCFGDIR/gui.conf`)*
All [window sizes](#Gui-Window-Size) will be stored in this config when `SAVESETSIZE` is enabled *(by default it is)*.

The initial resolution of all windows is calculated based on the screen-resolution.

### Url Config
`STLURLCFG` *(`$STLCFGDIR/url.conf`)*
For a transparent and easy overview all URLs available in **stl** are stored in here.
As all variables are in plaintext, there's no extra URLs Tab in the [Settings Menu](#Settings-Menu)
but the file can always be selected in the [Editor Dialog](#Editor-Dialog).

### Game Configurations

`$STLGAMECFG` *(`$STLCFGDIR/gamecfgs/$SteamAppId.conf`)*

When starting a game using **stl** the game specific config file is searched in `STLGAMEDIR`
and created if not available from the default config file *(which in turn is automatically created as well if not found)*.
Additional individual configs can be loaded via multiple different [Tweaks](#Tweaks).
Any option configured in here and also in [global.conf](#Global-Config) is overridden by this config.

### Steam Categories
**stl** parses the Steam categories of the started game and examines if a associated **stl** configuration file exists
under the same name (case-sensitive, but written uppercase in Steam **!**)

If a configuration file is found it is initialized as additional config file.

This makes it easy to create "Configuration categories" by
- simply creating a Steam Category
- creating a categories configfile under the same name and defining settings in it
- adding a game to the category to use those settings automatically

Category Configuration Files are searched in the [User Configurations](#User-Configuration) `STLCATEGORYDIR` *(`STLCFGDIR`/categories)*
or in the [system-wide](#Systemwide-Configuration) dir `GLOBALCATEGORYDIR` *(`SYSTEMSTLCFGDIR/categories)`*
where some category files are already preconfigured:

a game in the corresponding category
- **DOSBox.conf** is started automatically with linux native dosbox provided by [Boxtron](#Boxtron)
- **Luxtorpeda.conf** is started automatically with linux native binary provided by [Luxtorpeda](#Luxtorpeda)
- **ReShadeVR.conf** is started automatically in [SBS-VR](#Side-by-Side-VR) mode using [ReShade](#ReShade)
- **SBS-VR.conf** is started automatically in [SBS-VR](#Side-by-Side-VR) mode without Shader (for games with builtin Stereoscopic3D support)
- **ScummVM.conf** is started automatically with linux native scummvm provided by [Roberta](#Roberta)
- **Vortex.conf** is started automatically with the [Vortex](#Vortex) Mod Manager
- **vkVR.conf** is started automatically in [SBS-VR](#Side-by-Side-VR) mode using [vkBasalt](#vkBasalt) and 
- **Installer.conf** won't be started at all, but a requester lets one choose an exe which is started instead.
- **Cheat.conf** [GameConqueror](#GameConqueror) is automatically started with the game.

Multiple Category Configuration Files are possible, they are loaded one after another, with the last one overriding settings also found in the previous files.
All settings which are also configured in `$STLGAMECFG` are overridden (but not overwritten).

The function can be diabled per game with the option `CHECKCATEGORIES` 

### Tweaks

All different user writable tweakfiles live in their own subdirectory under `TWEAKDIR` *("$STLCFGDIR/tweaks")*

If a tweak config `TWEAKCFG` ( `SteamAppID.conf` ) in `GLOBALTWEAKDIR` or `USERTWEAKDIR` (overrides global) is found its settings
overrides the settings in the [`$STLGAMECFG`](#Game-Configurations).
By means of this function it is be possible to contribute tweak configs required to get games to work hazzlefree out of the box to the community.
With `CREATETWEAKS` a default template tweak file is autogenerated on game launch, to make creating one a bit easier.

Some systemwide tweaks can already be used (see [Installation](#Installation)).

If you use/create tweaks make sure to retest your game with later proton versions without the tweak and report upstream if the bug is fixed!
The used proton Version is automatically written into the tweak file when created with `CREATETWEAKS`.
User tweak-files in `USERTWEAKDIR` override global tweaks in `GLOBALTWEAKDIR`, [Autotweaks](#Auto Tweaks)

#### Tweakfiles
An example tweakfile looks like this:

`stl/tweaks/user/8080.conf:`

```
#########
#GAMENAME=Kane and Lynch Dead Men
#GAMEEXE=Launcher
#GAMEID=8080
#PROTONVERSION=proton-5.0-10-rc4
#########
WINETRICKSPAKS=d3dx9_31 d3dx9_34
PROTON_NO_ESYNC=1
PROTON_NO_FSYNC=1
NOGFWL=1
```

Explained in detail:
When the game "Kane and Lynch Dead Men" is started **stl** will find its tweakfile *(8080.conf = SteamAppId.conf)*
and apply following configurations:

- d3dx9_31 d3dx9_34 will be installed via wintricks
- PROTON_NO_ESYNC and PROTON_NO_FSYNC will both be set to 1
- gfwl will be removed

This works completely automatically and transparent without any user interaction.
*(of course the first start will need some time when aditional packages are installed)*

### Tweak Commands

It is also possible to define a script under `TWEAKCMD` *(f.e. in `TWEAKCFG`)* which should be started before the game launch.
This is especially useful when it is necessary to move or rename game files to get a game working.
When a `TWEAKCMD` is defined **stl** will check if it finds the file
- as absolute path
- in the system tweak directory
- in the user tweak directory
- in the gamedir

In case the file was found **stl** checks if a `TWEAKFILE` is defined in the `TWEAKCMD` file.
This comes in handy when the script requires a specific file (f.e. a custom game exe) which is not available for everybody.
With this little "dependency check" the tweak file is simply skipped if the file was not found and the tweak can still be shared in the community.
Not exported variables are not available in the script, but usually none should be required (yay might want to check `env` for available vars)

- `GPFX="$STEAM_COMPAT_DATA_PATH/pfx"` :can be used as variable for the games `WINEPREFIX`
- `GFD="$(awk -F 'common' '{print $1}' <<< "$PWD")common/$(awk -F 'common' '{print $NF}' <<< "$PWD" | cut -d'/' -f2)"`: can be used for the base game dir

### SBS Tweaks

Game specific config files `SteamAppID.conf` both in and [system-wide](#Systemwide-Configuration) *(`GLOBALSBSTWEAKDIR`)* and [User Configurations](#User-Configuration) *(`SBSTWEAKDIR`)*
with optimal settings for [SBS-VR](#Side-by-Side-VR) (f.e. launcher skips using the game exe as custom command).

Here's an example config for trine 2 `STLCFGDIR/sbs/35720.conf`

```
#########
#GAMENAME=Trine 2
#GAMEEXE=trine2_launcher
#GAMEID=35720
RUN_CUSTOMCMD=1
CUSTOMCMD=trine2_32bit.exe
ONLY_CUSTOMCMD=1
GAMEWINDOW=Trine 2
```

Means, when `RUNSBSVR` is not 0 in the main Trine2 config file it will autodetect above sbs tweak config and use the defined variables:
Trine 2 won't start it's original launcher (`ONLY_CUSTOMCMD=1`), but only the custom command `trine2_32bit.exe` and will wait for a `Trine 2` window to open in **VR**

So in general sbs configs are automatically loaded when found and override settings in the main config
so you just have to enable `RUNSBSVR` in `STLCFGDIR/gamecfgs/35720.conf` and everything else is configured automatically.

### Auto Tweaks

**stl** allows to import required game config files from several other platforms.
The path to those autogenerated tweaks is
`AUTOTWEAKDIR` *("$TWEAKDIR/auto")* with "$platform" as subdirectory.

All platforms from where configurations shall be imported need to be listed in the
global `AUTOTWEAKS` variable.
All enabled autotweak platform tweak files are loaded before all other configs, so it is always possible to override them later.
This is necessary, as aparrently not all autogenerated configs can be tested.

When `ATVALIDATE=0` the order in `AUTOTWEAKS` decides in which order they are loaded.
The later a config is found the more important it is, as it discards the configs found from previous platforms.
With `ATVALIDATE` being disabled there is apparently no control over what will be actually loaded.

When the variable `ATVALIDATE` is >0 a requester will pop up
asking the user if he wants to open the autocreated config with the editor
*(also her in the same order as the platforms are listed in `AUTOTWEAKS`)*
Afterwards another requester asks if the config should be loaded or skipped.
When multiple Auto Tweak Configs are found the requesters are opened for all of them,
but only the last accepted config is actually loaded!

If `IGNOREAUTOTWEAKS=1` is set in the current gameconfig `$STLGAMECFG` all autotweaks are skipped automatically.
If `ATADOPT=1` is set in the current gameconfig a requester will pop up when th game exited
asking if the used AutoTweak config should be converted into a regular tweakconfig.
Autotweaks will be disabled in this new config then.


#### Creating Auto Tweaks

Auto Tweaks are either autocreated on game launch automatically (if the chosen `AUTOTWEAKS` support the game)
or can be .


**stl** will download an active repo on the first run and prepare the datafiles for better searching if required.
To keep downloads as low as possible, on later runs the already downloaded data will be re-used where possible.

When started directly from Steam **stl** searches for a gamefix for the current SteamAppID.
If one is found the gamefix will be converted into a **stl** autotweakfile under `AUTOTWEAKDIR/protonfixes`.
This config is then applied like described in [Auto Tweaks](#Auto Tweaks) above.

Creating Auto Tweaks via **stl** command line:

`stl autotweaks PLAFTORM (optional steamid)`

Will autogenerate all tweak files for every parsible game of platform PLATFORM or just for the optional SteamAppID
  
Example:

`stl autotweaks lutris`
Creates for all supported Games Autotweak files in `AUTOTWEAKDIR/lutris`

`stl autotweaks lutris 883710`

Creates only for game 883710 an Autotweak file.

**Depending on the platform stl filters several original configuration options.
If you think something important is missing please open an issue!**

#### ProtonFixes
Some [protonfixes](https://github.com/simons-public/protonfixes) gamefixes are marked as deprecated inside protonfixes.
Those and a handful more (mostly those copying/changing files) are skipped automatically.
When run from terminal those skipped will be listed.
To see how Auto Tweak files are created read general describtion from above [here](# Creating Auto Tweaks)

Currently following options are imported into the Auto Tweak file:

- winetricks packages
- alternative executables
- env variables
- dll overrides
- game command line arguments

#### Lutris
[Lutris](https://github.com/lutris/lutris) is pretty huge and supports many different platforms.
**stl** uses multiple different filters to extract the steam-relevant games.
If you think something important was filtered out please open an issue!
Lines which were not filtered out, but were not used as well can be logged
*(into "/tmp/LUTWEAKDEBUG-raw.txt" (all) and
"/tmp/LUTWEAKDEBUG-raw.txt" (after another filter, which sorts out some more unused lines))*

by setting the variable `LUATDEBUG=1` directly within **stl**

Currently following options are imported into the Auto Tweak file:
- winetricks packages
- commandline arguments
- env variables
- dll overrides
- pulseaudio latency
- xlive
- mfplat
- basic script creation *(`TWEAKCMD`)*
- downloads and their extraction will be added commented out in the autotweak file

To see how Auto Tweak files are created read general describtion from above [here](# Creating Auto Tweaks)


### vortex.conf
See [Vortex Configuration](#Vortex-Configuration)


### Downloads
The `STLDLDIR` directory stores all downloads started through **stl**
As of writing those are
[Depth3D](#Depth3D) shader files
[Vortex](#Vortex) the installation setup exe
[ReShade](#ReShade) ReShade itself and required d3dcompiler dlls
[Auto Tweaks](#Auto-Tweaks) downloads for all enabled Auto Tweaks are stored in here
[GFWL/xlive](#GFWL) xlive replacement
[self maintaining configs](#self-maintaining-configs) stl itself will be downloaded here when self-maintaining-configs are used
[Proton packages](#Proton) Proton packages


### Logs
Logs are written into the `LOGDIR` defined in the [global.conf](#Global-Config).
The verbosity of the logfile depends on `WRITELOG` *(write logfile if not 0, increase verbosity from 1-2 (1:less, 2:all))*
also defined in the [global.conf](#Global-Config).
There are several logfiles, those which are written mostly are the game specific ones *($SteamAppId.log)*

## Features in detail:

#### Proton Selection
**stl** provides the option to easily choose a specific Proton Version per game, by simply selecting one from an autogenerated dropdown Menu in
the Game Settings Tab of the [Settings Menu](#Settings-Menu).

The function can be en-/disabled in the [Settings Menu](#Settings-Menu) *(by default disabled!)*, but if **stl** is used as [Steam Compatibility Tool](#Steam-Compatibility-Tool) with a Proton game,
a force override flag disables the set flag, as it obviously requires any Proton version to start. In this case the latest official Proton Version is set by default.

The List of available Proton Versions is generated on the first **stl** launch *(in `/dev/shm`)* and recreated when a new Proton Version was added on the fly.

**stl** searches in the following sources for Proton Versions to generate the list:
- user installed compatibility tools *(~/.steam/steam/compatibilitytools.d/)*
- system-wide compatibility tools *(/usr/share/steam/compatibilitytools.d)*
- official proton versions installed via Steam in default SteamLibrary *(~/.steam/steam/steamapps/common/)*
- official proton versions installed via Steam in additional SteamLibrary Paths *(the additional Paths are extraced from ~/.steam/steam/config/config.vdf)*
- a [custom Proton List](#Custom-Proton-List)

##### Custom Proton List
The optional custom Proton List `CUSTOMPROTONLIST` in [`STLCFGDIR`](#User-Configuration)
is used as additional source for custom Proton Versions for inclusion into the autogenerated Proton Version (dropdown) List.

###### Adding Entries to the Custom Proton List

There are several methods to add new entries to the list
*(besides editing it manually / via [Editor Dialog](#Editor-Dialog))*:

###### Adding local Custom Proton
a locally installed Custom Proton can be added either by

- using the button `Add local Custom Proton` in the Game Settings Tab of the [Settings Menu](#Settings-Menu)
- via command line: `stl addcustomproton` or just `stl acp` 
  *(accepting an absolute path to a proton executable as optional argument)*

With either method a `proton` file can be selected via file-requester
and an optional "proton version name" can be entered in a separate field.

###### Download Custom Proton
Custom Proton packages can also be downloaded and added by
- using the button `Download Custom Proton` in the Game Settings Tab of the [Settings Menu](#Settings-Menu)
- via command line: `stl addcustomproton dl` or just `stl acp dl` 
  *(accepting direct download URL  as optional argument)*
  
With either method a download requester with a dropdown menu is opened.
The menu is autogenerated, by parsing all `CP_*` *(Custom Proton)* URLs from the [Url Config](#Url-Config)
for proton packages. Currently following Custom builds are parsed *(feel free to recommend one if you think something is missing)*

- [GloriousEggroll](/https://github.com/GloriousEggroll/proton-ge-custom)
- [Proton TKG](https://github.com/Frogging-Family/wine-tkg-git)
- [Protola](https://github.com/Patola/wine)

Packages *(`tar.*`, `zip`)* containing a `proton` file will be extracted and added to the List of available Proton Builds.

###### Automatic Proton version
Using the variable `WANTPROTON` in configs and tweaks it is possible to automatically request a specific proton version to be used with the corresponding game.
If `AUTOPULLPROTON` is enabled *(it is by default)* **stl** will automatically download the specific proton version and install it.


#### Multi-Language Support
**stl** Multi-Language Support *(currently with [these languages](https://github.com/frostworx/steamtinkerlaunch/tree/master/lang))*.

At least the default language file (english) needs to be found, else **stl** will exit with an error.
**stl** searches both in the [Systemwide Configuration](#Systemwide-Configuration) and in the [User Configuration](#User-Configuration) for language files,
where those in the latter have a higher priority *(so copying a systemwide file to improve it is possible)*

Every language found can be selected from the Language Dropdown Menu in the Global Settings Tab of the [Settings Menu](#Settings-Menu).
*(a change requires a restart to take effect)*.

To give also the option to get a translated description in freshly created **stl** configfiles
it is also possible to define an available language or an absolute path to a valid language file with the `lang=` command line option.

When no language file was found as a last resort **stl** will download its own projectpage and use the language file from there.

*(every language file simply consists of multiple variables defining a text, so to contribute a translation,
simply duplicate one of the existing ones and translate all variables inside)


#### Custom Program

When enabled you can start custom programs easily with the following per-game config options:

- `RUN_CUSTOMCMD`: set to 1 or 2 *(see below)* to start the custom command `CUSTOMCMD`
- `CUSTOMCMD`: start this custom command
- `CUSTOMCMD_ARGS`: start `CUSTOMCMD` command with those args
- `ONLY_CUSTOMCMD`: set to 1 to only start `CUSTOMCMD` and not the game command itself
- `FORK_CUSTOMCMD`: set to 1 to fork the custom `CUSTOMCMD` into the background and continue with starting `%command%`

If only `RUN_CUSTOMCMD` is enabled, but `CUSTOMCMD` is empty, a requester will open where a executable file can be selected.
When `RUN_CUSTOMCMD` is 1 this selected file is automatically written into the [in game configfile `$STLGAMECFG`](#Game-Specific-Configuration).
When `RUN_CUSTOMCMD` is 2 this selected file is only started this time without saving the exe into the config.
This is especially useful for installers *(see provided [Steam Category](#Steam-Categories) 'Installer')*

If string `CUSTOMCMD` can't be found as file in either `PATH`, in game dir or as absolute filepath the requester will open as well.

#### Start Stop Scripts
If commands are defined in `USERSTART` `USERSTOP` they will be executed when a game starts/ends.
Of course the user is responsbile for what is executed here and needs take care that it both works and exits correctly!

Both scripts make use of following commandline arguments:
- SteamAppID as argument1
- the absolute path to the game exe as argument2
- and the WINEPREFIX of the game as argument 3

#### Winetricks
[Winetricks](https://wiki.winehq.org/Winetricks)
GUI:
Set `RUN_WINETRICKS` to 1 to start winetricks gui before game launch

Silent winetricks installation:
- `WINETRICKSPAKS`: install all packages in WINETRICKSPAKS silently with winetricks

#### Winecfg
- `RUN_WINECFG`: set to 1 to start winecfg before game launch


#### Boxtron

[Boxtron](https://github.com/dreamer/boxtron):

The global configs `BOXTRONCMD` and `BOXTRONARGS` in the [global.conf](#Global-Config) need to be set correcty initially.
It should not be necessary to change the default `ROBERTAARGS`.
Defaults are:
**
BOXTRONCMD=/usr/share/boxtron/run-dosbox
BOXTRONARGS=--wait-before-run
**
which is at least valid if you are on Arch Linux and installed boxtron from AUR.

To start a game with boxtron either set `USEBOXTRON` in the [gameconfig `$STLGAMECFG`](#Game-Configurations) or put the game into the [steam category](#Steam-Categories) "DOSBox"
Alternatively duplicate the file to a different name which you want to use as category name, ideally into [`STLCATEGORYDIR`.](#Steam-Categories).

#### Roberta

[Roberta](https://github.com/dreamer/roberta):

The global configs `ROBERTACMD` and `ROBERTAARGS` in the [global.conf](#Global-Config) need to be set correcty initially.
It should not be necessary to change the default `ROBERTAARGS`.
Defaults are:
**
ROBERTACMD=$HOME/.local/share/Steam/compatibilitytools.d/roberta/run-vm
ROBERTAARGS=--wait-before-run
**
which is at least valid if you installed roberta manually.

To start a game with roberta either set `USEROBERTA` in the [gameconfig `$STLGAMECFG`](#Game-Configurations) or put the game into the [steam category](#Steam-Categories) "ScummVM"
Alternatively duplicate the file to a different name which you want to use as category name, ideally into [`STLCATEGORYDIR`.](#Steam-Categories-dir).

#### Luxtorpeda
[Luxtorpeda-dev](https://github.com/luxtorpeda-dev/luxtorpeda) or (untested) the [main branch](https://github.com/dreamer/luxtorpeda)

The global configs `LUXTORPEDACMD` and `LUXTORPEDAARGS` in the [global.conf](#Global-Config) need to be set correctly initially.
It should not be necessary to change the default `LUXTORPEDAARGS`.

Defaults are:
**
LUXTORPEDACMD=$HOME/.local/share/Steam/compatibilitytools.d/luxtorpeda/luxtorpeda
LUXTORPEDAARGS=wait-before-run
**
which is at least valid if you installed roberta manually.

To start a game with luxtorpeda either set `USELUXTORPEDA` in the [gameconfig `$STLGAMECFG`](#Game-Configurations) or put the game into the [steam category](#Steam-Categories) "Luxtorpeda"
Alternatively duplicate the file to a different name which you want to use as category name, ideally into [`STLCATEGORYDIR`.](#Steam-Categories-dir).
The luxtorpeda-dev dev was so kind to add a manual-download option in v20, so if native game files are missing they are downloaded before the actual game launch now.
Therefore it is recommended to use the lastest luxtorpeda-dev version.

#### Native Games
**stl** also works with native linux games.
The implementation is pretty new, so please report back if there are false positives in the detection. Currently the first distinction is if "waitforexitandrun" appears in the game %command%.
If yes, **stl** assumes we have a proton game. Now, when another check finds "steamapps/common" (without "waitforexitandrun") a linux game is assumed, and the *(now generic)* launchSteamGame function is started.
Looks like only proton games have the Variable `STEAM_COMPAT_DATA_PATH`, so if it is missing several features are disabled in the setLinGameVals function,
as they do not work with native linux games (f.e. [ReShade](#ReShade)) *(still visible in the Settings though)*. The Game and Exe Path Variables are differently extracted as well when `STEAM_COMPAT_DATA_PATH` is missing.


#### GFWL
Some games still depend on GFWL which is discountinued and doesn't work under wine.
With the variable `NOGFWL` set to 1 for a game **stl** takes care that
everything is configured automatically to start the game ootb.
If the dependant xlive.dll is missing it will be downloaded automatically
( [from Ultimate-ASI-Loader](https://github.com/ThirteenAG/Ultimate-ASI-Loader/releases) )
into `$STLDLDIR/xlive/` and installed into the gamedir.
**stl** ships already several tweak files, which enable `NOGFWL` for several games (f.e.: "Fable 3 (105400)", "Resident Evil 5 (21690)", "Kane and Lynch Dead Men (8080)", "FlatOut Ultimate Carnage (12360)"

#### WMP10
Games which depend on WMP10 can be played by setting the variable `HACKWMP10` to 1.
[Tweak](#Tweaks) with automatic support already implemented for

**
Giana Sisters Twisted Dreams (223220)
Giana Sisters - Rise of the Owlverlord (246960)	
**

#### Vortex
[Vortex Mod Manager](https://github.com/Nexus-Mods/Vortex)

##### Starting Vortex:
Vortex can be used without any **stl** configuration and will work ootb without zero configuration.

There are 3 different ways to start Vortex:

###### Start Vortex using Steam Category
Just create a "Vortex" [Steam Category](#Steam-Categories) and add your (Vortex compatible) game to it and start the game regularly.
Vortex will start, with the selected game preconfigured and ready to mod
and when you exit Vortex the selected game will start normally (with your mods).

###### Start Vortex using commandline:
**stl Vortex commandline options:**
`stl vortex install`: starts a full Vortex installation with all dependencies
`stl vortex start`: starts Vortex
`stl vortex getset`: lists all configured Vortex settings
`stl vortex stage`: will open a dialog where a vortex stage directory can be added
                    *(accepts absolute path to the (to be created) directory as argument to skip the dialog)*

###### Start Vortex by enabling it in the Settings Menu:
The `VORTEXMODE` option in the Game Tab of the [Settings Menu](#Settings-Menu) has the following modes:
- "disabled": Vortex won't be used
- "normal": Vortex will be started regularly
- "quickstart": Vortex will be started but some checks are skipped
- "editormode": Vortex will be started in quickstart mode, but the selected game won't start after Vortex is closed

##### stl Vortex gif
![stl Vortex in action](https://github.com/frostworx/repo-assets/blob/master/gifs/stl-vortex.gif)

**Installation?**
If Vortex is not yet installed, it will be installed on the first launch, so the first launch will need some time (mostly depends on dotnets mind of its own... maybe 5 minutes).
Alternatively you can also install it via command line (see below).
If using proton-wine for `VORTEXWINE` (which is default if it is not configured) the `WINEPREFIX` user is "steamuser" (as always with proton wine).
When you switch to a wine version which doesn't patch the username to "steamuser" your user-settings are emtpy of course.
**stl** will not symlink in between those two users!

**Functionality**:
Some settings are preconfigured, to make this working without any user configuration, but of course all of the settings can be as well configured if you want.

##### Vortex Configuration

**stl** uses an extra vortex directory inside `STLCFGDIR` defined under `STLVORTEXDIR`
This directory contains the Vortex configfile `STLVORTEXCFG` *(`STLCFGDIR`/vortex/vortex.conf`)*

Here are the main configuration options, for a full list, simply look into the [Settings Menu](#Settings-Menu)
- `VORTEXWINE`: the wine binary used for Vortex - **defaults to wine from Newest Official Proton installed**
- `VORTEXPREFIX`:the `WINEPREFIX` path used for Vortex - **default is `STLVORTEXDIR/wineprefix`**
- `VORTEXDOWNLOADPATH`: the path where all Vortex downloads should be stored - **default is `STLVORTEXDIR/downloads`**
- `VORTEXINSTALL`: download and install Vortex automatically if set to 1 **default enabled**
- `DISABLE_AUTOSTAGES`: set to 1 if you don't want **stl** to try to auto set/create [Vortex Stages](#Vortex-Stages) directories **default 0**

##### Vortex Stages

Vortex uses 2 main [Deployment_Methods](https://wiki.nexusmods.com/index.php/Deployment_Methods) to enable Mods for the managed games.
"Hardlink Deployment" and "Symlink Deployment". Symlink Deployment doesn't work under wine, so Hardlink is required (and automatically set for every game from **stl**, although it is default anyway)
Those "Hardlinks" only work if the "Staging directory" is on the same partition as the game (yes the same physical partition, not the same "windows drive in wine).
As Steam Library directories can be on multiple partitions a "Staging directory" is required for every one of them.

###### Automated (zeroconf) `VORTEXSTAGELIST` configuration
When you start a game **stl** will parse on which mount point it actually lies.
Then it tests if it can create/write a "Vortex" directory in the root directory of the partition.
If it fails to create a directory in the previous step, it tests next if it can create/write a "Vortex" directory
directly in the "Steam Library" directory of the started game besides the "steamapps" directory.

The first succeeding directory will be added automatically to the `VORTEXSTAGELIST` list
and will be used from now on as "Staging directory" automatically for all games lying on the same partition.
So after you have started one "Vortex" game from each of your "Steam Library" partitions the `VORTEXSTAGELIST` variable is ready for all of your games.
The only exception is the partition where your steam is installed ("/" or "/home" if you have an extra /home/partition).
Here the default "Vortex Staging directory" is `STLVORTEXDIR/staging` instead.

Other additional paths can be added easily, just make suggestions.
If you don't want that automation just set `DISABLE_AUTOSTAGES` to 1 and set them manually instead:

###### Manual `VORTEXSTAGELIST` configuration
Simply add one writable directory per Steam Library partition you want to use to the `VORTEXSTAGELIST`.
This can also be done directly by using the `add Vortex Stage button` in the Vortex Tab of the [Settings Menu](#Settings-Menu).

##### Script Extender
Several games *(Skyrim, Fallout flavours)* have many mods which depends on a special "Script Extender" program ("SE").
Unfortunately those "SE" programs don't [work with default proton since some time](https://github.com/ValveSoftware/Proton/issues/170).
When **stl** detects one of those "SE exe" files in the game dir, a requester will pop up with following options:
- start the regular game exe
- start the regular game exe and save the decision (so don't ask again)
- start the found "SE exe"
- start the found "SE exe" and save the decision (so don't ask again)

When choosing "SE exe" make sure the [selected Proton Version](#Proton-Selection) is can actually run the exe!

*(The "don't ask again" option `SELAUNCH` can't be set in the [Settings Menu](#Settings-Menu)
and must be removed manually from the [game config](#Game Configurations) -f.e. via [Editor Dialog](#Editor-Dialog)*


#####  Some additional Notes

- On the first start Vortex warns that it is started with admin privileges. Very likely wine related, just click it away, it won't pop up again
- I tested ~25 games and they worked ootb, feel free to open an issue for a not (automatically) working game if you think this is a **stl** bug. (Nehrim doesn't seem to work (yet))
- It was pretty much work to get this into the current state, but although I tested a lot there still might be glitches and problems.
  Also Vortex can stop working under linux/wine anytime after an update (as it already did before).
  Don't complain and rant when it doesn't work as expected (anymore) (as it happened already before with other Vortex-linux solutions),
  but try to help fixing the issue instead then (no offense, but imho linux already had better times regarding this).

#### Registry

Auto-applying registry files:
If `REGEDIT` is
- set to 0 it will be skipped completely
- set to 1 a registry file `$SteamAppId.reg` will be searched and used in `GLOBALREGDIR` and `STLREGDIR`
- set to anything else the file `$REGEDIT` will be searched and used in `GLOBALREGDIR` and `STLREGDIR`

when a registry file from above was applied `REGEDIT` will be set to "0" in the game config, to skip regedit on the following game starts

#### Side-by-Side VR

SBS-VR (regular games side-by-side in **VR**):
--------------------------------------------

To play games with **built in** side-by-side you just have to set `RUNSBSVR` to 1 (or greater to delay the VR start for `RUNSBSVR` seconds) in the game specific config,
everything else is done (almost) automatically:

- start SteamVR
- start the game (game settings required to enable sbs are not automatically enabled! added a tweakcmd for **Crysis 2** though )
- start [vr-video-player](https://git.dec05eba.com/vr-video-player)
- when exiting the game, vr-video-player wil be closed as well.

There are also two quickstart options to choose from to directly start regular games in SBS mode without any further configuration
by auto-enabling side-by-side with the shader [Depth3D](#Depth3D):

 - `SBSVRVK`: set to 1 as shortcut to enable all required flags for SBSVR with [vkBasalt](#vkBasalt)
 - `SBSVRRS`: set to 1 as shortcut to enable all required flags for SBSVR with [ReShade](#Reshade)

Where Reshade has more features and vkBasalt is probably more stable, because it works natively.

Before Starting SteamVR **stl** checks if a HMD is present *(using lsusb)*.
If none was found the SBS VR mode is cancelled and if `SBSVRRS` was supposed to start ReShade is disabled as well.
The game starts regularly in pancake mode subsequently.

**stl** goes through several functions to automatically find the current window id
*(and for later use also the game window name, to make starting SBS VR for the game faster)*
This works mostly very good, but some games start own launchers before the actual game.
Then autodetecting the correct window is almost impossible, and the window name has to be set manually as `GAMEWINDOW`.
If autodetecting failed for whatever reason, it is still possible to pick the game window name again, by using the [Tray Icon](#Tray-Icon)

The vr-video-player author was so kind to accept a little patch, to work better with **stl**.
It is possible to live zoom in and out and the zoom state is written into a temporary file, which **stl** picks up.
The value is stored in the internal [SBS Tweak](#SBS-Tweaks) config (also when changed) and read from there from now on.

To make switching between game- and vr-video-player window easier (with hmd) there is also the option `TOGGLEWINDOWS`:
When enabled, all visible windows will minimize on game start, and will maximize back when game finishes
So switching between the windows is easily possible with *Alt+Tab*.
`TOGGLEWINDOWS` is also enabled by default in the **VR** [Steam Categories](#Steam-Categories) *(ReShadeVR,SBS-VR,vkVR.conf)*

#### GameMode
[gamemode](https://github.com/FeralInteractive/gamemode)
- `USEGAMEMODERUN`: set to 1 to start game with gamemoderun
*([User Configuration](#User-Configuration) overrides [system-wide configuration](#Systemwide-Configuration))*

#### Notifier
Set `NOTY` to your notifier to draw some start/stop **stl** messages

#### MangoHud
[MangoHud](https://github.com/flightlessmango/MangoHud)
Set `MANGOHUD` to 1 to enable mangohud *(does nothing in stl itself, but just exports the upstream variable)*

#### Nyrna
[Nyrna](https://github.com/Merrit/nyrna)
Set `RUN_NYRNA` to 1 to enable nyrna while game is running 
*([User Configuration](#User-Configuration) overrides [system-wide configuration](#Systemwide-Configuration))*

#### ReplaySorcery
[ReplaySorcery](https://github.com/matanui159/ReplaySorcery)
Set `RUN_REPLAY` to 1 to enable replay-sorcery while game is running 
*([User Configuration](#User-Configuration) overrides [system-wide configuration](#Systemwide-Configuration))*

#### GameConqueror
[GameConqueror](https://github.com/scanmem/scanmem)
Set `RUN_GAMCON` to 1 to automatically start GameConqueror when the game starts.
The game exe will be loaded into GC automatically,
but also can be overridden with `GAMCONWAITEXE` *(f.e. for games starting a launcher)*.
When the game exits GameConqueror will be closed automatically as well.

As the gameconqueror startscript uses pkexec and asks for more permissions, the default
executable is set to `GAMCON=/usr/share/gameconqueror/GameConqueror.py` in the global config.
Enabling GameConqueror is also possible by simply adding the game to the "Cheat" [[Steam Category](#Steam-Categories).

Some games *(afaik mostly multiplayer)* are not cheat-safe and could lead to a ban, so **be careful with cheating**!

#### GameScope
[GameScope](https://github.com/Plagman/gamescope)
Set `USEGAMESCOPE` to 1 to automatically start GameScope when the game starts, either per game or globally.
The commandline arguments used *(`GAMESCOPE_ARGS`)* can be configured both per game and globally as well.

#### Toggle Open Windows
minimize all open windows on game start and maximize them when game exited using wmctrl
- `TOGGLEWINDOWS`: toggle visibility of all open windows on start/stop

#### Strace
If `STRACERUN` is set to 1 **stl** will write a strace log of the launched game
strace is launched with the commandline arguments found in `STRACEOPTS`.

When `STRACERUN` is enabled make sure
`/proc/sys/kernel/yama/ptrace_scope` is set to 0.
else your user will get access denied when trying to attach a process.
Either 
`echo 0 > /proc/sys/kernel/yama/ptrace_scope`
as root or enable it persistent in sysctl.

#### Network Monitoring
Basic Network Traffic Monitor
- `NETMON`: program to record game network-traffic with arguments `NETOPTS` - used when enabled

If `NETMON` is set the basic network traffic of the selected game is monitored and written into `NETMONDIR`.
duplicate lines are unique sorted at the end.

#### ReShade
[ReShade](https://reshade.me)
Set `INSTALL_RESHADE` to 1 to automatically install reshade into the selected game dir.
Set `USERESHADE` to 1 to start game with ReShade enabled

If `DOWNLOAD_RESHADE` is set to 1 all required files for ReShade are [downloaded](#Downloads) once into `RESHADESRCDIR`
of course you can install all files manually as well. make sure to rename all files correctly:

**64bit** `d3dcompiler_47.dll`: -> d3dcompiler_47_64.dll
**32bit** `d3dcompiler_47.dll`: -> d3dcompiler_47_32.dll
`ReShade64.dll`, `ReShade32.dll`: renaming not required as they will be placed in the gamedir under the required name

The required architecture is autodetected from the game.exe and the matching files are copied from `RESHADESRCDIR` into the selected game dir
both downloadfiles and basic configuration were taken from [r/linux_gaming](https://www.reddit.com/r/linux_gaming/comments/b2hi3g/reshade_working_in_wine_43) 

If `USERESHADE` is disabled and the corresponding game is started, the previously installed ReShade dll will be renamed, so ReShade is disabled when the game starts.
When `USERESHADE` is re-enabled the renamed dll will be re-activated.

#### vkBasalt
[vkBasalt](https://github.com/DadSchoorse/vkBasalt)
- `ENABLE_VKBASALT`: set `ENABLE_VKBASALT` to 1 to start the game with vkbasalt *(does nothing in stl itself, but just exports the upstream variable)*
- `VKBASALT_CONFIG_FILE`: the vkbasalt source config file - it points per default to `STLCFGDIR/vkBasalt.conf` and is autogenerated if not found
The autogenerated `VKBASALT_CONFIG_FILE` points to the files from `RESHADE_DEPTH3D` so it should have been at least checked out once with `CLONE_DEPTH3D`

#### Depth3D
[Depth3D](https://github.com/BlueSkyDefender/Depth3D)
Mostly useful in combination with [SBS-VR](#Side-by-Side-VR).
Set `RESHADE_DEPTH3D` to 1 to install ReShade Depth3D Shader into gamedir
If `CLONE_DEPTH3D` is set to 1 the git repository will be automatically cloned/pulled (only when `RESHADE_DEPTH3D=1`) to `DEPTH3DSRCDIR` in [Downloads](#Downloads)

With `RESHADE_DEPTH3D` enabled `Overwatch.fxh`, `SuperDepth3D.fx`, `SuperDepth3D_VR.fx` from Depth3D are copied to the gamedir.
When the game started just create a initial profile by selecting the autodetected `SuperDepth3D_VR.fx`

#### Editor
Config files can optionally be opened with the texteditor `STLEDITOR` if desired, either by accepting a requester (for editing Tweakfiles) or by opening
Configfiles within the [Editor Dialog](#Editor-Dialog) started directly or as submenu of the [Settings Menu](#Settings-Menu).

If xdg-open is configured as `STLEDITOR` or if the configured editor is not found, **stl** tries to autoconfigure an installed texteditor.
*(first trying to find it through 'xdg-mime query', then check binary availability in this order: geany, gedit, leafpad, kwrite)*

Set `OPENEDITORURL` to 1 to additionally open the `EDITORURL` url for the game in your `BROWSER` when starting the editor from the [Editor Dialog](#Editor-Dialog).
*(by default the url `$OPENEDITORURL/$SteamAppID` is opened, if this doesn't work with the url you want to open just open an issue)*

#### Editor Dialog
A little File selection requester allowing to choose which config files to open with the [Editor](#Editor).
The requester works with both `USEGUI` set to 'yad' and 'zenity'.
If `USEGUI` is set to "zenity" in the [global config](#Global-Config) the [Editor Dialog](#Editor-Dialog) will open directly instead of the [Settings Menu](#Settings-Menu)
when selected [on Game Launch](#On-Game-Launch) and also [via Command Line](#via-Command-Line).


#### ENV Variables
Literally every env variable can be set in [gameconfig `$STLGAMECFG`](#Game-Configurations) and [system-wide configuration](#Global-Config),
making it pretty easy to tinker with important ones *(f.e `PROTON`* , `DXVK`* , `MANGOHUD`, `RADV_PERFTEST`, `WINE`...)*
The Possibilities Are Endless...

## Game Launch Speed
**stl** has pretty much to check, but when everything is configured, several option-checks can be disabled (per game)
to speed up the actual game start process.
Here are some examples which improve the start notably *(all settings can be configured in the [Settings Menu](#Settings-Menu))*
- set `WAITEDITOR` to `0` [on Game Launch](#On-Game-Launch)
- set `CHECKCATEGORIES` to `0` if the Game has no [Steam Category](#Steam-Categories) Tweak anyway
- set `SAVESETSIZE` to `0` when all windows have their optimal [size](#Gui-Window-Size)

## Contribution

**Any contribution is welcome and everybody can help!**

- help improving the **README**
- create [Tweakfiles](#Tweakfiles) and share them with the community, either open a pull request, or open an issue if you don't like git too much :)
- add new functions & fix bugs (please open a pull request)
- bugreports (please also post the relevant stl logfile)
- spread the word *(**stl** is still pretty unknown - the more people know it the more can help to improve it)*
