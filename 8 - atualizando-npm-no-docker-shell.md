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
Um dos conceitos fundamentais no Docker é sobre a criação e execução de imagens que são processo criados a partir de camadas, ou seja imagine que temos uma imagem inicial chamada "Scratch", um HD formatado, depois disso precisaremos de partes de um Sistema operacional como o Ubuntu, ovbiamente as partes do ubuntu que precisaremos são apenas as partes que o SO não tem, pois as que ele tem não serão necessárias para baixar.</br>
Agora imaginemos isso no contexto do NodeJS, pois em seu registry (como o DockerHub) no Docker, existem versões que contém partes necessárias para a execução do NodeJS puramente em nossa máquina sem que tenhamos a necessidade de ter o Node instalado localmente, tudo ocorre por meio do Docker.</br></br>
Compreendido esse tópico, vamos criar uma imagem utilizando uma imagem Node para criar a nossa própria.

```bash 
FROM node:18-alpine

WORKDIR /usr/my-app/app

USER node

COPY package*.json .

EXPOSE 3000

CMD [ "tail", "-f", "/dev/null" ]
```
