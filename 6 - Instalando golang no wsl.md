# Instalando golang no ambiente WSL 2
</hr>

Uma das melhores features do Windows a partir da versao 10 é seu suporte para WSL ou WSL 2, usando essa funcionalidade você pode executar
um ambiente Linux como se fosse uma aplicação do próprio Windows.</br>
E esse recurso é extremamente importante pois se falando de desenvolvimento, muitos recursos dependem de um ambiente Linux para serem executados
ou rodarem de forma mais performatica, é o caso de ferramentas como o Docker, Kubernetes, Redis... e para esse caso podemos falar também de linguagens
de programação como a Golang.</br>
Se você quer instalar a linguagem de programação Go (Golang) no WSL/WSL 2 e configurar seu ambiente de desenvolvimento temos uns passos a serem seguidos:
</br></br>
<strong>1 - Verifique a versão do Go que você deseja executar:</strong></br>
Você pode fazer essa verificação através do site da própria linguagem, lá existem diversas versões para distribuições Linux (nativa), macOS e Windows.</br>
Escolha a versão da linguagem de sua preferência e execute os seguintes comandos:
<a href="https://go.dev/dl/">Ir para a documentação Go</a></br>
</br></br>
<strong>2 - Realize a instalação da linguagem go:</strong></br>
Utilize o comando wget para baixar o .exe compactado.
```bash
## Para esse exemplo utilizaremos uma distribuição nativa do próprio Linux visto que o WSL simula esse ambiente
## até a criação desse tutorial a versão mais atual da linguagem Go é a 1.20.3

# baixa o arquivo executável compactado
$ wget https://go.dev/dl/go1.20.3.linux-amd64.tar.gz

# extrai os arquivos dentro do diretório atual
$ sudo tar -xvf go1.20.3.linux-amd64.tar.gz

$ ls
  go go1.20.3.linux-amd64.tar.gz

# é recomendado mover o arquivo extraído para o path /usr/local/
$ sudo mv go /usr/local
```
</br></br>
<strong>3 - Edite as configurações no .bashrc:</strong></br>
Nesse caso específico nosso tutorial engloba alterações para o bash, porém caso você esteja utilizando o zsh o procedimento é o mesmo.
```bash
## Entre nas configurações do bash e adicione as variáveis de ambientes do Go
$ nano (ou) vi .bashrc

# insira as variáveis de embientes do Go
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
# salve e saia da tela de edição do arquivo de configurações

# execute um reload no terminal 
$ source ~/.bashrc

# execute o comando go para verificar a versão que confirma a instalação
$ go version
  go version go1.20.3 linux/amd64
```
</br></br>
<strong>Observações importantes</strong></br>
Uma vez instalado a Golang necessita da execução da extensão oficial GO no VS Code para processar alguns recursos e ferramentas que a linguagem
depende para funcionar completamente. Para isso após instalar a extensão utilize o comando CTRL + SHIFT + P e procure pela opção >Go: Install/Update Tools
selecione todas as ferramentas necessárias para o funcionamento da linguagem.
<code>
  // hello world em Go
  package main
  
  <code>import "fmt"</code>
  
  func main() {
    fmt.Printf("Hello world")
</code>
```bash
# execute o comando para a saída
$ go run <filename.go>
  hello world
```
