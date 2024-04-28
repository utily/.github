# Setup Ubuntu 24.04

# Post Installation

```
sudo apt install -y pwgen nmap traceroute git meld gitg curl gnome-tweaks printer-driver-cups-pdf
sudo snap install slack chromium
```

## Node
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
. ~/.bashrc
nvm install node
```

## Code
```
sudo snap install code --classic
```

## REST Clients
```
sudo snap install insomnia postman
```
## Chrome
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
rm google-chrome-stable_current_amd64.deb
```

## Prince XML
```
wget https://www.princexml.com/download/prince_20240418-1_ubuntu22.04_amd64.deb
sudo dpkg -i prince_20240418-1_ubuntu22.04_amd64.deb
rm prince_20240418-1_ubuntu22.04_amd64.deb
```

# Configuration for User

## Git
```
git config --global user.name "<Full Name>"
git config --global user.email "<full.name@example.com>"
```

## NPM & Node Packages
```
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo "export PATH=~/.npm-global/bin:$PATH" >> ~/.profile
source ~/.profile
npm install -g npm-check-updates typescript @typeup/cli wrangler
```
## VS Code User Configuration
```
{
	"diffEditor.ignoreTrimWhitespace": false,
	"git.confirmSync": false,
	"git.autofetch": true,
	"editor.minimap.enabled": false,
	"window.titleBarStyle": "custom",
	"terminal.integrated.enableMultiLinePasteWarning": "never",
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
pushd ~/versioned/utily
for i in flagly transactly langly tidily selectively smoothly isoly library-template worker-template mendly cloudly-router cloudly-http cloudly-rest cloudly-storage cloudly-formdata authly paramly uply persistly gracely
do 
  git clone https://github.com/utily/$i
done
for i in *
do
  pushd $i
  npm install
  popd
done
popd
```
