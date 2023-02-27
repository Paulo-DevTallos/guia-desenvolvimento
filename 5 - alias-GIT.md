# Alias no Git
</hr>
<strong>O que são alias (aliases) do Git?</strong></br>
São ferramentas de fluxos de trabalho muito eficazes que criam atalhos para comandos Git que utilizamos com
frequência. A utilização desses recurso de forma "consciênte" te fará sem sombra de dúvidas um desenvolvedor
mais ágil e eficiente.
</br></br>
Eles podem ser utilizados para reproduzir uma sequência de comandos dentro de cunho "algoritimico" e lógico 
de acordo com o passo ao qual você realiza suas ações dentro da ferramenta. Para utilizar os aliases é necessário
acessar os recursos de configurações globais do seu usuário git conforme veremos a seguir. Porém é importante
lembrar de que apesar de estarmos falando de um conceito simples de se aplicar e utilizar, é sumáriamente
importante que você tenha um bom conhecimento sobre a utilização dos comandos reais do Git, além de muitíssima 
concentração, pois quando estamos trabalhando em equipe qualquer erro na utilização dos comandos pode comprometer
todo o trabalho, seu e até de outros devs. Portanto leve em consideração utilizar os aliases para comandos corriqueiros
de uso constante além de fazê-lo de forma responsável.

</br></br>
<strong>Acessando recurso de configuração:</strong></br>
Para acessar as configurações de usuário do git é necessário abrir .gitconfig ou utilizar o comando:
```bash
$ git config --global --edit
```
Esse comando te direcionará para uma janela aberta em um terminal (vim, bash, algum terminal Linux) com recursos de edição, 
porém é possível configurar seu uso para um editor de texto como o VS Code. Para isso utilize o comando:
```bash
$ git config --global core.editor [EDITOR_NAME]
## no caso do comando específico para abrir o VS Code utilizamos "code"

## em seguida chamar novamente o comando:
$ git config --global --edit

## abrirá a janela do VS Code com a área de edição de configurações Git
```
<strong>Adicionando aliases:</strong></br>
Para tal simularemos dentro do Bash a tela de configurações com alguns exemplos de aliases já adicionados.
É possível renomeá-los a sua maneira de forma que fique fácil sua identificação e memorização.
```bash

[user]
	email = meuemail@gmail.com
	name = Meu Usuário
[core]
	editor = code
[alias]
	# query commands
	s = !git status
	ss = !git status -s
	l = !git log
	lo = !git log --oneline
	b = !git branch
	d = !git diff

	#new branch statement
	cnb = !git checkout -b

	# add file
	a = !git add 
	# indivual commit
	c = !git commit -m
	# add all utilizando lógica que permite adicionar arquivos e commitá-los ao mesmo tempo
	ac = !git add --all && git commit -m 
```
