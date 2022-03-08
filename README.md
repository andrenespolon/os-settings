# os-settings

These are my personal configs for dev setup on MacOS or Linux (Ubuntu). 💻

> Note: These settings apply to based in unix systems. Some app maybe not working in Windows.

## Dev Setup `(macOs | ubuntu)`

#### System extensions

- [MenuMeters](https://github.com/yujitach/MenuMeters) | [Vitals]()**

- [Quick View Calendar](https://quickviewcalendar.com/)

- [Dropbox](https://www.dropbox.com)

- [OneDrive](https://www.microsoft.com/pt-br/microsoft-365/onedrive/download)

- [Spectacle](https://www.spectacleapp.com/)*

- [Dejal - Time Out](https://www.dejal.com/timeout/)* | [Break timer](https://breaktimer.app/)

- [Alfred](https://www.alfredapp.com/)* | [Albert](https://albertlauncher.github.io/)

- [Google Chrome](https://www.google.com/intl/pt-BR/chrome/) and [Firefox]()
  
  - [uBlock Origin](https://ublockorigin.com/)
  
  - [Privacy Badger](https://privacybadger.org/)
  
  - [Http Everwhere](https://www.eff.org/https-everywhere)
  
  - [Vue devtools](https://github.com/vuejs/vue-devtools), [React devtools](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/) and [Redux devtools](https://github.com/reduxjs/redux-devtools)
  
  - [DevDocs](https://devdocs.io/)

#### Development environment

- [Homebrew](https://brew.sh/index_pt-br)*

- [Git](https://git-scm.com/)

- [nvm](https://github.com/nvm-sh/nvm) (npm and yarn)

- [Visual Studio Code](https://code.visualstudio.com/download) ([see all extensions here](https://github.com/andrenespolon/vscode-settings))

- [Iterm2](https://iterm2.com/)*
  
  - shell: [z shell (oh-my-zsh)](https://github.com/ohmyzsh)
  
  - theme: [Spaceship](https://github.com/denysdovhan/spaceship-prompt)
  
  - plugins: git, dnf, [sh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting), [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
  
  - fun: cowsay, fortune

- [Insomnia](https://insomnia.rest/)

- XCode*, Transporter* and [Android Studio](https://developer.android.com/studio) (for RN)

- [Arduino IDE](https://www.arduino.cc/)

- [GraphiQL](https://github.com/graphql/graphiql)

- [Reactotron](https://github.com/infinitered/reactotron)

- [MongoDB Compass](https://www.mongodb.com/try/download/compass), [Robo 3T](https://robomongo.org/)

- [Beekeeper Studio](https://www.beekeeperstudio.io/)

- [Docker](https://www.docker.com/)
  
  - containers: mysql, sql server etc.

#### Productivity

- [Notion](https://www.notion.so/product)

- Teams, Word, Excel, PowerPoint and OneNote

- [Tempo](https://www.yourtempo.co/)*◊

- [Fig](https://fig.io/)*

- [Discord](https://discord.com/download)

- [Twitch](https://www.twitch.tv/downloads)

- [Slack](https://slack.com/intl/pt-br/)

- [Draw.io](https://drawio-app.com/)

- Adobe XD and Figma

#### Bash commands

**Compile C++ files `compile <file>`**

```shell
#!/bin/bash
# Author: André Nespolon
# compile <file_name>
compile() {
  g++ -o $1 $1.cpp
}
```

**Testing C++ code (brute force) `tcc <number_of_tests>`**

```shell
#!/bin/bash
# Author: André Nespolon
# tcc <number_of_testes>
tcc() {
  NUM_TEST=$1
  for ((i = 1; i <= $NUM_TEST ; i++)); do
    echo $i
    ./gen $i > int
    # ./a < int > out1
    # ./brute < int > out2
    # diff -w out1 out2 || break
    diff -w <(./a < int) <(./brute < int) || break
  done
}
```

**Delete folders not empty (recursively) `del <folder>`**

```shell
#!/bin/bash
# Author: André Nespolon
# del <folder>
del() {
 DIR=$1
 if [ -d $1 ]; then
  if read -q "REPLY?Do you really want to delete /${DIR}? (y/n): "; then
   rm -rf $1
   echo "\nDone."
  else
   echo "\nCanceled."
  fi
 else
  echo "Error. Folder ${DIR} not exists."
 fi
}
```

**Create a folder and go in there `mcd <folder_name>`**

```shell
#!/bin/bash
# Author: André Nespolon
# mcd <folder_name>
mcd() {
 DIR=$1
 if [ ! -d $1 ]; then
  mkdir -p "$1"
  cd "$1"
  echo "Done."
 else
  echo "Error. Folder ${DIR} already exists."
 fi
}
```

**Create Prettier files `prettier [flag] <path>`**

```shell
#!/bin/bash
# Author: André Nespolon
# prettier [flag] <path>

# sintaxe colors
FGRED='\033[0;31m'
FGGREEN='\033[0;32m'
FGYELLOW='\033[0;33m'
NORMAL='\033[0m'

# main process create in current path
processCP() {
  echo '{ \n  "printWidth": 80,\n  "useTabs": true,\n  "semi": true,\n  "singleQuote": true,\n  "jsxSingleQuote": true,\n  "trailingComma": "es5",\n  "bracketSpacing": true,\n  "jsxBracketSameLine": true,\n  "arrowParens": "always",\n  "proseWrap": "always",\n  "endOfLine": "lf",\n  "parser": "babel"\n}' > .prettierrc.json
  success
}

# main process create with path
processSP() {
  if [ -d $1 ]; then
    echo '{ \n  "printWidth": 80,\n  "useTabs": true,\n  "semi": true,\n  "singleQuote": true,\n  "jsxSingleQuote": true,\n  "trailingComma": "es5",\n  "bracketSpacing": true,\n  "jsxBracketSameLine": true,\n  "arrowParens": "always",\n  "proseWrap": "always",\n  "endOfLine": "lf",\n  "parser": "babel"\n}' > $1/.prettierrc.json
    success
  else
    error
  fi
}

# error process
error() {
  echo "${FGRED}Error: input a valid folder/path.${NORMAL}"
  helpCmd
}

helpCmd() {
  echo "${FGYELLOW}usage:"
  echo "       prettier [-c]: create a file in current folder";
  echo "       prettier [-p] <path_dir>: create a file in a specific folder"
  echo "       prettier [-h]: print this help;${NORMAL}"
}

success() {
  echo "${FGGREEN}File created!${NORMAL}"
}

# run command
prettier() {
  while getopts ":c :h p:" opt; do
    case $opt in
      c)
        echo "creating file..."
        processCP
        ;;
      p)
        echo "creating file in $OPTARG"
        processSP $OPTARG
        ;;
      h)
        echo "prettier help"
        helpCmd
        ;;
      \?)
        echo "invalid option: -$OPTARG"
        helpCmd
        ;;
    esac
  done
}
```

#### Commands for MacOS

```bash
sudo xcode-select --install
/bin/bash -c "$(curl -fsSL https://aw.githubusercontent.com/Homebrew/install/master/install.sh)"
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
brew install nvm
npm install -g yarn
brew cask install visual-studio-code skype # update vscode settings and extensions
mkdir ~/dev
```

#### Commands for Linux (Ubuntu)

```bash
sudo apt-get update
sudo apt-get install gnome-tweaks
sudo apt install plank # and then set it in ~/.config/autostart
# set firefox or chrome preferences and install extensions (gnome extensions)
sudo apt install git # install git first
# install manually: theme Ant/Dracula
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme" # and then, set ZSH_THEME="spaceship" in your .zshrc
sudo apt-get install fortune cowsay # and also fortune-br
sudo apt install albert
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
nvm install stable
npm install -g yarn
sudo snap install insomnia # or by .deb daownload
sudo snap install code skype --classic
mkdir ~/dev
```

---

<small>(*) available only for macOs</small>

<small>(**) additional tools for ubuntu: Tweak, Plank, No dash in Overview, Unite and User Themes</small>

<small>(◊) unfortunately Tempo was discontinuous on October 29, 2021</small>