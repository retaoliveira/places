---
date: "2021-05-05T00:00:00+01:00"
draft: false
menu:
  intro_r:
    parent: 3 - Estrutura de dados no R
    weight: 10
title: Tipos de dados, objetos e operadores no R
editor_options: 
  markdown: 
    wrap: 70
output: 
  blogdown::html_page:
    toc: true
type: docs
weight: 40
---


### Tipos de dados no R {.tabset .tabset-fade .tabset-pills}

No R, os dados são organizados por meio de uma estrutura hierárquica de tipos de dados que podem ser utilizados para armazenar valores em diferentes estruturas. Cada tipo de dado pode ser associado com uma função de teste e uma função de conversão. 

A função de teste retorna sempre `TRUE` ou `FALSE`, pois é uma `função lógica`. 

A função de conversão, quando possível, transforma os dados em diferentes tipos. 

Funções de teste apresentam a estrutura `is.character()` e funções de conversão são `as.character()`. 

Neste curso não detalharemos todos os tipos de dados, mas apresentaremos apenas os mais importantes para a análise de dados em caráter exploratório. No blog, temos diversas sugestões de tutoriais e documentação geral que contempla todos os tipos de dados e capacidade de interoperabilidade do R.

#### Character
Variáveis `character` são aquelas que contém texto. Para designar uma variável como texto, precisamos colocar seus valores entre aspas. Dados do tipo texto são comuns em variáveis categóricas. 

Experimente:


```r
d <- "texto"
is.character(d)
```

```
## [1] TRUE
```

#### Numeric

Dados `numeric` são números. A função `numeric` pode ser utilizada para gerar um vetor com elementos numéricos com valor 0. 

Faça:


```r
# Criar vetor de cinco posições com valores 0
numeric(5)
```

```
## [1] 0 0 0 0 0
```

```r
# Gera valor character
e <- "1980"

# Teste
is.numeric(e)
```

```
## [1] FALSE
```

```r
# Conversão
f <- as.numeric("1980")

# Teste
is.numeric(f)
```

```
## [1] TRUE
```

#### Logical
A função `logical` gera um vetor lógico com o tamanho desejado e por padrão, cada elemento do vetor recebe o valor `FALSE`. 


> Um objeto de qualquer uma desses tipos é chamado de **objeto atômico**.

Mãos à obra:


```r
logical(3)
```

```
## [1] FALSE FALSE FALSE
```

```r
# Conversão
as.logical(c(7,5,0))
```

```
## [1]  TRUE  TRUE FALSE
```

```r
# TRUE e FALSE podem ser convertidos em 1 ou 0
as.logical(c(7,5,0))*1
```

```
## [1] 1 1 0
```
Os valores no vetor que são diferentes de *zero*, recebem o valor `TRUE`. 

> A função **`c`**(*combine*) é utilizada para composição de um vetor, combinando valores identificados por índices.


### Tipos de classes no R {.tabset .tabset-fade .tabset-pills}
 
Diferentes tipos de dados podem ser utilizados para popular diferentes estruturas de dados ou `classes`. As classes mais comumente utilizadas para análise de dados espaciais são: vetores, matrizes, data frames, listas e factores. 

É por meio das classes que as funções e operadores conseguem saber exatamente o que fazer com um objeto. 

Experimente:


```r
1+1
```

```
## [1] 2
```

Faça `"a" + "b"`

O operador `+` verifica que "a" e "b" não são números (ou que não são do tipo `numeric`) e devolve uma mensagem de erro informando isso. 

#### Vetores
O R é construído com base no conceito de vetores e matrizes. As maior parte das operações é feita para os elementos.


```r
# Definição de vetores
vector(mode = "numeric", length = 8)
```

```
## [1] 0 0 0 0 0 0 0 0
```

```r
vector(length = 8)
```

```
## [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
```

```r
tmp <- data.frame(a=10:15, b=15:20)
```

#### Fatores
Fatores são vetores de categorias específicas, definidas por meio do parâmetro `levels`. A ordem dos fatores pode ser especificada pela função `ordered`. Experimente:


```r
# Vetor de texto
tipos.casas <- c("casa", "apartamento", "apartamento", "sobrado")

# Vetor de fatores
tipos.casas <- factor(c("casa", "apartamento", "apartamento", "sobrado"), levels=c("casa", "apartamento", "sobrado"))
```

Quando utilizamos dados em estrutura de fatores, é possível gerar sínteses rápidas e simples por meio da função `table`. 


```r
table(tipos.casas)
```

```
## tipos.casas
##        casa apartamento     sobrado 
##           1           2           1
```

Dados fatoriais são úteis para o tratamento de dados categóricos, ou que pertencem a um determinado número de classes predeterminadas. Existem muitas feições representadas por meio de dados espaciais que são estruturadas em variáveis discretas. 

LEMBRANDO..... Dados podem ser:
![Discretos x Contínuos](https://retaoliveira.github.io/relements/figures/continuous_discrete.png)
![Discreto x Contínuo](https://retaoliveira.github.io/relements/figures/nominal_ordinal_binary.png)


Para ordenar dados fatoriais, utilizamos a função `ordered`. 


```r
renda_1 <- factor(c("alta", "alta", "baixa", "baixa", "media", "alta"), levels=c("baixa", "media", "alta")) 

renda_2 <- ordered(c("alta", "alta", "baixa", "baixa", "media", "alta"), levels=c("baixa", "media", "alta")) 
```

#### Listas

Os tipos de dados `character`, `numeric` e `logical` só podem ser associados a classes de dados nas quais TODOS os elementos são do mesmo tipo. A classe `listas` não tem esse requisito. As listas têm posições (índices) para diferentes topos de elementos. 

Para acessar um elemento em um vetor, utilizamos `[]`. 


```r
vector_teste <- c(5:10)
vector_teste
```

```
## [1]  5  6  7  8  9 10
```

```r
vector_teste[4]
```

```
## [1] 8
```

Para acessar um elemento em uma lista por meio de sua posição, utilizamos `[[]]`. 


```r
colaborador <- list(name="Renata Oliveira", ano.inicio = 2006, posicao = "Professora")
colaborador
```

```
## $name
## [1] "Renata Oliveira"
## 
## $ano.inicio
## [1] 2006
## 
## $posicao
## [1] "Professora"
```

#### Matrizes, data.frames e tibble
Matrizes são um conjunto de vetores. As linhas e colunas das matrizes podem ser nomeadas. Na análise espacial de um dado vetorial, temos uma tabela de atributos em estrutura matricial. As linhas representam as feições e as colunas são os atributos dessas feições. Na representação de dados raster, linhas e colunas representam latitudes e longitudes ou células raster. 

`Data frames` e `tibble` são estruturas tabulares de dados que, diferentemente das matrizes (`matrix`), permitem representar diferentes atributos (e tipos de dados) em diferentes colunas. Esses tipos de classes são utilizadas para organizar dados espaciais (pontos, linhas, áreas e pixels).


Em tabelas de dados espaciais, cada informação representa um fenômeno real por meio de uma feição geográfica e os campos representam atributos associados com cada feição (população, área, altitude etc.). 


A classe `data.frame` no R é composta por uma série de vetores de **comprimento igual** (número de observações) que juntos formam uma estrutura de dados bi-dimensional. Cada vetor registra valores de um atributo específico. Essa é a classe de dados mais comumente utilizada para armazenar dados no R. 


```r
df <- data.frame(dist=seq(0, 400, 100), city=c("Belo Horizonte", "São Paulo", "Rio de Janeiro", "Brasília", "Salvador"))
str(df)
```

```
## 'data.frame':	5 obs. of  2 variables:
##  $ dist: num  0 100 200 300 400
##  $ city: chr  "Belo Horizonte" "São Paulo" "Rio de Janeiro" "Brasília" ...
```
> A função `seq` possibilita a criação de uma sequência de dados por meio de três parâmetros: seq(`valor_inicial`, `valor_final`, `intervalo`). 

Tibbles e data.frames não são muito diferentes. Há alguns detalhes quanto à transformação de dados na criação dessas classes, mas, em linhas gerais, a estrutura de dados em `tibble` é mais eficiente e organizada. 

As seguintes funções são adequadas tanto para `data.frames` como para `tibble`:   
`names()`   
`colnames()`   
`rownames()`   
`length()`   
`ncol()`   
`nrow()`   

> Explore a documentação do `tibble` em: `vignette("tibble")`


Os objetos dessas duas classes podem ser selecionados por meio da estrutura `data.frame[linha, coluna]`, na qual os parâmetros linhas e coluna são os índices desses elementos. 

Para combinar `data.frame` e `tibble` por linhas ou colunas utilizamos, respectivamente, as funções `rbind()` e `cbind()`.


Até aqui, já ficou claro que a escolha ou identificação dos tipos e das classes de dados espaciais e não espaciais é muito importante para sua análise. 

Algumas funções para manipulação de dataframes:

head() # - Mostra as primeiras 6 linhas.   
tail() #  - Mostra as últimas 6 linhas.   
dim() # - Número de linhas e de colunas.   
names() # - Os nomes das colunas (variáveis).   
str() # - Estrutura do data.frame. Mostra, entre outras coisas, as classes de cada coluna.   
cbind() # - Acopla duas tabelas lado a lado.   
rbind() # - Empilha duas tabelas.   

# Dicas de sites com informação interessante

https://lhmet.github.io/adar-ebook/vetor.html

http://leg.ufpr.br/~fernandomayer/aulas/ce083-2016-2/02_funcoes_e_objetos.html

http://www.estatisticacomr.uff.br/?p=564

https://livro.curso-r.com/3-r-base.html

https://www.msperlin.com/padfeR/operacoes-basicas.html

