# Configuração do ambiente de dev no Ubuntu :boom:

### 1 - Diretórios
```
mkdir ~/dev && cd ~/dev && mkdir cursos && cd cursos && mkdir rocketseat && mkdir algaworks
```
### 2 - Instalação de pacotes
```
sudo apt install git -y
sudo apt install fonts-firacode
sudo apt-get install gnome-tweak-tool
```
### 3 - Instalação do tema flat-remix (opcional)
```
git clone https://github.com/daniruiz/flat-remix
git clone https://github.com/daniruiz/flat-remix-gtk
mkdir -p ~/.icons && mkdir -p ~/.themes
cp -r flat-remix/Flat-Remix* ~/.icons/ && cp -r flat-remix-gtk/Flat-Remix-GTK* ~/.themes/
```
### 4 - Softwares a serem instalados
* vscode (sudo dpkg -i <file.deb>)
* Postman
* Insomnia
* Devdocs app
* Discord
* Postbird
* Intellij

### 5 - Configurando IDEs
#### 5.1 - vscode
* Plugins a serem instalados
  * Dracula Official
  * Material Icon Theme
  * Color Highlight
  * Bracket Pair Colorizer
  * Rocketseat ReactJS e React Native
  * DotEnv
  * Markdown All in One
* Abrir o settings.json e colar o conteúdo abaixo
```
{
  "workbench.colorTheme": "Dracula",
  "editor.fontFamily": "Fira Code",
  "editor.fontLigatures": true,
  "editor.fontSize": 14,
  "workbench.iconTheme": "material-icon-theme",
  "editor.rulers": [80, 120],
  "editor.renderLineHighlight": "gutter",
  "editor.tabSize": 2,
  "terminal.integrated.fontSize": 14,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "emmet.syntaxProfiles": {
    "javascript": "jsx"
  },
  "javascript.updateImportsOnFileMove.enabled": "never",
  "editor.parameterHints.enabled": false,
  "breadcrumbs.enabled": true,
  "javascript.suggest.autoImports": false
}
```
#### 5.2 - Intellij
  * Plugins
    * Dracula Theme
    * Rainbow Brackets
    * Atom Material Icons
    * Lombok
  * Live reload
    * File->Setting –> Build, Execution, Deployment –> Compiler–>Build project automatically is selected
    * Press SHIFT+CTRL+A -> type: Registry... -> and check: compiler.automake.allow.when.app.running

### 6 - Configurando terminal
```
sudo apt install zsh
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```
* Abra o arquivo .zshrc e cole no final
```
set ZSH_THEME="spaceship"
```
```
mkdir ~/.zplugin
git clone https://github.com/zdharma/zplugin.git ~/.zplugin/bin
```
* Abra o arquivos .zshrc e cole no final
```
SPACESHIP_PROMPT_ORDER=(
  user
  dir
  host
  git
  exec_time
  line_sep
  jobs
  exit_code
  char
)

SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_CHAR_SYMBOL=">"
SPACESHIP_CHAR_SUFFIX=" "

source ~/.zplugin/bin/zplugin.zsh
autoload -Uz _zplugin
(( ${+_comps} )) && _comps[zplugin]=_zplugin

zplugin light zsh-users/zsh-autosuggestions
zplugin light zsh-users/zsh-completions
zplugin light zdharma/fast-syntax-highlighting
```
### 7 - Instalando node, npm e yarn
* Instalar primeiro nvm
```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```
  * Add in .zshrc and .bashrc
* Procurar qual versão estável do node no site e...
```
nvm install <numero_da_versao>
```
* Setar versão padrão do node
```
nvm alias default <numero_da_versao>
```
* Testar
```
npm -v
node -v
```
* Instalar o yarn
```
sudo apt update && sudo apt install --no-install-recommends yarn
```

### 8 - Docker
* Procure por: "docker ce" no google
  * https://docs.docker.com/install/linux/docker-ce/ubuntu/
* Desinstale versões anteriores
```
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update && sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```
* Add Docker’s official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
* Install Docker CE
```
sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io
```
  * List Docker CE versions
```
apt-cache madison docker-ce
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```
  * Testar
```
sudo docker run hello-world
sudo docker ps
```
* Manage Docker as a non-root user
  * Create the docker group
  ```
  sudo groupadd docker
  ```
  * Add your user to the docker group
  ```
  sudo usermod -aG docker $USER
  ```
  * Logout e Login
  ```
  newgrp docker
  ```
  * Testar
  ```
  docker run hello-world
  docker ps
  ```
  
### 9 - React Native - [fonte](https://docs.rocketseat.dev/)
* Instalar react-native-cli
```
npm install -g react-native-cli
```
* Instalar JDK versão 8
```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```
* Como alterar versão do java/javac atual para usar
```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```
* Instalar graphic libs
```
sudo apt-get install gcc-multilib lib32z1 lib32stdc++6
```
* Configurar Android SDK
  * [Download](https://developer.android.com/studio/#downloads)
    * Em "Command line tools only" baixe a SDK
  * Crie os diretório
  ```
  cd ~
	mkdir Android
	cd Android
	mkdir Sdk
  ```
  * Extraia o arquivo baixado para ~/Android/Sdk
  * Adicione as linhas abaixo no ~/.bashrc e ~/.zshrc
  ```
  source .bashrc
  source .zshrc
  ```
* Instalar Genymotion (se não for debugar no cel físico)
  * Instalar Virtualbox
  ```
  sudo apt-get install virtualbox
  ```
  * Baixar o genymotion [download](https://www.genymotion.com/fun-zone/)
    ```
    cd ~/Downloads && chmod +x genymotion*.bin 
    ./genymotion-xxx.bin
    ```
  * Crie um emulador no Genymotion
  * Conect o emulador ao ADB (Android Debug Bridge)
    * adb connect IP_DO_SEU_EMULADOR:5555 -> (Para verificar o IP do dispositivo, basta esticar a janela do emulador, o IP estará no título da janela)
    * adb devices -> (se aparecer o nome do seu dispositivo na lista, seu emulador foi conectado com sucesso)

### 10 - Java
* Instalar jdk 11 - [fonte](https://www.digitalocean.com/community/tutorials/como-instalar-o-java-com-apt-no-ubuntu-18-04-pt)
```
sudo apt install default-jre
java -version
sudo apt install default-jdk
javac -version
```
* Instalar jdk 13
  * Faça o [download](jdk.java.net/13)
  ```
  cd ~/Downloads && tar xvf openjdk-13*_bin.tar.gz
  sudo mv ~/Downloads/openjdk-13* /usr/lib/jvm
  ```
* Adicionar o jdk ao java update alternatives
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-13.0.1/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-13.0.1/bin/javac 1
sudo update-alternatives --config java
sudo update-alternatives --config javac
```


Ambiente configurado! Só começar a codar. :coffee: :raised_hands: 
