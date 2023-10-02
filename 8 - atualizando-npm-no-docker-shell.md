# New major version of npm is available!
</hr>

Pois é desenvolvedor, periodicamente os avanços de uma ferramenta ou tecnologia requerem atualizações e com os gerenciadores de pacote não é diferente, inclusive essa é a mensagem que comumente vemos quando novas features ou correções são diponibilizadas, no caso do NPM. 
</br></br>
Ainda tem dúvida sobre o que é o NPM?</br>
NPM (Node Package Manager) é o gerenciador de pacotes padrão para o ecossistema NodeJS. Ele é uma ferramenta que permite que desenvolvedores instalem, gerenciem e compartilhem pacotes de código JavaScript reutilizáveis. Os pacotes podem conter bibliotecas, frameworks, módulos, ou até mesmo programas inteiros escritos em base JavaScript. Além disso você tem benfcícios como, por exemplo:
<ul>
  <li>Instalação de pacotes externos direto em seu projeto</li>
  <li>Gerenciamento de pacote, o qual o NPM utiliza-se de um auto rastreio para verificar as dependências necessárias em que seu projeto precise para trabalhar</li>
  <li>Criação de scripts personalizados no package.json que permitem a execução de comandos do próprio NPM</li>
</ul>
Porém como é a proposta desse artigo vamos explorar algo mais específico utilizando o Docker no contexto de execução de um container utilizando uma imagem Node.
</br>
<h2>Um pouco sobre o Docker</h2>
O Docker é uma plataforma de código aberto que permite criar, implementar e gerenciar a criação de aplicativo em containers. Um contêiner é uma unidade de software leve que inclui tudo o que é necessário para executar um aplicativo, incluindo o código, runtime, bibliotecas, dependências e variáveis de ambiente. Isso faz o Docker uma ferramenta amplamente utilizada para desenvolver e implantar aplicativos de maneira consistente e escalável, independente de ambiente ou hospedagem, ou seja, com a utilização do Docker não temos problemas como o famoso "na minha máquina funciona...".
</br></br>
<h2>Criando uma imagem Node</h2>
Utilizaremos o comando curl para instalar o NVM, caso não possua o comando basta instalá-lo.

```bash 
$ sudo apt install curl
```
