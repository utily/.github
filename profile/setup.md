# Setup Ubuntu 22.04


# Post Installation

```
sudo apt install -y pwgen nmap traceroute git meld gitg curl chromium-browser gnome-tweaks build-essential
sudo snap install slack --classic
```

## Node
```
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## Code
```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg
```
```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code # or code-insiders
```

## Insomnia
```
# Add to sources
echo "deb [trusted=yes arch=amd64] https://download.konghq.com/insomnia-ubuntu/ default all" \
    | sudo tee -a /etc/apt/sources.list.d/insomnia.list

# Refresh repository sources and install Insomnia
sudo apt-get update
sudo apt-get install insomnia
```
## Chrome
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Prince XML
```
wget https://www.princexml.com/download/prince_14.3-1_ubuntu22.04_amd64.deb
sudo dpkg -i prince_14.3-1_ubuntu22.04_amd64.deb
```

# Configuration

## Git
```
git config --global core.editor gedit
git config --global credential.helper 'cache --timeout=36000'
git config --global user.name "<Full Name>"
git config --global user.email "<full.name@example.com>"
```

## NPM
```
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo "export PATH=~/.npm-global/bin:$PATH" >> ~/.profile
source ~/.profile
npm install -g npm-check-updates typescript
npm install -g @typeup/cli @cloudflare/wrangler
```
## VS Code
```
{
	"diffEditor.ignoreTrimWhitespace": false,
	"git.confirmSync": false,
	"git.autofetch": true,
	"editor.minimap.enabled": false,
	"window.titleBarStyle": "custom",
	"terminal.integrated.enableMultiLinePasteWarning": false,
	"typescript.updateImportsOnFileMove.enabled": "always",
	"window.zoomLevel": 0,
	"debug.onTaskErrors": "debugAnyway",
	"files.associations": {
		"*.tup": "markdown"
	},
	"workbench.colorTheme": "Default Dark+",
	"workbench.panel.defaultLocation": "right",
	"editor.multiCursorModifier": "ctrlCmd",
	"javascript.updateImportsOnFileMove.enabled": "always"
}
```
Install context menu entry in nautilus
```
wget -qO- https://raw.githubusercontent.com/cra0zy/code-nautilus/master/install.sh | bash
```
Enable week numbers
```
gsettings set org.gnome.desktop.calendar show-weekdate true
```

# Repositories
```
mkdir -p ~/versioned/utily
cd ~/versioned/utily
for i in flagly transactly langly tidily selectively smoothly isoly library-template worker-template mendly cloudly-router cloudly-http cloudly-rest cloudly-storage cloudly-formdata authly paramly uply persistly gracely; do 
git clone https://github.com/utily/$i
cd $i
npm install
cd ..
done
```

## Sharing Screen
Sharing screen is disabled if your build uses wayland. To circumvent this do the following:
Open terminal
Check if system uses wayland:
```
echo $XDG_SESSION_TYPE
```
If the command outputs wayland continue with
```
sudo nano /etc/gdm3/custom.conf
```
and uncommit this line:
```
#WaylandEnable=false
```
Save and exit, reboot and checking with first command should display
```
x11
``` 
