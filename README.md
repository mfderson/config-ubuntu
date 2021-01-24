# Configuração do ambiente de dev no Ubuntu :boom:

### 1 - Diretórios
```bash
mkdir ~/dev && cd ~/dev && mkdir cursos && cd cursos && mkdir rocketseat && mkdir algaworks
```
### 2 - Instalação de pacotes
```bash
sudo apt install git -y
sudo apt install fonts-firacode
sudo apt-get install gnome-tweak-tool
```
### 3 - Softwares a serem instalados
* vscode (sudo dpkg -i <file.deb>)
* Postman
* Insomnia
* Devdocs app
* Discord
* Postbird
* Intellij
* Reactotron (baixar o arquivo .deb)

### 5 - Configurando IDEs
#### 5.1 - vscode - [fonte](https://www.notion.so/Visual-Studio-Code-e0d3c48eebdd4df586c4ba8c12cf5a7a)
* Plugins a serem instalados
  * Omni
  * Material Icon Theme
  * Color Highlight
  * Bracket Pair Colorizer
  * Rocketseat ReactJS e React Native
  * DotEnv
  * Markdown All in One
  * vscode-styled-components
  * Arruma a ordem dos imports: [plugin](https://www.npmjs.com/package/eslint-plugin-import-helpers)

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
[fonte](https://blog.rocketseat.com.br/terminal-com-oh-my-zsh-spaceship-dracula-e-mais/)

```bash
mkdir ~/.zplugin
git clone https://github.com/zdharma/zplugin.git ~/.zplugin/bin
```
* Abra o arquivos .zshrc e cole no final
```
SPACESHIP_PROMPT_ORDER=(
  user          # Username section
  dir           # Current directory section
  host          # Hostname section
  git           # Git section (git_branch + git_status)
  hg            # Mercurial section (hg_branch  + hg_status)
  exec_time     # Execution time
  line_sep      # Line break
  vi_mode       # Vi-mode indicator
  jobs          # Background jobs indicator
  exit_code     # Exit code section
  char          # Prompt character
)
SPACESHIP_USER_SHOW=always
SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_CHAR_SYMBOL="❯"
SPACESHIP_CHAR_SUFFIX=" "
```
### 7 - Instalando node, npm e yarn
* Instalar primeiro nvm (gerenciador de pacotes do node) [fonte](https://github.com/nvm-sh/nvm)
  * Add in .zshrc and .bashrc
* Procurar qual versão estável do node no site e...
```bash
nvm install <numero_da_versao>
```
* Setar versão padrão do node
```bash
nvm alias default <numero_da_versao>
nvm use <numero_da_versao>
```
* Testar
```bash
npm -v
node -v
```
* Instalar o yarn
	- Configurarar o repositórios do yarn
```bash
npm install -g yarn
```
	- Testar
```bash
yarn -v
```

### 8 - Docker
[Fonte](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
* Manage Docker as a non-root user
  * Create the docker group
  ```bash
  sudo groupadd docker
  ```
  * Add your user to the docker group
  ```bash
  sudo usermod -aG docker $USER
  ```
  * Logout e Login
  ```bash
  newgrp docker
  ```
  * Testar
  ```bash
  docker run hello-world
  docker ps
  ```
  
### 9 - React Native - [fonte](https://react-native.rocketseat.dev/)
* Instalar react-native-cli
```bash
npm install -g react-native-cli
```
* Instalar JDK versão 8
```bash
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```
* Como alterar versão do java/javac atual para usar
```bash
sudo update-alternatives --config java
sudo update-alternatives --config javac
```
* Instalar graphic libs
```bash
sudo apt-get install gcc-multilib lib32z1 lib32stdc++6
```
* Instalar Android Studio
  * [Download](https://developer.android.com/studio/)
  
  * Extraia o android-studio na sua home
  
  * Execute o comando
  ```bash
  export PATH=$PATH:~/android-studio/bin
  ```
  
  * Para executar o android-studio digite
  ```bash
  studio.sh
  ```
  
  * Crie os diretório
  ```bash
  cd ~
	mkdir Android
	cd Android
	mkdir Sdk
  ```
  
  * Adicione as variáveis de ambiente no seu .zshrc ou .bashrc
  ```bash
  export JAVA_HOME=CAMINHO_ANOTADO_COM_SUA_VERSÃO
  export ANDROID_HOME=~/Android/Sdk
  export PATH=$PATH:$ANDROID_HOME/emulator
  export PATH=$PATH:$ANDROID_HOME/tools
  export PATH=$PATH:$ANDROID_HOME/tools/bin
  export PATH=$PATH:$ANDROID_HOME/platform-tools
  ```
  * Extraia o arquivo baixado para ~/Android/Sdk
  
  * Adicione as linhas abaixo no ~/.bashrc e ~/.zshrc
  ```bash
  source .bashrc
  source .zshrc
  ```

* Configurar o Android Studio
  
  A primeira janela a ser apresentada deve ser perguntando sobre a importação de configurações de outro Android Studio. Selecione a opção **Do not import settings** e clique em **OK**.

  Após o carregamento terminar, deve aparecer uma página de Welcome. Clique em **Next**.

  Na sequência, será pedido o tipo de instalação. Escolha a opção **Custom** e clique em **Next**.

  Nesse momento, será pedido para escolher a localização do pacote JDK instalado. Clique em ⬇ e escolha a opção **JAVA_HOME**. Verifique se ela está apontando para a JDK 8. Clique em **Next**

  Em seguida, será perguntado sobre qual tema será utilizado. Escolha o que preferir e clique em **Next**

  Chegamos na etapa mais importante do processo, a instalação da SDK. A janela apresentará algumas opções, marque todas.

  - SDK é o pacote que vai possibilitar que sua aplicação React Native faça o build. Por padrão, ele instala a última 
  
  - SDK estável (nesse caso a 29);
  
  O Android Virtual Device vai criar um emulador padrão pronto para execução.

  Um fator essencial nessa etapa é o caminho de instalação da SDK. Utilize a pasta que você criou na seção Preparativos para o Android Studio (Ex.: ~/Android/Sdk). Não utilize espaços ou caracteres especiais pois causará erros mais para frente.

  Se tudo estiver correto, clique em **Next**.

  Na sequência, temos uma janela avisando sobre a possibilidade de executar o Emulador com melhor performance usando o KVM (Kernel-mode Virtual Machine). Essa etapa não irá aparecer para todos pois nem todo computador é compatível com esse recurso. Caso tenha interesse em instalar essa ferramenta, será ensinado como ao final dessa página. Finalizada essa etapa, clique em **Next**.

  Em seguida, será apresentada uma janela com um resumo de todas as opções escolhidas até aqui. Verifique se está tudo certo, principalmente os caminhos da SDK e do JDK. Clique em **Finish**.

  Por fim, será realizada a instalação das configurações selecionadas. Quando o programa terminar, clique em **Finish**.

* SDK Manager
  
  Atualmente, o React Native utiliza a **SDK 28** como padrão para projetos Android. Ao executar o app no android, a cli detecta se você possui a SDK 28 e se aceitou as licenças necessárias. Caso contrário, ela já instala parcialmente a SDK 28 para você.

  Porém, para não depender apenas da cli, nesse tópico será ensinado como instalar a SDK 28 pelo SDK Manager do Android Studio.

  Abra o Android Studio. No **canto inferior direito da janela**, clique em **Configure** e escolha a opção **SDK Manager**.

* KVM
  
  Caso o seu Android Studio tenha acusado a possibilidade de instalar o **KVM** e você pretende executar sua aplicação React Native no Emulador, pode prosseguir com esse tutorial. Caso contrário, pode pular para o próximo

  Para instalar o **KVM**, o processo é bem simples. Em sistemas Ubuntu/Debian e Linux Minti, instale o **KVM** executando o comando:
  ```bash
  sudo apt install qemu-kvm
  ```

  Em seguida, adicione o seu usuário no grupo do KVM:
  ```bash
  sudo adduser $USER kvm
  ```

  Por fim, reinicie (ou deslogue e log novamente) o sistema e execute o comando:
  ```bash
  grep kvm /etc/group
  ```

  Se o resultado for algo semelhante a:
  ```bash
  kvm:x:NUMERO_QUALQUER:SEU_USUARIO
  ```

  O kvm está instalado corretamente e pronto para uso.

* Emulador

  Siga o [tutorial](https://react-native.rocketseat.dev/android/emulador) para configuração.

* Dispositivo Físico
  
  Siga o [tutorial](https://react-native.rocketseat.dev/usb/android) para configuração.

### 10 - Java
* Instalar jdk 14
  * Faça o [download](https://jdk.java.net/14/)
  ```bash
  cd ~/Downloads && tar xvf openjdk-14*_bin.tar.gz
  sudo mv ~/Downloads/jdk-14** /usr/lib/jvm
  ```

* Adicionar o jdk ao java update alternatives
```bash
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-14.0.1/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-14.0.1/bin/javac 1
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

* Setar o java home no VSCode
  * No arquivo settings.json adicionar?
  ```json
  "java.home": "/usr/lib/jvm/jdk-14.0.1",

  "[java]": {
    "editor.defaultFormatter": "redhat.java",
  },
  ```

### 11 - Maven
```bash
sudo apt-get -y install maven
```

Ambiente configurado! Só começar a codar. :coffee: :raised_hands: 
