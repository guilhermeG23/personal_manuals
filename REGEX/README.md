### Regex Básico

5 grupos de expressões regulares
* Metacaracteres literais
* Metacaracteres gerais
* Metacaracteres logicos
* Metacaracteres Quantificadores
* Metacaracteres posicionais

Procuras de texto são literalmente buscas com expressões regulares


Uso de \d é igual a usar o [0-9]

Uso de alguns caracteres especiais são "Uso exclusivo" do regex, dessa forma tem que ter os caracteres de escape, a \ (barra contra)

. = Significa qualquer caractere

\s = Espaço

^ -> Inicio do paragrafo

[] = caixa de caracteres -> Uma seleção de ocorrencia, Ex: [a-zA-z]-> Selecione todos os caracteres entre "a" a "z" em upper e slow case, a caixa de seleção tambem funciona como um grande OU, Ex: [a2] -> Ele vai mostrar todas as ocorrencias de "a" ou "2" do texto alvo

Selecione todos os caracteres que forme uma sequencia \w

Limite a exibição \w{3}, vai mostra somente os seguidos com 3 ou mais ocorrencias iguais
Entre as ocorrencias com {3,5}, entre um range de 3 a 5 repetições de um mesmo caractere


Se existe uma ocorrencia ou não entre um valor, Ex:
color, colour
colo?r = Vai selecionar ambos pq o ? existe ao mesmo tempo que não existe, ele preenche com qualquer coisa, inclusive, nada

* = > Vale para qualquer coisa no meio, se existe ou não
+ => Vale qualquer coisa no meio, más tem que existir algo para operar


Regex é uma linguagem que seleciona tudo oq bata com a regra, uma forma de limitar isso é colocar o ? no fim da regra para limitar a somente a primeira ocorrencia

\d = todos os numeros
\w = todos os caracteres

Usar em maiusculo esses caras faz o efeito de negação, usar o W faz trazer tudo que não é caractere


Uso do OU dentro do operador lógico |, você pode usar ele para variar a pesquisa de um valor


Negar tudo de que apresente certo padrão

[^teste], toda a palavra teste será negada na analise e toda a estrutura parecia será negada tambem

Selecionar somente o primeiro valor de uma decisão, Ex: teste(?=\1), isso é, só vai trazer para mim, os testes que tiveram o 1 seguido com espaço sobre os testes

A forma negativa de seu uso é trocar o = por ! como negação

\b = boundre, limitador de uma palavra


___

Exemplos:

```[0]``` -> Mostra todas as ocorrencias de 0 dentro do texto;
```[0][0]``` -> Mostra todas as ocorrencias de 00 dentro do texto;
```[0]{2}``` -> Mostra todas as ocorrencias com o operador de multiplicação, é o mesmo 00, más esse é de uma forma mais inteligente de fazer;
```[0-9]{6}``` -> Todas as ocorrencias de 0 a 9 dos 6 primeiros caracteres alvo;
```[0-9]{6}$``` -> Todas as ocorrencias de 0 a 9 dos 6 ultimos caracteres alvo, Ex: numa linha com 10 numeros, ele vai selecionar os 6 ultimos numeros desses 10;
```^[0-9]{6}$``` -> Todas as ocorrencias de 0 a 9 dos 6 primeiros caracteres alvo com fim de seleção, isso é, só será selecionada a primeira palavra das frases que tenha 6 caracteres e tenha numeros;
```^[0-9]+$``` -> O + é uma seleção sem fim de caracteres, ele é modular, podendo selecionar de 1 a infinito;

