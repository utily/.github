# Setup Ubuntu 26.04


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
sudo snap install --classic code
```

## Insomnia
```
sudo snap install --classic insomnia
```
## Chrome
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
rm google-chrome-stable_current_amd64.deb
```

## Prince XML
```
wget https://www.princexml.com/download/prince_17-1_ubuntu26.04_amd64.deb
sudo dpkg -i prince_17-1_ubuntu26.04_amd64.deb
sudo apt --fix-broken install
rm prince_17-1_ubuntu26.04_amd64.deb
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
npm install -g @typeup/cli wrangler
sudo apt install printer-driver-cups-pdf
```
## VS Code
```
{
	"editor.tabSize": 2,
	"editor.insertSpaces": false,
	"diffEditor.ignoreTrimWhitespace": false,
	"git.confirmSync": false,
	"git.autofetch": true,
	"editor.minimap.enabled": false,
	"window.titleBarStyle": "custom",
	"terminal.integrated.enableMultiLinePasteWarning": "never",
	"js/ts.updateImportsOnFileMove.enabled": "always",
	"window.zoomLevel": 0,
	"debug.onTaskErrors": "debugAnyway",
	"files.associations": {
		"*.tup": "markdown"
	},
	"workbench.colorTheme": "Dark+",
	"workbench.panel.defaultLocation": "right",
	"editor.multiCursorModifier": "ctrlCmd",
	"chat.agentSkillsLocations": {
		"~/versioned/utily/tools/ai/skills": true
	},
	"files.autoSave": "afterDelay",
	"chat.viewSessions.orientation": "stacked",
	"workbench.activityBar.location": "top"
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
