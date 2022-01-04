---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Acesso à API do Twitter"
subtitle: ""
summary: ""
authors: []
tags:
  - R
  - Análise textual
  - Twitter
categories:
  - R
  - Análise de dados
date: 2020-12-27T13:39:12-03:00
lastmod: 2020-12-27T13:39:12-03:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Photo by Chris J. Davis"
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

## Como obter e usar tokens de acesso à `API` do `Twitter` para uso no pacote `rtweet`

### Criando um aplicativo no Twitter

Para criar um aplicativo no Twitter, você precisará primeiro solicitar uma conta de desenvolvedor. Este processo, juntamente com uma explicação detalhada pode ser encontrado em [developer.twitter.com](developer.twitter.com).

Uma vez que você tenha adquirido uma conta de desenvolvedor, navegue até [developer.twitter.com/pt/apps](developer.twitter.com/pt/apps). Clique no botão azul que diz: _Create a New App_, e então preencha o formulário com os seguintes campos:

- `App Name`: Como seu aplicativo será chamado
- `Application Description`: Como seu aplicativo será descrito para seus usuários
- `Website URLs`: Website associado ao app-I. Recomendo usar a URL em seu perfil no Twitter
- `Callback URLs`: **IMPORTANTE** digite exatamente o seguinte: `http://127.0.0.1:1410`
- `Tell us how this app will be used`: Seja claro e honesto

Quando você tiver preenchido os campos obrigatórios do formulário, clique no botão azul `Criar`, na parte inferior. Leia atentamente e indique se você aceita os termos do desenvolvedor. 

Mais detalhes podem ser encontrados na [Vignette](https://cran.r-project.org/web/packages/rtweet/vignettes/auth.html) sobre esse processo. 