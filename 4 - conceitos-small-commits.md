# Conceitos base da cultura de small commits - pequenos commits
</hr>

Small commits é conceito cultural que acabou se tornando boa prática no mundo Git, principalmente quando se trata de organização 
de projetos no que diz respeito a históricos de commits e logs, e porque não na gestão de branches. A prática consiste na realização
de pequenos commits durante a execução de um conjunto de tarefas em um projeto como feats, fix, styles... Ou seja, é a prática de 
especificar de forma mais minuciosa, porém não tão menos suscinta sobre ações que você realiza dentro do contexto de tarefas como as 
citadas. Nesse caso small não significa necessariamente pequeno em termos de linhas de código escritas, mas sim algo relativo concernente 
às etapas de seu workflow.

Obs1: Você não pode tirar vantagem de nenhuma das características que o git tem para oferecer, a menos que realize um commit. Portanto, 
commitar cedo, e commitar frequentemente, mesmo que mais tarde as suas alterações sejam submetidas por <code>squash</code> a um único 
sistema de revisão baseado em um único commit que vise comprimí-lo para um <code>pull request</code>.

Obs2: Git commits habilitará você para nomear "versões" para as suas changes, assim como voltar atrás e seguir o seu próprio processo de 
pensamento, então você pode compartilhar esse processo de pensamento (commits) com os outros. Multiplos commits também te proporcionarão 
ter acesso a recursos importantes como revert, resets, rebases, diff por partes das suas changes.

Para verificar sua árvore de commits utilize o comando: <code>git log --oneline</code>
* Esse comando permitirá que você veja todo o histórico de ações como commits e merges referente a outras branches que por ventura existam
  em seu projeto.
  ```bash
  $ git log --oneline
    ## lista de commits e merges
    [COMMIT_ID] (HEAD -> <branch>) <current commit message>
    [COMMIT_ID] <previous commit message>
    ...
  ```
  
## 
<strong>Problemática</strong>:</br> O Conceito de small commits tem como primícia tornar o histórico de changes de seu projeto mais organizado
de forma a fazer sua árvore de commits uma "timeline" que conte todo o processo de desenvolvimento do projeto, por tanto tal prática evita
conflitos de código nas branches de um projeto com o escopo bem maior.</br>
Então, digamos que seu time está dividido em um projeto com diversas features e você recebeu uma demanda dentro desse contexto. Em um determinado
momento você precisa realizar uma ação em um trecho de código de responsabilidade de um outro desenvolvedor, mas que tal ação irá contribuir para 
o segmento de seu fluxo de trabalho. Então ao finalizarem suas atividades você, seu colega e os demais do time realizam seus commits de forma global,
sem especificar todas as suas changes.</br>
Temos ai o prenúncio de que algo pode dar errado, principalmente durante o processo de <code>merge</code>, visto que ao obtermos um conflito no código
por conta das alterações realizadas em um mesmo arquivo, temos o agravante do commit global que puxa todas as alterações a partir de um git add all.

##
<strong>Boas práticas de small commits:</strong></br>
Nesse contexto simulamos a criação de dois componentes em um frontend "Header e Navbar"</br>
Prática utilizada para commits globais:
```bash
$ git status
  modified file1.js
  modified file2.js
  modieied file3.js
  
$ git add .
$ git commit -m 'criando header do usuário'
$ git push || git push --set-upstream origin <branch>
```

Práticas para a aplicação de small commits:
```bash
$ git status
  modified file1.js
  modified file2.js
  modieied file3.js
  
$ git add file1.js
$ git commit -m 'criando header do usuário'

$ git add file2.js
$ git commit -m 'criando menu de navegação'

$ git add file3.js
$ git commit -m 'criando rotas de navegação'

$ git push || git push --set-upstream origin <branch>
```

Aplicando small commits para vários arquivos:</br>
Nesse contexto temos o caso onde é necessário realizar alguma intervenção em um arquivo que foi alterado por um outro desenvolvedor
```bash
$ git status
  modified file1.js
  
$ git add file1.js
$ git commit -m 'implementando menu de navegação ao header'

$ git push || git push --set-upstream origin <branch>
```

Note que em comparação com a abordagem global criamos o contexto de histórico o que certamente facilitará nossa vida em casos de conflitos 
de commits e merges. Ao listarmos o log e verificarmos nossa árvore de commits e percebemos que as alterações ganham um sequencia que passa
a fazer sentido em seu processo de desenvolvimento, vejamos:
```bash
## aqui temos uma simulação de acordo com as práticas de small commit vistas nos exemplos acima
## os COMMIT_IDS são fictícios
$ git log --oneline
  
  f28e07df3a (HEAD -> <implement-header>) implementando menu de navegação ao header
  a90f319a86 criando rotas de navegação
  bfdb0540dc criando menu de navegação
  a22fff35f5 criando header do usuário
```
##
<strong>Aplicando git rebase no contexto de small commits:</strong></br>
Rebase basicamente é o processo de mover ou combinar uma sequencia de commits para um novo commit base. O rebase é mais útil e facilmente 
visualizado no contexto chamado de feature branching workflow. Dentro desse contexto os small commits oferecem uma ajuda muito relevante
no que podemos chamar de debug no git, isso é possível quando utilizamos o conceito de commitar alterações em um contexto mais especifico.
```bash
## nesse caso precisamos eliminar um commit específico:
$ git rebase -i <COMMIT_ID>

  pick f28e07df3a (HEAD -> <implement-header>) implementando menu de navegação ao header
  pick a90f319a86 criando rotas de navegação
  pick bfdb0540dc criando menu de navegação
  drop a22fff35f5 criando header do usuário
  
## Ao utilizamos o rebase com a flag -i utilizamos o processador de forma interativa possibilitando escolher... 
## ... as opções "pick" para passar o commit...
## ... ou a opção "drop" para remover o commit
```
Opções disponíveis para o utilização do <code>git rebase -i</code>
* pick = usar commit
* reword = usar commit, porém editar a mensagem de commit
* edit = usar commit, porém parar as alterações
* squash = comprimi os commits
* fixup = como o squash, porém descarta o log de commits
* exec = executar comando
* drop = remover o commit

##
<strong>Boas práticas de commits no contexto de testes e pipelines:</strong></br>
Uma prática muito comum quando estamos em um cenário de execusão de testes ou na preparação e transição de ambientes de nossos projetos
é realizar por diversas vezes vários commits que por vezes não representam nada específico ou acabam sujando a nossa árvore de commits.
Isso ocorre principalmente no contexto de execução de pipelines no CI/CD, Deploy automatizado com uso do Jenkins ou TDD's, pois por várias
vezes é preciso executar e alterar os arquivos de execusão, sendo necessário commitá-los inumeras vezes. Para isso, podemos adotar algumas
práticas limpas para escrita de commits que vão nos ajudar a manter nosso histórico mais organizado.

* <code>git commit --allow-empty</code>: Permite que você faça um commit "vazio", sem necessariamente adicionar arquivos a ele evitando a 
  declaração de mensagens como "commit de teste" 
* <code>git commit --amend --no-edit</code>: Utiliza a mensagem do commit selecionado sem lançar um editor. Ou seja, emenda um commit sem 
  alterar a sua mensagem inibindo também que ela fique visível em seu hitórico.
