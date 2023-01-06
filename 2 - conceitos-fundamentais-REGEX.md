# Regex: Expressões regulares

forma tradicional: new RegExp("o") - encontra qualquer ocorrência dessa letra dentro de uma string, comum utilização para concatenar strings com variáveis
sintax sugar: /o/

* //ig - regex vazia considerando todo um texto aplicado
* \d - digito
* \d. - "." representa um meta-char, interpreta qualquer caracter entre digitos
* \d\. - busca um ponto "." literal
* 'g' - global - localiza todas as ocorrências de forma global. Ex: /o/g
* 'i' - utilizando a flag "i" passamos a considerar todas as ocorrências de um determinado caracter: 
Ex: Paulo, /p/ig ou /P/gi => a posição da flag i não interfere no resultado da busca. 
Nesse caso temos todas as ocorrências com letras maiusculas ou minusculas na palavra 

Realizando busca dentro da regex com opções de strings
Ex: React, ReactJS 
/react(js)?/ig ou /react(js){0,1}/
/(react|reactjs)/ig - forma mais verbosa, pois repete as palavras da busca
* () - cria um aninhamento "concatenando" valores de caracteres, variáveis
* ? - Significa que o último caracter ou bloco de agrupamento podem existir nenhuma ou uma vez 
* {0,1} - Significa que podem haver nenhuma ou uma ocorrência de determinado valor
* {0,} - Significa que podem haver nenhuma ou infinitas ocorrências de determinado valor.
* + - Caracter de uma ou mais ocorrências
* * - Caracter de nenhuma ou muita ocorrências, varrendo todos os resultados

* '^' - caracter circunflexo representa o inicio de uma string de caracteres 
* '$' - representa o final da string de caracteres
Ex: Paulo, /^paulo$/ig - faz um match checkando toda a palavra buscada.
Ex: Paulo, /^pa/ig - quero que comece com esses caracteres
Ex: Paulo, /ulo$/ig - quero que termine com esses caracteres

* \ - contra barra é utilizado quando queremos especificar um caracter espacial válido em nossa busca.
Ex: Paulo$, /ulo$\$/ig

O asterisco \* (somente o asterisco sem a barra) que serve para definir uma quantidade de chars, zero ou mais vezes
{} - as chaves que servem para definir uma quantidade de caracteres específicas que é desejado encontrar

representação de busca de um cpf (cadeia de números)
* \d\d\d\.\d\d\d\.\d\d\d-\d\d

quantifier - é utilizado para definir quantas vezes um determinado caracter deve aparecer
* \d{3} - retorna o digito 3x
* \d{3}\.\d{3}\.\d{3}\-\d{2} - cpf utilizando quantifier

##

Exercicio:

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
```

\(\d{2}\) \d{4}-\d{4} - caracteres para numeros de telefone
