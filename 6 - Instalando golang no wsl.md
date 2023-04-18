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
