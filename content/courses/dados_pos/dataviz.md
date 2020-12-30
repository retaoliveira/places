---
date: "2020-12-27T00:00:00+01:00"
draft: true
menu:
  dados_pos:
    parent: Unidade 2 - Documentos reprodutíveis
    weight: 19
title: Primeiras visualizações de dados
toc: true
type: docs
weight: 19
---


## Gráficos no R

### Ferramentas básicas de construção de gráficos no R

```{r echo=TRUE, message=FALSE, warning=FALSE}
x1 <- rnorm(100)
y1 <- rnorm(100)
plot(x1,y1)
```


```{r echo=TRUE, message=FALSE, warning=FALSE}
plot(x1,y1,pch=16, col='red')
```


```{r echo=TRUE, message=FALSE, warning=FALSE}
x2 <- seq(0,2*pi,len=100)
y2 <- sin(x2)

plot(x2,y2,type='l')
plot(x2,y2,type='l', lwd=3, col='darkgreen') 

plot(x2,y2,type='l', col='darkgreen', lwd=3, ylim=c(-1.2,1.2));
y2r <- y2 + rnorm(100,0,0.1)
points(x2,y2r, pch=16, col='darkred')
```


## Introdução ao `ggplot` {.tabset .tabset-fade .tabset-pills}

### Sintaxe básica
A sintaxe do package `ggplot` é estruturada por meio da chamada dos dados e complementada pela _aesthetic_ (propriedades do gráfico que vão representar certos elementos dos dados) e por funções que chamam diferentes tipos de gráficos. 

<p>
<hr>
<p>

### Tipos de gráficos com duas dimensões
Gráficos com duas dimensões requerem _aesthetics_ `x` e `y`. Todos esses tipos de gráficos possibilitam o uso de outras _aesthetics_ como `color`, `size` e `fill`. 

Algumas _aesthetics_ básicas são: 

Código | Descrição
-------|----------
x | posição no eixo-x
y | posição no eixo-y
shape | forma
color | cor da borda dos elementos
fill | cor de preenchimento dos elementos
size | tamanho
alpha | transparência (1:opaco; 0:transparente)
linetype | tipo de linha (solid; dashed)

<p>
<hr>
<p>

## Verificação de aprendizagem
**Questão 1:**
Abra o `data.frame` "iris". 

a. Faça um gráfico de dispersão considerando duas variáveis desse data.frame.

+ [Introdução a R para Visualização e Apresentação de Dados by Sillas Gonzaga](http://sillasgonzaga.com/material/curso_visualizacao/)