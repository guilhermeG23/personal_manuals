# Manual simples de makedown

___

### Objetivo:

Esse manual tem o objetivo de apresentar a construção de arquivos **MD** sem o uso de tags **HTML**;
___

Markdown é uma linguagem simples de marcação originalmente criada por John Gruber e Aaron Swartz. Markdown converte seu texto em HTML válido. Markdown é frequentemente usado para formatar arquivos README, para escrever mensagens em fóruns de discussão online e para criar rich text usando um editor de texto simples. [Wikipédia](https://pt.wikipedia.org/wiki/Markdown)

___

### Títulos

Como o **HTML**, o MD tem 6 níveis de títulos;

**Exemplo em MD** 
```
# Teste
## Teste
### Teste
#### Teste
##### Teste
###### Teste
```


O referênte está abaixo:

* # # h1 Teste;
* ## ## h2 Teste;
* ### ### h3 Teste;
* #### #### h4 Teste;
* ##### ##### h5 Teste;
* ###### ###### h6 Teste;

___

### Alternativas do "#"

Pode se utilizar os:
* "===" é igual a "#";
* "---" é igual a "##";

Exemplo desses estão abaixo:

Este utiliza o ===
===

Este utiliza o ---
---

___

### Separar linhas


Se utiliza o ```___``` como separador de linhas, o mesmo que a tag ```<hr>``` no **HTML**;

____

### Texto normal

O texto normal não precisa colocar nenhuma marcação, somente escrevê-lo;

___

### Quebrando a linha

Use ```&nbsp;``` para quebrar as linhas, Ex:

```
teste

&nbsp;

teste
```

A saída é:

teste

&nbsp;

teste

___

### Decoração de texto

Não misture métodos de decoração, só dificulta o entendimento final:

##### Itálico:
* *Teste* -> ```*Teste*```
* _Teste_ -> ```_Teste_```

##### BOLD:
* **Teste** -> ```**Teste**```
* __Teste__ -> ```__Teste__```

##### Tachar
* ~~Teste~~ -> ```~~Teste~~```

##### Justando ambos:
* ***Teste*** -> ```***Teste***```
* ___Teste___ -> ```___Teste___```

##### Mistureba (Não recomendado, más possível):
* *__Teste__* -> ```*__Teste__*```
* _**Teste**_ -> ```_**Teste**_```
* **_Teste_** -> ```**_Teste_**```
* __*Teste*__ -> ```__*Teste*__```

____

#### Listas

Valores que se podem ser usados para criar uma lista: *, -, +

Uso prático:
* Uso do ```*``` 
+ uso do ```+```
- Uso do ```-```

Exemplo de **MD**:
```
* Uso do ```*``` 
+ uso do ```+```
- Uso do ```-```
```

Não é recomendavél misturar eles.

Podemos fazer nível tambem, **Exemplo:**

* teste
    * test
        * teste
        
ou:

```
* teste
    * test
        * teste
```

Tem tambem sobre os valores numéricos, **Exemplo:**

| MD | Resultado | 
| --- | --- |
| ```1. teste``` | 1. teste |
| ```5. teste``` | 2. teste |
| ```7. teste``` | 3. teste |
| ```2. teste``` | 4. teste |
| ```4. teste``` | 5. teste |
###### tabela simulada

Esses valores sempre vão seguir numéricamente, então não importa o valor antes do ponto, ele será controlá-do pelo primeiro valor, como **exemplos:**

**MD:**
```
1. teste
4. teste
```
**Saída:**

1. teste
4. teste

**MD:**
```
3. teste
3. teste
66. teste
    1. teste
    3. teste
```
**Saída:**

3. teste
3. teste
66. teste
    1. teste
    3. teste

**Justando dois:**

1. Teste
3. Teste
    - Teste
    - Teste
        - Teste
4. Teste

Ou:

```
1. Teste
3. Teste
    - Teste
    - Teste
        - Teste
4. Teste

```
____

### Bloco de citação

Bloco de citação, **Exemplo:**

```
>Teste
```

O resultado é: 

>Teste

Pode se fazer assim para multiplas linhas:

```
>Teste
Teste
```

O resultado é:

>Teste
Teste
teste

Também é possível colocar níveis, como:

> teste
>> teste
>>> teste
>>>>> teste
>>>>>>>>>>>>>>>>> teste
>>>>>>>>>>>>>>>>>> teste
>>>>>>>>>>>>>>>>>>> teste
>>>>>>>>>>>>>>>>>>>> teste

Seguindo essa construção em  **MD**:

```
> teste
>> teste
>>> teste
...
```
____

### Misturas

Eu não recomendo fazer muito, más é possível, Ex:

> teste
> 1. teste
> * teste
>   * teste 
> > * teste
> > - teste

Em **MD** é isso: 
```
> teste
> 1. teste
> * teste
>   * teste 
> > * teste
> > - teste
```
____

### Blocos de código

Demonstração:

```
teste
```

~~~
teste
~~~

Construção em **MD**:
```
` ` `
teste
` ` `
~~~
teste
~~~
```

Também é possível demonstrar a síntese colorida de várias linguagens (Tem o suporte de muitas linguagens), Ex:

* Javascript com o bloco em ``` ` ` ` ``` 
```javascript
alert("teste");
```

&nbsp;
* Javascript com o bloco em ``` ~~~ ``` 
~~~javascript
alert("teste");
~~~

&nbsp;
* PHP
~~~php
echo "teste";
~~~

&nbsp;
* HTML
~~~html
<h1>Teste</h1>
~~~

&nbsp;
* Python
~~~python
import sys
print("teste")
~~~

Em **MD** o resultado fica:
```
* Javascript com o bloco em  ` ` `  
` ` `javascript
alert("teste");
` ` `

&nbsp;
* Javascript com o bloco em  ~~~  
~~~javascript
alert("teste");
~~~

&nbsp;
* PHP
~~~php
echo "teste";
~~~

&nbsp;
* HTML
~~~html
<h1>Teste</h1>
~~~

&nbsp;
* Python
~~~python
import sys
print("teste")
~~~
```



____

### Imagens

Uso de imagens com MD:

![RSA](rsa.png)

Para fazer isso use:

```
![RSA](rsa.png)
```

____

### Tabela

Criando uma tabela, **Exemplo:**

| Cabeçalho | teste | teste | teste| 
| --- | --- | --- | --- |
| Corpo | teste | teste | teste |

**MD:**

```
| teste | teste | teste | teste| 
| --- | --- | --- | --- |
| teste | teste | teste | teste |
```

Tem que se utilizar o divisor ```| --- |``` para separar o cabeçalho do corpo;

Lembrando que a quantidade de ```---``` não importada, tem de haver no minimo um para a criação, forá que é recomendado ter o mesmo tamanho a todos para a facilidade de vizualização.

Para se criar mais colunas, deve-se criar a quantidade igual entre **Cabeçalho** e **Divisor**;


Nas tabelas também é possível acertar o alinhamento dos conteúdos, Ex: 

| Olha para a esquerda | Olha para o meio | Olha para a diretira |
|:- |:-:| -:|
| Esquerda  | Centro    | Direita |

Em **MD** fica assim:

```
| Olha para a esquerda | Olha para o meio | Olha para a diretira |
|:- |:-:| -:|
| Esquerda  | Centro    | Direita |
```

Faz o uso do : na posição que deseja para realizar o alinhamento.

___

### Links

Para se criar um link de redirecionar:

[Teste](#)

**MD:**
```
[Teste](#).
```

Uso de váriaveis de links:

[teste][1]

[1]: <#> "Teste"

Ou:

**MD:**
```
[teste][1]

[1]: <#> "Teste"
```

___

### Juntando um link com imagem

Criando uma imagem com link:

[![teste](rsa.png "RSA")](#)


Ex:
```
[![teste](rsa.png "RSA")](#)
```

____
