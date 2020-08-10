# os-settings 
Personal configs for dev setup on MacOS or Linux (Ubuntu). 💻
> Notes: These settings apply to base systems unix. Spactacle is only works on Mac (for resize and adjust windows use [super]+arrows on Linux).

### Dev Setup

#### List of setup
| Tools                 | MacOS / Linux (Ubuntu)                                                                                                                                                                                                |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Custom settings       | Mojave / Ant (gtk-theme) - [Dracula](https://draculatheme.com/gtk/)                                                                                                                                                   |
| ->*Extensions*        | [iStat Menus](https://bjango.com/mac/istatmenus/) / Tweak, Plank, No dash in Overview, Unite, User Themes, Vitals, [Flat-remix](https://github.com/daniruiz/flat-remix)                                               |
| Package manager       | [Homebrew](https://brew.sh/) / Apt-get (default)                                                                                                                                                                      |
| Terminal              | [iTerm2](https://iterm2.com/) / [Hyper](https://hyper.is/), [Dracula](https://draculatheme.com/), [Z Shell (zsh framework)](https://github.com/ohmyzsh), [Spaceship](https://github.com/denysdovhan/spaceship-prompt) |
| ->*Plugins*           | git, dnf, [sh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting), [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions), emoji                                              |
| ->*Descompression*    | cowsay, fortune                                                                                                                                                                                                       |
| Quick launcher        | [Alfred](https://www.alfredapp.com/) / [Albert](https://albertlauncher.github.io/)                                                                                                                                    |
| Web browser           | Firefox                                                                                                                                                                                                               |
| ->*AdBlocks*          | [uBlock Origin](https://ublockorigin.com/)                                                                                                                                                                            |
| ->*Badger*            | [Privacy Badger](https://privacybadger.org/)                                                                                                                                                                          |
| ->*Style*             | [Stylus](https://github.com/openstyles/stylus) (dark github, wikpedia etc)                                                                                                                                            |
| ->*Security*          | [Http Everwhere](https://www.eff.org/https-everywhere)                                                                                                                                                                |
| ->*Devtools*          | [Vue](https://github.com/vuejs/vue-devtools), [React](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)                                                                                                 |
| Version control       | Git                                                                                                                                                                                                                   |
| Window resize         | [Spactacle](https://www.spectacleapp.com/) / --                                                                                                                                                                       |
| Node package managger | npm, [yarn](https://yarnpkg.com/), nvm                                                                                                                                                                                |
| Code editor           | VS Code (and Atom)                                                                                                                                                                                                    |
| VS Code extensios     | [see all extensions here](https://github.com/andrenespolon/vscode-settings)                                                                                                                                           |
| Environment settings  | Dock, dev folder                                                                                                                                                                                                      |
| Break timer           | [Dejal](https://www.dejal.com/) / [Break Timer](https://breaktimer.app/)                                                                                                                                              |
| Databases             | [MongoDB](https://docs.mongodb.com/manual/installation/) (and GUI [Robo3T](https://robomongo.org/))                                                                                                                   |
| Design APIs           | [Insomnia](https://insomnia.rest/)                                                                                                                                                                                    |
| Prototypes            | [Adobe XD](https://www.adobe.com/br/creativecloud.html) / --                                                                                                                                                          |
| Connect               | Skype, Slack, Discord                                                                                                                                                                                                 |
| Study                 | [DevDocs](https://devdocs.io/)                                                                                                                                                                                        |
---

#### Commands for MacOS
```bash
sudo xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew update
brew install git # install git first
brew cask install iterm2 # update iterm2 settings: theme, color etc.
brew install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# if not set zsh default shell, then run
# chsh -s $(which zsh)
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme" # and then, set ZSH_THEME="spaceship" in your .zshrc
brew install fortune cowsay 
brew cask install spectacle
brew cask install alfred # set cmd+sapce to launch alfred
brew cask install firefox # set preferences and install extensions
brew install node
npm install -g yarn
npm install -g eslint
mkdir ~/dev
brew cask install visual-studio-code skype # update vscode settings and extensions
# install manually: iStas Menus, Dejal
```

#### Commands for Linux (Ubuntu)
```bash
sudo apt install gnome-tweak-tool
sudo apt install plank # and then set it in ~/.config/autostart
# set firefox preferences and install extensions (gnome extensions)
sudo apt install git # install git first
# install manually: theme Ant/Dracula
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme" # and then, set ZSH_THEME="spaceship" in your .zshrc
sudo apt-get install fortune cowsay # and also fortune-br
sudo apt install albert
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
nvm install stable
npm install -g yarn
npm install -g eslint
mkdir ~/dev
sudo snap install insomnia # or by .deb daownload
sudo snap install code skype --classic
```