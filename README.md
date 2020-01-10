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

### 5 - Configurando tema no vscode
* Plugins a serem instalados
  * Dracula Official
  * Material Icon Theme
  * Color Highlight
  * Bracket Pair Colorizer
  * Rocketseat ReactJS e React Native
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
  

### 2 - Delete eslint
Apagar arquivo do eslint se houver e instalar o eslint como depedência de desenvolvimento:
```
yarn add eslint -D
yarn eslint --init
```
### Obs: Após rodar o comando eslint --init, algumas opções deverão ser selecionadas:
> How would you like to use ESLint? (Como você gostaria de utilizar o ESLint?)

 To check syntax, find problems, and enforce code style

> What type of modules does your project user? (Quais tipos de módulos o seu projeto usa?)

Javascript modules (import/export)

> Which framework does your project use? (Qual framework o seu projeto usa?)
 
React, Vue ou None of theses

> Does your project use TypeScript? (y/N) (O seu projeto usa TypeScript?)
 
N

> Where does your code run? (Onde irá rodar seu projeto?)

Browser ou Node (use a barra de espaço para desmarcar uma opção. No caso do react native, desmarque todas.)

> Use a popular style guide (Utilize uma guia de estilo popular)

Use a popular style guide

> Which style guide do you want to follow? (Qual guia de estilo deseja seguir?)

Airbnb 

> What format do you want your config file to be in? (Em que formato você deseja que o seu arquivo de configuração esteja?)

JavaScript

> Would you like to install them now with npm? (Y/n) (Gostaria de instalar as dependências com npm?)

Y



### 3 - Delete package-lock
Apagar aquivo ***package-lock.json*** para associar as dependências ao arquivo ***yarn.lock*** e reinstalar utilizando o comando abaixo:
```
yarn 
```

### 4 - Install Prettier
Instalar dependências do prettier e babel-eslint conforme abaixo:
```
yarn add prettier eslint-config-prettier eslint-plugin-prettier babel-eslint -D 
```

### 5 - Add to eslintrc
No arquivo ***.eslintrc.js*** copiar as configurações:
```
module.exports = {
  env: {
    es6: true,
  },
  extends: ['plugin:react/recommended', 'airbnb', 'prettier/react'],
  globals: {
    Atomics: 'readonly',
    SharedArrayBuffer: 'readonly',
  },
  parser: 'babel-eslint',
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 2018,
    sourceType: 'module',
  },
  plugins: ['react', 'prettier'],
  rules: {
    'linebreak-style': ['error', 'windows'],
    'linebreak-style': 0,
    'prettier/prettier': 'error',
    'react/jsx-filename-extension': [
      'warn',
      {
        extensions: ['.jsx', '.js'],
      },
    ],
    'import/prefer-default-export': 'off',
  },
};
```

### 6 - Add to prettierrc
Criar arquivo ***.prettierrc*** com configurações de single quote:
```
{
  "singleQuote": true,
  "trailingComma": "es5"
}
```

### 7 - Add to settings
Para que as configurações sejam aplicadas ao salvar o arquivo, no arquivo principal de configurações do VSCODE ***settings.json*** (ctrl + shift + P) adicione a seguinte linha:
```
"editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    }
``` 


Ambiente configurado! Só começar a codar. :coffee: :raised_hands: 
