---
title: Tutoriais interativos
author: ''
date: '2021-01-20'
slug: tutoriais-interativos
categories: []
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2021-01-20T15:02:24-03:00'
featured: no
image:
  caption: 'Photo by Stefano Intintoli'
  focal_point: ''
  preview_only: no
projects: []
---

Fiquei pensando em como posso ajudar os estudantes no desenvolvimento de competências no R com tão pouco tempo e remotamente. Uma possibilidade que consegui viabilizar são tutoriais interativos. São atividades eletivas também, mas FORTEMENTE recomendadas! No site os estudantes podem encontrar as informações necessárias para utilizar as funções e podem sempre consultar o "oráculo" universal Google. 

Os estudantes um procedimento breve para conseguirem abrir o tutorial:

1. Salvar o arquivo nesta mensagem em um diretório em seu computador. 
2. Abrir o RStudio e procedam com a instalação do package swirl: `install.packages("swirl")`
3. Carregar a biblioteca do swirl: `library(swirl)`
4. Instalar o tutorial: `install_course()`
	- uma janela de navegação permitirá a seleção do arquivo desta mensagem em seu computador.
5. Abrir o menu de tutoriais `swirl::swirl()`
6. Digitar o número referente à alternantiva R_business. Caso essa opção não esteja disponível, digitar o último valor que o tutorial aparecerá no novo menu. 
7. Selecionar 1: `introR`

Mãos à obra! Bom tutorial!!!! Por enquanto são cinco tutoriais autoexplicativos e interativo.  

In a `chunk`:

```{r }
install.packages("swirl")
library(swirl)

install_course()
swirl()
```

O arquivo pode ser acessado no [link](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/ERP-1p3qFR1MiftEt5n0kwkBwzxgRSVTlLFeRKe9QLKXIQ?e=0NopHG)

Bonus: Existem vários cursos disponíveis online. Para acessá-los, veja o [Swirl Course Network](http://swirlstats.com/scn/). A instalação é feita também com a função `install_course()`, mas nesse caso você precisa digitar o nome do curso como em: 

```{r}
swirl::install_course("A_(very)_short_introduction_to_R")
```

