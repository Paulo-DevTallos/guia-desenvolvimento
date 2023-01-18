# Criando subtree para centralizar repositórios
</hr>

Problemática: Quando criamos projetos que dependem de outros recursos para seu pleno funcionamento caimos na seguinte questão: 
Como criar um recurso onde eu tenha disponível todas as etapas que constituirão minha aplicação? Por exemplo, um projeto que é 
composto por um frontend e uma API, por vezes criamos um repositório para cada projeto separadamente. E de fato, uma das poucas
deficiências do sistema Git é essa. Não há muitos recursos que possamos utilizar para já criar projetos do zero com essa ideia de
"children", porém temos alguns recursos que nos ajudam a trabalhar de uma forma melhor a cerca da nossa gestão de projetos dentro
do gitHub.

```bash
## Exemplo da estrutura
Repositorio
   |--- Reposotorio_1.0
   |    |--- index.html
   |    |--- README.md
   |    
   |--- Reposotorio_2.0
   |    |--- index.html
   |    |--- README.md
   |  
   |--- README.md
```

-- submodules: Muitas vezes acontece que, ao trabalhar em um projeto, você precisa usar outro projeto dentro dele. Talvez seja uma 
biblioteca ou algo que você esteja desenvolvendo separadamente e usando em vários projetos principais. Um problema comum surge nesses 
cenários: ainda que você trate os dois projetos como separados eles sempre dependerão um do outro.

-- subtree: Cria um repositório que contenha outros repositórios clonando suas URLs mantendo o mesmo histórico de commits

Para esse caso usaremos o conceito de subtree: porém é preciso levar em consideração que os dois projetos já estejam em seus devidos 
repositórios, com suas branch em mesmo níveis e atualizadas. Então é necessário notar se há essa discrepância.

```bash

## Primeiro crie um repositório vazio, vinculando remoto e local. Geralmente fazemos isso usando um README comum.
## Após a criação desse repositório é necessário seguir alguns passos.

## dentro do repositório vazio:
$ git subtree add -P <nome-do-repositorio> [url] HEAD
## url de clone do repo: https://github.com/usergit/Repositorio-1_0.git (HEAD aponta para todos o histórico de commits do projeto)

## após a realização do clone do projeto para dentro do repositório pai é necessário fazer um push para subir toda aplicação
$ git push origin <repositorio-pai>

```

Observação: Os projetos funcionam de forma individual recebendo commits e pushs de formas distintas, no entanto é preciso ter cuidado quanto
a sua gestão de branches já que a branch principal pertence ao repositório principal.

...
