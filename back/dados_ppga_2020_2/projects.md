---
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  dados_pos:
    parent: Projetos
    weight: 5
title: Projeto Integrador
toc: true
type: docs
weight: 10
---

Os projetos integradores são parte estruturante do curso e, portanto, visam promover a sistematização e a consolidação da aprendizagem. Ainda, tem como objetivo proporcionar aos estudantes a capacidade de implementação do conhecimento adquirido ao longo deste curso de maneira aplicada e em uma situação-problema real. 

Este projeto será desenvolvido ao longo de toda a disciplina e deve ser relacionado com cada unidade de ensino. Seu conteúdo deve ser estruturado seguindo normas cultas de linguagem, clareza em relação ao problema em investigação e aos objetivos propostos. 

Consideraremos três dimensões para construção do projeto integrador:

- Situações-problemas: a aprendizagem deve ser iniciada com situações reais e do cotidiano. A ideia é criar um olhar investigativo para o mundo

- Conteúdos interdisciplinares e práticos: rompe com as fronteiras tradicionais do conhecimento, ao passo que relaciona disciplinas e até mesmo promove a articulação de áreas. Além disso, a produção de conhecimento do projeto integrador deve ser aplicável em situações reais.

- Trabalho coletivo: desenvolve as habilidades dos alunos para trabalhar em equipe.

## Etapas essenciais para desenvolvimento de um projeto de suporte à decisão que contemple análise de dados

1. Definição do problema - O primeiro e mais crítico passo é delinear as questões que pretende abordar por meio da análise de dados e desenhar hipóteses a partir da caracterização do problema.
2. Coleta de dados - A coleta de dados é um passo muito crucial e não tão fácil como parece. O processo requer tempo e esforço. Nenhum conjunto de dados contém dados como se espera e envolve pesquisa, arranjos, reordenações e montagem final.
3. Limpeza e transformação de dados - Se quiser que os seus resultados sejam consistentes, deve certificar-se de que a limpeza dos dados foi feita corretamente. Na essência, a limpeza de dados elimina dados desnecessários e duplicados da coleta de dados.
4. Representação dos dados - representações gráficas permitem importantes insights sobre o fenômeno ou processo em investigação. 
5. Análise dos dados - Nesta fase, tem de detectar tendências e padrões nos dados coletados, agrupá-los em conformidade, e compreender o comportamento dos dados para que seja possível caracterizar o processo em investigação.
6. Modelagem dos dados - Nesta fase, os dados são divididos em duas partes - uma para formação e desenvolvimento de modelos, e a outra para testes.
7. Otimização e implementação do modelo - Nesta etapa, o modelo é implementado visando acurácia e eficiência das análises.
8. Comunicação da análise, discussão e resultados. Nessa etapa, os grupos deverão reservar parte do instrumento de comunicação para discussão ética do uso dos dados para a análise em curso e discutir implicações nos curso, médio e longo prazos para a sociedade, apresentando aspectos positivos e negativos da exploração de dados para suporte ao processo decisório em questão.

Nesse projeto, em função da natureza da disciplina que tem como objetivo proporcionar aos estudantes competências para realização de análise exploratória de dados, as etapas 6 e 7 não serão exploradas no projeto integrador.

## Entregas parciais

As entregas parciais deverão ser realizadas conforme o cronograma a seguir que está alinhado com as etapas apresentadas anteriormente:

| Data | Etapa concluída |
|------|-----------------|
|09/02|Descrição do problema em investigação, hipóteses desenhadas pelo grupo, coleta preliminar de dados e plano de análise dos dados|
|06/04|Dados processados (limpeza e transformação) e estrutura do instrumento de comunicação esboçada. Representação do problema e dos instrumentos de análise orientada pelos dados|
|13/04|Análise e discussão dos resultados e instrumento de comunicação final e apresentação do instrumento final para a turma|

## Organização das atividades:

1. **Composição dos grupos de trabalho:** Cada grupo será composto por **4 (quatro) alunos**. Esse grupo deve se manter para realização dos `PROJETOS INCREMENTAIS`, realizadas após e antes dos encontros síncronos, e para construção do `PROJETO INTEGRADOR`. 

2. **Planejamento da execução do trabalho:** Definir um cronograma a priori, contemplando entregas parciais alinhadas com os projetos e acompanhar as etapas de execução. 


### Ideias para desenvolvimento do projeto integrador

Para que você tenha a maior chance de sucesso neste projeto, é importante que você escolha um conjunto de dados adequado. Isto significa que os dados devem ser prontamente acessíveis e suficientemente grandes para que múltiplos relacionamentos possam ser explorados. Como tal, seu conjunto de dados deve ter pelo menos 50 observações e entre 10 a 20 variáveis (exceções podem ser feitas, mas você deve falar comigo primeiro). As variáveis do conjunto de dados devem incluir variáveis categóricas, variáveis numéricas discretas e variáveis numéricas contínuas.

Se você estiver usando um conjunto de dados que vem em um formato que não trabalhamos no curso, certifique-se de que você seja capaz de carregá-lo em R, pois isso pode ser complicado dependendo da fonte. Se você estiver tendo problemas, peça ajuda antes que seja tarde demais.

> `Nota sobre a reutilização de conjuntos de dados da classe:` Não reutilizar conjuntos de dados usados em exemplos, tarefas de casa ou laboratórios da classe.

Abaixo segue uma lista de repositórios de dados que podem ser de interesse. Você não está limitado a estes recursos e, de fato, é encorajado a se aventurar além deles. 

- [TidyTuesday](https://github.com/rfordatascience/tidytuesday)
- [NHS Scotland Open Data](https://www.opendata.nhs.scot/)
- [Edinburgh Open Data](https://edinburghopendata.info/)
- [Open access to Scotland’s official statistics](https://statistics.gov.scot/home)
- [Bikeshare data portal](https://www.bikeshare.com/data/)
- [UK Gov Data](https://data.gov.uk/)
- [Kaggle datasets](https://www.kaggle.com/datasets)
- [OpenIntro datasets](http://openintrostat.github.io/openintro/)
- [Awesome public datasets](https://github.com/awesomedata/awesome-public-datasets)
- [Youth Risk Behavior Surveillance System (YRBSS)](https://chronicdata.cdc.gov/Youth-Risk-Behaviors/DASH-Youth-Risk-Behavior-Surveillance-System-YRBSS/q6p7-56au)
- [PRISM Data Archive Project](https://www.icpsr.umich.edu/icpsrweb/content/ICPSR/fenway.html)
- [Harvard Dataverse](https://dataverse.harvard.edu/)

Algumas ideias para desenvolvimento do projeto são apresentadas a seguir. Essas ideias não são compulsórias. O grupo pode propor outros problemas para serem analisados. O importante é ter em mente que os dados para caracterização de determinados processos ou fenômenos podem não estar abertos e disponíveis. 

**1. Análise de Sentimento** 

A análise dos sentimentos é o processo de análise das palavras para determinar opiniões e sentimentos que têm diferentes polaridades - positivas, negativas ou neutras. O método também se baseia nos nomes `polarity detection e opinion mining`. Nesse tipo de classificação, os dados (sentimentos) são categorizados em diferentes classes; estas classes podem ser binárias (positivas e negativas), neutras ou múltiplas (felizes, tristes, zangadas, e assim por diante).

O processo de análise dos sentimentos pode ser utilizado para determinar a natureza das opiniões refletidas nos websites, feeds das redes sociais, documentos, etc. 

**2. Análise de dados de Uber ou de dados de mobilidade da Google e da Apple** 

Uma componente crucial da aprendizagem de máquinas é a narrativa de dados; esse processo ajuda as empresas a compreenderem o histórico e o contexto de várias operações, assim como gestores públicos a entenderem os fenômenos urbanos, por exemplo. A visualização de dados ajuda os gestores a compreender conjuntos de dados complexos, o que, por sua vez, suporta as decisões.

A análise de dados de mobilidade é um projeto de visualização de dados, onde `R` e as suas bibliotecas são utilizadas para analisar parâmetros ou variáveis como as `viagens durante um dia`, ou as `viagens mensais durante um ano`. Estas visualizações para diferentes períodos de tempo e em diferentes escalas podem ser geradas utilizando o 'Uber Pickups in New York City Dataset' ou os dados de mobilidade da Google e da Apple disponibilizados a partir do início da pandemia. As bibliotecas e pacotes essenciais do `R` que precisam de ser importados para este projeto incluem, por exemplo - `ggplot2`, `ggthemes`, `lubridate`, `dplyr`, `tidyr`, `DT`, e `scales`.

**3. Sistema de Recomendação de Filmes** 

Já alguma vez se perguntou como é que o `Netflix` sugere filmes e séries web dos generos que lhe atraem instantaneamente? Diferentes plataformas de streaming como `Netflix` e `Amazon Prime` utilizam algo conhecido como o `Sistema de Recomendação`; esse sistema utiliza um processo de seleção e classificação para sugerir conteúdos com base nas preferências do utilizador, padrões de observação e histórico de navegação. Os dados de navegação do utilizador fornecem a entrada para o Sistema de Recomendações.

Enquanto um Sistema de Recomendação baseado no conteúdo sugere filmes que são semelhantes ao que se viu no passado, a `Recomendação de Filtragem Colaborativa` fornece sugestões com respeito a outros utilizadores com as mesmas preferências e históricos de visualização. 

Essa ideia pode ser realizada para análise de dados do `Spotify` ou da `Amazon`, por exemplo.

É possível ainda explorar bases como o `imdb`, que permitem investigar as produções cinematográficas. 

**4. Segmentação de clientes**

A `segmentação de clientes` é um dos tópicos mais importantes para a gestão estratética e mercadológica de empresas. Sempre que as empresas precisam de identificar potenciais clientes, podemos considerar o método de Segmentação de Clientes. Por meio desse método, a base de clientes é dividida e agrupada de acordo com algumas características semelhantes que são relevantes para o mercado, tais como idade, sexo, interesses, e hábitos de despesa.

É uma forma eficiente para as empresas desenvolverem as suas estratégias de marketing com uma probabilidade reduzida de `riscos` relacionados com o investimento. Os dados coletados pelas empresas ajudam-nas a compreender melhor as preferências e requisitos dos clientes individuais, o que pode gerar vantagens competitivas. 

**5. Predição de Preferência de Vinho** 

A prova de vinhos é uma profissão única em si mesma. Pode ser bastante desafiante prever o que o cliente pode gostar, com base nas suas preferências passadas. Contudo, seria mais fácil para os restaurantes recomendar um vinho aos seus clientes se os seus gostos e preferências fossem previamente identificados. As propriedades físico-químicas do vinho podem ser utilizadas para processos de extração de dados e identificar as preferências dos clientes. 

A abordagem adotada no projeto de Previsão das Preferências do Vinho e sua relação com preço de venda, pode ser aplicada a produtos semelhantes para modelar os gostos dos clientes, ajudando assim no marketing alvo. Uma base disponível para essa análise é a do aplicativo `Vivino`. 

**6. Análise da adesão ao distanciamento social como medidas não farmacológicas de contenção da difusão do COVID-19**

Caracterizar a adesão da população ao distanciamento por meio dos dados de mobilidade da Google e da Apple e relacionar os níveis de adesão em diferentes localidades com, por exemplo, índices de desenvolvimento humano. 

**7. Análise do Legislativo Brasileiro**
Entendimento dos padrões de votação e outras atividades do corpo legislativo Brasileiro ao longo dos anos por meio do package `bRasilLegis`.

### Rubrica de avaliação

Embora a presença nos encontros síncronos não seja explicitamente acompanhada, a participação neste curso conta para sua nota. A seguir, são apresentados os critérios considerados para a avaliação do projeto integrador que são úteis para nortear o desenvolvimento do trabalho. Esta atividade será avaliada em `40 pontos`.

> Certifique-se que você está cadastrado ao servidor da disciplina no `Teams`, pois o processo de desenvolvimento do projeto será tão importante quanto seu resultado para a avaliação e eu acompanharei as discussões, análises e resultados por lá. 

Os `40 pontos` serão distribuídos em: 

|Item|Pontuação
|----|-----------------
|Relatório/instrumento de comunicação|25
|Apresentação do projeto|5
|Trabalho em equipe - avaliação pelos pares|10

Segue a discriminação geral da pontuação:

- `90%-100% `- **Esforço notável**. O estudante compreende como aplicar os fundamentos considerados na análise, pode argumentar de maneira consistente, pode identificar fraquezas no argumento e pode comunicar claramente os resultados.
- `80%-89%` - **Bom esforço**. O estudante compreende a maioria dos conceitos, reúne um argumento adequado, identifica alguns pontos fracos de seu argumento e comunica claramente a maioria dos resultados aos outros.
- `70%-79%` - **Esforço para aprovação**. O estudante tem uma má compreensão dos conceitos em diversas áreas, tem alguma dificuldade em juntar resultados em um argumento convincente, e a comunicação dos resultados às vezes não é clara.
- `60%-69%` - **Esforço limítrofe**. O estudante está fazendo algum esforço, mas tem uma má compreensão de muitos conceitos e é incapaz de montar um argumento convincente. A comunicação dos resultados não é clara.
- `Abaixo de 60%` - O estudante não está fazendo um esforço suficiente.


#### Relatório/Instrumento de comunicação

##### 1. Caracterização do problema em análise (5 pontos)
|Item|Pontuação
|----|-----------------
|Relevância do problema para o contexto do processo decisório|1
|Necessidade de investigação orientada por dados para suporte ao processo decisório|1
|Pertinência das hipóteses geradas|1
|Consistência do objetivo geral proposto|2

##### 2. Organização, limpeza e transformação dos dados (5 pontos)

|Item|Pontuação
|----|-----------------
|Escolha das fontes para coleta de dados|2
|Escolha e implementação dos instrumentos para organização e limpeza dos dados|1
|Organização final dos dados |1
|Escolha e implementação das variáveis e indicadores para análise|1

##### 3. Representação dos dados para suporte à decisão (5 pontos)

|Item|Pontuação
|----|-----------------
|Escolha e implementação dos instrumentos de visualização|1
|Reprodutibilidade da visualização|2
|Capacidade de representação do fenômeno ou processo em análise|1

##### 4. Instrumento de comunicação RMarkdown (5 pontos)

|Item|Pontuação
|----|-----------------
|Formalidade textual|1
|Conteúdo do instrumento representa o desenvolvimento do trabalho|1
|O instrumento é objetivo quanto à caracterização do problema|1
|Reprodutibilidade do instrumento de comunicação|1
|Adequação dos instrumentos de comunicação ao público-alvo|1

##### 5. Resultados e discussões (5 pontos)

|Item|Pontuação
|----|-----------------
|Interpretação das condicionantes dos problemas em investigação|1
|Discussão dos dados em relação às hipóteses inicialmente determinadas|1
|Discussão de preceitos éticos do uso de dados no contexto do trabalho|1
|Discussão das implicações no curto, médio e longo prazos para a sociedade|1
|Criatividade e pensamento crítico|1


#### Apresentação do projeto (5 pontos)

10 minutos no máximo, e cada membro da equipe deve dizer algo substancial. Você pode apresentar ao vivo durante o encontro ou pré-gravar e enviar seu vídeo para ser reproduzido durante o encontro.

Prepare um `slide deck` usando o pacote chamado `xaringan` e sintaxe R Markdown. Não há um limite para quantos slides você pode usar, apenas um limite de tempo (10 minutos no total). Cada membro da equipe deve ter a oportunidade de falar durante a apresentação. Sua apresentação não deve ser apenas um relato de tudo o que você tentou ("então fizemos isto, depois fizemos isto, etc."), mas deve transmitir **quais escolhas você fez, e por quê, e o que você encontrou**.

O esquema de notas (rubrica) para a apresentação é o seguinte:

|Item|Pontuação
|----|-----------------
|Gerenciamento de tempo: A equipe dividiu bem o tempo entre si ou foi cortada ao longo do tempo?	|1
|Conteúdo: A questão da pesquisa está bem projetada e os dados estão sendo usados de forma relevante para a questão da pesquisa?|1
|Profissionalismo: Até que ponto a equipe se apresentou bem? A apresentação parece ter sido bem praticada? Todos tiveram a oportunidade de dizer algo significativo sobre o projeto?|1
|Trabalho em equipe: A equipe apresentou uma história unificada, ou pareceu um trabalho independente remendado em conjunto?|1
|Slides: Os slides são bem organizados, legíveis, não estão cheios de texto, apresentando figuras com etiquetas legíveis, lendas, etc.?|1


#### Trabalho em equipe - avaliação pelos pares (10 pontos)

Você deverá preencher uma pesquisa onde avaliará a contribuição e o trabalho em equipe de cada membro da **SUA** equipe em `10 pontos`. Além disso, você informará um percentual de contribuição para cada membro da equipe. O preenchimento desse formulário é um pré-requisito para obtenção de crédito na avaliação do membro da equipe. Se você estiver sugerindo que um indivíduo fez menos de 10% do trabalho, por favor, dê alguma explicação. Se qualquer indivíduo obtiver uma pontuação média de colegas indicando que fez menos de 10% do trabalho, essa pessoa receberá metade da nota do resto do grupo.
