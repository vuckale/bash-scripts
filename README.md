## wifi-switch.sh

### **Description:**
Bash script for enabling/disabling wireless connection on linux based systems using [rfkill](https://linux.die.net/man/1/rfkill). Ideal for binding to a keyboard shortcut.

### **Dependencies**
`rfkill` and `libnotify-bin` <br>

copy paste friendly command for Debian based distros:
```bash
sudo apt install rfkill libnotify-bin
```
copy paste friendly command for Arch based distros:
```bash
sudo pacman -S rfkill libnotify-bin
```

### **Before binding it to a keyboard shortcut you should make script executable:**
```bash
sudo chmod +x wifi-switch.sh
```
### **Bind it to keyboard shortcut using** [xbindkeys](https://linux.die.net/man/1/xbindkeys):

#### 1. Install xbindkeys:

* In debian based distributions run:
```bash
sudo apt install xbindkeys
```
* In arch based distributions run:
```bash
sudo pacman -S xbindkeys
```

#### 2. Generate xbindkeys config file:

```bash
xbindkeys -d > ~/.xbindkeysrc
```

#### 3. Add shortcut and point it to bash script:

* Start `xbindkeys`:
```bash
xbindkeys
```

* Open config file with your favourite editor:

```bash
vi ~/.xbindkeysrc
```

* Add this to .xbindkeys if `wifi-switch.sh` is in your `home` directory:
```
"./wifi-switch.sh"
    alt+y
```
or any other key combination. If `wifi-switch.sh` is not in your home directory point it to it with an absolute path to script.

* Reload the config file:
```bash
killall -s1 xbindkeys
```
or

```bash
xbindkeys --poll-rc
```

#### Further read on configuring xbindkeys:
[https://wiki.archlinux.org/index.php/Xbindkeys](https://wiki.archlinux.org/index.php/Xbindkeys)

### Bind to it to keyboard shortcut in GNOME with GUI:
Go to `Settings` and navigate to `Keyboard/Keyboard Shortcuts`. Scroll down until you see `+` and click on it. A small window with title `Add Custom Shortcut` will open with 3 fileds to set. Set `Name` to whatever you want. Under command enter a ```absolute/path/to/script``` (if `wifi-switch.sh` is in your `home` directory it should look like this ```/home/YourUsername/wifi-switch.sh```). Next click on set shortcut and enter your key combination.
