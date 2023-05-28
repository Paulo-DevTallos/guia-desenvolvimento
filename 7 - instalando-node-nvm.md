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
Utilizaremos o comando curl para instalar o NVM, caso não possua o comando basta instalá-lo.</br>
```sh 
$ sudo apt install curl
```
