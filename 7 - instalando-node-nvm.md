# Instalando node utilizando o nvm
</hr>

Com suporte para MAC e Linux, incluinso o subsistema WSL no Windows o NVM (Node version manager) é uma ferramenta utilizada para instalar e gerir várias versões do Node, ou seja, ele permite que você instale e gerencie o Node em sua máquina de forma simples, bem como também proporcionar troca de versões dentro da ferramenta. 
</br></br>
Por exemplo, se você possui o Node v18.16.0 instalado em seu sistema e precisa realizar a manutenção de um projeto antigo que utilize a versão v16.14.0 para o NVM isso não será um problema. Então vamos entender como utilizá-lo e gerir esses recursos.
</br></br>
<h2>Instalando o NVM</h2>
Para esse tutorial verificaremos a instalação para quem utiliza as dependências de Debian e Ubuntu, mas se preferir você pode consultar o repositório oficial do NVM e verificar o passo a passo completo. </br>
ver tutorial completo: <a href="https://github.com/nvm-sh/nvm">Repositório NVM</a>
</br></br>
Utilizaremos o comando curl para instalar o NVM, caso não possua o comando basta instalá-lo.

```bash 
$ sudo apt install curl
```
Após instalar o curl execute o seguinte comando que captura e executa a url que contém o script de instalação do NVM

```bash
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Com isso temos o NVM instalado, esse comando cria automáticamente um script de inicialização do NVM em no path de nosso terminal (na nossa máquina). Para verificar basta digitar <code>nvm --help</code>. Se por acaso não for retornada as mensagens de help do NVM configure manualmente o script no sistema. Para adicioná-lo no path do nosso sistema, precisamos editar um desses três arquivos ( ~/.zshrc, ~/.profile, or ~/.bashrc), vai depender do seu terminal de utilização, adicione ao final do arquivo o seguinte trecho de código:

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```
Após essa configuração é só digitar o comando de help ou verificar a versão, então teremos o NVM funcionando.
</br></br>

<h2>Instalando o Node via NVM</h2>
Então bora ver como instalar o Node utilizando o NVM? Primeiro de tudo é importante notar que o NVM já é uma ferramenta do próprio Node, (pois é um gerenciador de versões) já pré-dispomos de algumas versões do Node disponíveis, para listar essas versões basta inserir no terminal o comando <code>nvm ls-remote</code>.</br>
Esse comando lista todas as versões disponíveis no ambiente do NVM, inclusive listando a versão LTS mais recomendada, versões Alpines e Gallium por exemplo...</br>

```bash
## exemplo do output do terminal
       ...
       v16.15.1   (LTS: Gallium)
       v16.16.0   (LTS: Gallium)
       v16.17.0   (LTS: Gallium)
       v16.17.1   (LTS: Gallium)
       v16.18.0   (LTS: Gallium)
       v16.18.1   (LTS: Gallium)
       v16.19.0   (LTS: Gallium)
       v16.19.1   (LTS: Gallium)
       v16.20.0   (Latest LTS: Gallium) 
       ...
       v18.9.0
       v18.9.1
       v18.10.0
       v18.11.0
       v18.12.0   (LTS: Hydrogen)
       v18.12.1   (LTS: Hydrogen)
       v18.13.0   (LTS: Hydrogen)
       v18.14.0   (LTS: Hydrogen)
       v18.14.1   (LTS: Hydrogen)
       v18.14.2   (LTS: Hydrogen)
       v18.15.0   (LTS: Hydrogen)
       v18.16.0   (Latest LTS: Hydrogen)
        v19.0.0
        v19.0.1
        v19.1.0
        v19.2.0
        v19.3.0
        ...
```
Para instalar uma versão basta escolher uma versão, recomendo que seja alguma LTS (latest) e executar o comando <code>nvm install v18.16.0</code>, por exemplo.</br>
Uma vez escolhida a versão e executado o comando o NVM instala também a versão do NPM equivalente e versão do Node escolhida.

```bash
$ node -v
v18.16.0

$ npm -v
9.5.1
```
E pronto! caso você necessite trocar de versão basta utilizar o comando nvm ls-remote e todas as versões serão listadas, basta escolher a de sua preferência.</br></br>
Obs: Caso você possua algumas versões instaladas e precise alterar entre elas vai uma dica bem legal! Utilize o comando <code>nvm ls</code> e veja as versões que já estão instaladas em seu sistema.

```bash
nvm ls 

default -> v18.16.0
iojs -> N/A (default)
unstable -> N/A (default)
node -> stable (-> v18.16.0) (default)
stable -> 18.16 (-> v18.16.0) (default)
lts/* -> lts/hydrogen (-> v18.16.0)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.24.1 (-> N/A)
lts/erbium -> v12.22.12 (-> N/A)
lts/fermium -> v14.21.3 (-> N/A)
lts/gallium -> v16.20.0 (-> N/A)
lts/hydrogen -> v18.16.0
```
Utilize o comando <code>nvm use v16.20.0</code> para trocar da versão 18 para a 16, por exemplo. Basicamente o comando ls identifica as versões instaladas e o comando use <versão> faz o apontamento para a versão que você deseja utilizar.</br>
* Para manter uma versão como padrão utilize <code>nvm alias default v16.20.0</code>
* Para instalar uma nova versão do Node utilizando NVM <code>nvm install <version></code>
