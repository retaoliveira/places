---
date: "2021-05-05T00:00:00+01:00"
draft: false
menu:
  intro_r:
    parent: 4 - Estatística descritiva e mineração de dados
    weight: 30
title: Introdução à estatística descritiva
toc: true
type: docs
weight: 30
---

## Estatística descritiva para sumarização de dados com o R

Já apresentamos os operadores relativos às estatísticas descritivas básicas. Segue uma síntese: 

### Operadores aritméticos R

Operador | Descrição
---------|-----------
x + y |	Adição de x com y
x - y	| Subtração de y em x
x * y	| Multiplicação de x e y
x / y	| Divisão de x por y
xy ou x**y	| x elevado a y-ésima potência
x%%y	| Resto da divisão de x por y (módulo)
x%/%y	| Parte inteira da divisão de x por y

### Operadores de comparação no R

Operador	| Significado
----------|------------
==	| igual a
!=	| diferente de
\>	| maior que
<	| menor que
\>=	| maior ou igual a
<=	| menor ou igual a


> Os operadores de comparação sempre retornam um valor lógico TRUE ou FALSE.



### Operadores lógicos no R

Operador|Descrição|Explicação
--------|---------|----------
&|	AND lógico|	Versão vetorizada. Compara dois elementos do tipo vetor e retorna um vetor de TRUEs e FALSEs
&&	|AND lógico|	Versão não-vetorizada. Compara apenas o primeiro valor de cada vetor, retornando um valor lógico.
\|	|OR lógico| Versão vetorizada. Compara dois elementos do tipo vetor e retorna um vetor de TRUEs e FALSEs
\|\|	|OR lógico	|Versão não-vetorizada. Compara apenas o primeiro valor de cada vetor, retornando um valor lógico.
!	|NOT lógico|Negação lógica. Retorna um valor lógico único ou um vetor de TRUE / FALSE.
xor	|XOR	|Ou Exclusivo. Retorna valor lógico TRUE se ambos os valores de entrada forem diferentes entre si, e retorna FALSE se os valores forem iguais.

> Também conhecidos como operadores booleanos, permitem trabalhar com múltiplas condições relacionais na mesma expressão, e retornam valores lógicos verdadeiro ou falso.

### Algumas funções estatísticas para sumarização de dados

Funções | Descrição
--------|----------
`min()`| mínimo  
`max()`| máximo  
`range()`| amplitude   
`mean()`| média   
`sum()`| soma
`median()`| mediana
`sd()`| desvio-padrão
`IQR()`| intervalo interquantil
`quantile()`| quartis
`var()`| variância
`cor()`| correlação
`summary()`| métricas de sumarização
`rowMeans()`| média das linhas
`colMeans()`| média das colunas
`rowSums()`| soma das linhas
`colSums()`| soma das colunas

### Tratamento de dados omissos
O R permite que sejam armazenados, em vetores e data.frames, o valor `NA` (Not Available), que representa dados que ainda não são conhecidos. 


>`x == NA` trará sempre um resultado FALSE, mesmo que `x` não seja conhecido.

<p>
<hr>
<p>

## Atividades de verificação de aprendizagem

**Questão 1:**
Abra o `data.frame` "iris". 

```{r echo=TRUE, message=FALSE, warning=FALSE}
a <- iris
class(iris)
```
a. Calcule estatísticas básicas de cada variável. Copie e cole no Canvas (código e resultado).

Veja o exemplo:

```{r echo=TRUE, message=FALSE, warning=FALSE}
summary(iris$Sepal.Length)
```
b. Para que serve p símbolo `$` após o nome do data.frame?
c. Por meio das funções `hist()` e `boxplot()`, respectivamente, gere um exemplo de cada gráfico para a variável que você escolher. Copie e cole no Canvas. 
