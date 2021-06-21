---
title: Principais comandos do Git
author: Renata Oliveira
date: '2021-06-21'
slug: principais-comandos-do-git
categories:
  - Análise de dados
  - Git
tags:
  - Git
  - Github
subtitle: ''
summary: ''
authors: []
lastmod: '2021-06-21T16:46:27-03:00'
featured: no
image:
  caption: 'Roman Synkevych'
  focal_point: ''
  preview_only: no
projects: []
---

# O que é Sistema de Controle de Versão?

O sistema de controle de versão é uma estrutura que nos permite acrescentar e supervisionar várias entregas e fases de um item de produto sem realmente manter diferentes documentos ou pastas. Além disso, eles tornam a melhoria dentro de um grupo mais sensata e menos estressante, pois os desenvolvedores não precisam trocar pastas, mas, em vez disso, falam com uma fonte solitária onde cada uma das progressões está acontecendo e tudo é salvo.

## O que é Git?

Git é o VCS (Version Control Systems) mais utilizado. Git rastreia as progressões que você faz nos documentos, assim você tem um registro do que foi feito, e você pode voltar a adaptações explícitas caso você precise a qualquer momento. Git também torna a cooperação mais simples, permitindo que as mudanças feitas por inúmeros indivíduos sejam todas convertidas em uma única fonte.

---
## Agora vamos falar sobre alguns dos comandos úteis de Git que você deve conhecer.

- `git add .`: adiciona todos os arquivos
- `git commit`: registra o arquivo permanentemente
- `git config`: ele controla o conjunto para o projeto/arquivo de salvamento local
- `git help`: exibe todas as informações necessárias sobre os comandos de git
- `git status`: dá todas as informações sobre o ramo atual
- `git log`: conheça os commits anteriores
- `git diff`: realiza um trabalho de difusão de fontes de informação Git. Estas fontes de informação podem ser alterações, ramos, registros e outras.
- `git reset --hard`: apaga todas suas alterações não commitadas | comando perigoso
- `git remoto adicionar <url ou endereço>`: para adicionar um novo endereço remoto
- `git remove rm`: para remover o arquivo do repositório Git
- `git push -u origin master`: para empurrar arquivos locais para o github
- `git branch`: um ramo onde são feitas as alterações - é um arquivo de alterações.
- `git checkout`: permite que você explore entre os ramos gerados pelo git branch
- `tag`: as tags são utilizadas para assinalar uma alteração como importante
- `git fetch`: este comando faz com que seu git local recupere os dados mais recentes da primeira meta-informação
- `git rebase`: você pode pegar cada uma das alterações que foram submetidas a um ramo e reproduzi-las em um ramo alternativo.
- `git config -global color.ui true`: veja cores diferentes em saídas diferentes
- `git init`: cria um novo repositório git
- `git commit -m "Novo arquivo Readme.md"`: salva suas mudanças no repositório local
- `git merge`: permite pegar as linhas autônomas de alterações feitas no ramo e coordená-las em no ramo **main**
- `git pull <repo link>`: para fazer o download da pasta a partir do repositório remoto
- `git stash save`: armazena arquivos rastreados modificados
- `git stash drop`: descarta os arquivos mais recentes 
- `mkdir project`: criar nova pasta de projeto


---

> Dica: Use o Github desktop ou o Git Kraken. Facilitam bem a vida e você não tem que lembrar os comandos diretos.
