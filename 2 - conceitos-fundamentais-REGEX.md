# Regex: Expressões regulares

forma tradicional: new RegExp("o") - encontra qualquer ocorrência dessa letra dentro de uma string, comum utilização para concatenar strings com variáveis
sintax sugar: /o/

Principais caracteres utilizados no RegEx:
* //ig - regex vazia considerando todo um texto aplicado.
* \d - digito
* \d. - interpreta qualquer caracter entre digitos
* \d\. - busca um ponto "." literal
* 'g' - global - localiza todas as ocorrências de forma global. Ex: /o/g
* 'i' - utilizando a flag "i" passamos a considerar todas as ocorrências de um determinado caracter: 
* '.' - representa um meta-char, se não for isolado por uma barra representa todos os caracteres dentro de uma cadeia de strings
* 
Ex: Paulo, /p/ig ou /P/gi => a posição da flag i não interfere no resultado da busca. 
Nesse caso temos todas as ocorrências com letras maiusculas ou minusculas na palavra 

Realizando busca dentro da regex com opções de strings
Ex: React, ReactJS 
/react(js)?/ig ou /react(js){0,1}/
/(react|reactjs)/ig - forma mais verbosa, pois repete as palavras da busca
* () - cria um aninhamento "concatenando" valores de caracteres, variáveis
* ? - Significa que o último caracter ou bloco de agrupamento podem existir nenhuma ou uma vez 
* {0,1} - Significa que podem haver nenhuma ou uma ocorrência de determinado valor
* {0,} - Significa que podem haver nenhuma ou infinitas ocorrências de determinado valor, nesse contexto a virgula representa quantas vezes forem necessários.
* "+" - Caracter de uma ou mais ocorrências
* "*" - Caracter de nenhuma ou muita ocorrências, varrendo todos os resultados
* [-.$] ou [0-9a-g] - definindo uma cadeia de caracteres
* Ex: formatação de um CPF: \d{3}.\d{3}.\d{3}\[-.]?\d{2} ****
* '^' - caracter circunflexo representa o inicio de uma string de caracteres 
* '$' - representa o final da string de caracteres
Ex: Paulo, /^paulo$/ig - faz um match checkando toda a palavra buscada.
Ex: Paulo, /^pa/ig - quero que comece com esses caracteres
Ex: Paulo, /ulo$/ig - quero que termine com esses caracteres

Tratando espaçamentos em uma regex:
* \s - significa whitespace
[1-3]?\d\s - define um espaço em uma cadeia com digitos de 1 a 3 e que contém um espaço em branco
* para definir um espaçamento maior: é preciso um quantifier para o caracter: \s{1,} ou \s+

* \ - contra barra é utilizado quando queremos especificar um caracter espacial válido em nossa busca.
Ex: Paulo$, /ulo$\$/ig

O asterisco \* (somente o asterisco sem a barra) que serve para definir uma quantidade de chars, zero ou mais vezes
{} - as chaves que servem para definir uma quantidade de caracteres específicas que é desejado encontrar

representação de busca de um cpf (cadeia de números)
* \d\d\d\.\d\d\d\.\d\d\d-\d\d

quantifier - é utilizado para definir quantas vezes um determinado caracter deve aparecer
* \d{3} - retorna o digito 3x
* \d{3}\.\d{3}\.\d{3}\-\d{2} - cpf utilizando quantifier

Ancoras:
É o mesmo que procurar uma palavra especifica dentro de um texto e saber sua posição, Não pode está atrelado a um word char: 
Obs: word char é "[A-Za-z0-9_]" ou mais curto \w
* \b - word boundary 
Ex 1: de aplicação: procurando as preposições "de" na frase "Eu fico cada vez mais feliz de estudar e de aprender" => \bde\b
Essa notação vai delimitar as duas ocorrências de "de" dentro da frase.
Ex 2: "aaa aaaaaa aaa aaaaaa aaa aaaa" => utilizando o \baaa\b ele encontrará apenas as ocorrências de "3as" dentro da frase. 

Exemplo contrário de word boundary, existe o non-word boundary \B (Maiuscula). 
Aplicada a franse "portugues proporciona compor" => \Bpor\B
A nossa regex seleciona a sílaba "por", e antes e depois dela, deve ter um Non word boundary. Em outras palavras, 
a silaba por deve aparecer dentro de uma palavra, nunca no inicio ou fim.

Âncoras de inicio e de final:
Ex: url file:///USer/minhaurl/Desktop/regex/index.html
* ^file.+\.html$ => encontra toda a URL pois ela inicia e termina com os caracteres estabelecidos


##

Exercicios:

```sh
## O número do IP de um computador é gerado ao conectá-lo à internet, 
## esse número permite que o dispositivo seja identificado e capaz de enviar/receber informações. 
## Abaixo há alguns exemplos de IP:

## 126.1.112.34
## 128.126.12.244
## 192.168.0.34

\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
## Um IP tem quatro grupos de no mínimo um e máximo três números. Repare que estamos escapando o ponto (.) entre os números, 
que são blocos de dígitos \d entre 1 e 3 caracteres {1,3}

# caracteres para numeros de telefone
\(\d{2}\) \d{4}-\d{4}
```
```sh
# Qual é a classe correta para definir os números entre 1 e 3 E 6 e 9?
[1-36-9]

## definindo formato de data no padrão 28 de Dezembro de 2023
[1-3]?\d\s+de\s+[A-Z][a-zç]{3,8}\s+de\s+[12]\d{3}

Explicação:
[1-3]?\d - quantidade de caracteres entre 1 e 3 digitos (dia)
\s+ - espaço em branco que pode ser 1 ou mais
[A-Z][a-zç]{3,8} - definição da regex que configura os mêses do ano 
ex: [Primeira letra do mês maiuscula entre A-Z][demais letras minusculas entre a-z, considerando ç como caracter especial]{quantidade de letras dos meses}
[primeiro número que o ano deverá pouuir]\d{3}

## definindo formato de hora 19h32min16s
\d{2}h\d{2}min\d{2}\s
outro modo: [0-9]{2}h[0-9]{2}mim[0-9]{2}s

## definindo as regras de regex para uma placa de carro
[A-Z]{3}-\d{4}

## definindo regex que captura "Data: 02/09/1964 ou Data:02/09/1964".
^Data:[\s]?[0-9]{2}\/[0-9]{2}\/[0-9]{4}$

```

Revisão sobre os grupos de regex:
Ancoras:
\b - world boundary
^  - início do alvo
$ - fim do alvo

Quantificadores:
{n,m} - "n" o minimo de vezes / "m" - o máximo de vezes
? - zero ou uma vez
"+" - uma ou mais vezes
("*") - zero ou mais vezes

Classes de char - []
[A-Z] - letras de A até Z
[123] - 1,2 ou 3
\d - todos os digitos
\s - whitespace
\w - wordchar [A-Za-z0-9_]
