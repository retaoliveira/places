---
date: "2020-12-27T00:00:00+01:00"
draft: true
menu:
  dados_pos:
    parent: Unidade 5 - Funções para manipulação e tratamento de dados
    weight: 30
title: Manipulação e limpeza de dados
toc: true
type: docs
weight: 30
---

Introdução ao pacote dplyr
Começando pelo meio: data frames
Uma característica distintiva da linguagem de programação R é ter sido desenvolvida para a análise de dados. E quando pensamos em análise de dados, a protagonista do show é a base de dados ou, como vamos conhecer a partir de agora, data frame.

Por esta razão, em vez de aprender como fazer aritmética, elaborar funções ou executar loops para repetir tarefas e outros aspectos básicos da linguagem, vamos começar olhando para o R como um software concorrente dos demais utilizados para análise de dados em ciências sociais, como SPSS, Stata, SAS e companhia.

As principais características de um data frame são: (1) cada coluna representa uma variável (ou característica) de um conjunto de observações; (2) cada linha representa uma observação e contém os valores de cada variável para tal observação. Vejamos um exemplo:

Candidato	Partido	Votos
Beatriz	PMDB	350
Danilo	SOL	1598
Pedro	PTB	784
Davi	PSD	580
Mateus	PV	2
Note que em uma linha os elementos são de tipos de diferentes: na primeira coluna há uma nome (texto), na segunda uma sigla de partido (texto, mas limitado a um conjunto de siglas) e na terceira votos (número inteiros).

Por outro lado, em cada coluna há somente elementos de um tipo. Por exemplo, há apenas números inteiros na coluna votos. Colunas são variáveis e por isso aceitam registros de um único tipo. Se você já fez um curso de estatísticas básica ou de métodos quantitativos deve se lembrar que as variáveis são classificadas da seguinte maneira:

1- Discretas

Nominais, que são categorias (normalmente texto) não ordenadas

Ordinais, que são categorias (normalmente texto) ordenadas

Inteiros, ou seja, o conjunto dos números inteiros

2- Contínuas, números que podem assumir valores não inteiros

Se destacamos uma coluna do nosso data frame, temos um vetor. Por exemplo, a variável "Votos" pode ser presentado da seguinte maneira: {350, 1598, 784, 580, 2}. Um data frame é um conjunto de variáveis (vetores!) dispostos na vertical e combinados um ao lado do outro.

Data frame e vetores são objetos na linguagem R.

Vamos ver como o R representa vetores e data frames na tela. Antes disso, é preciso "abrir" um data frame.

Cadastro de Escolas
Neste tutorial vamos trabalhar com as bases de dados da educação municipal da cidade de São Paulo. Em particular, vamos começar trabalhando com o cadastro de escolas da Prefeitura de São Paulo.

A página na qual você encontrará o cadastro de escolas é essa aqui aqui. Comece baixando o dicionário de dados e os dados mais atuais.

Abrindo dados em R com botão (aaaaaaargh!)
Se você decidiu aprender a programar em R, provavelmente quer substituir a análise de dados com cliques no mouse que fazemos no editor de planilhas pela construção de scripts que documentam o passo a passo da análise. Daqui em diante estaremos num mundo sem botões. Exceto um, por enquanto, aí no canto direito superior chamado "Import Dataset".

Clique no botão (aaaaaaargh!). Veja que temos a opção de importar arquivos de texto com duas bibliotecas diferentes, base e readr (que é o pacote de abertura de dados do tidyverse) e dados em alguns outros formatos, como MS Excel e outros softwares de análise estatística.

Use a primeira opção, "From Text (base)" para carregar os dados do cadastro de escola.

Abrindo dados em R (com script)
(Lembre-se de carregar o pacote tidyverse antes de prosseguir)

library(tidyverse)
Use o recurso "Import Dataset" enquanto não se sentir confortável com a linguagem. Mas, aos poucos, vá abandonando. Abrir dados em R é muito simples.

Repetindo o procedimento, para abrir o cadastro de escola basta fazer:

escolas <- read_csv2("http://dados.prefeitura.sp.gov.br/pt_PT/dataset/8da55b0e-b385-4b54-9296-d0000014ddd5/resource/e0f7d848-1d35-4ce8-b2b3-20e1196c2076/download/escolas122018.csv")
Em R, as funções "read." são as funções de abertura de dados do base e as funções "read_" são as análogas do pacote readr, parte do tidyverse. Há funções "read" para abrir todos os tipos de dados, de arquivos de texto a páginas em HTML.

No nosso caso, utilizamos a função read_csv2 para abrir um arquivo de texto cujos valores das colunas são separados por vírgula. Infelizmente, não há tempo para aprender sobre as variedades das funções de abertura de dados, mas você pode aprender um pouco mais aqui ou aqui.

Note que utilizamos o URL dos dados diretamente. Não precisamos fazer download para uma pasta local para, depois, abrir os dados.

Um jeito mais confortável, na mina opinião, de fazer a abertura de dados com um URL é guardar o URL em um objeto de texto e, depois, utilizar esse objeto como input da função:

url_escolas <- "http://dados.prefeitura.sp.gov.br/pt_PT/dataset/8da55b0e-b385-4b54-9296-d0000014ddd5/resource/e0f7d848-1d35-4ce8-b2b3-20e1196c2076/download/escolas122018.csv"
escolas <- read_csv2(url_escolas)
Note que, pela segunda vez, utilizamos o símbolo "<-". Ele é um símbolo de atribuição, e é um das marcas mais importantes da linguagem. Atribuir, significa "guardar na memória com um nome". O nome, é o que vai do lado esquerdo. A parte do lado direito da equação de atribuição é o objeto a ser guardado.

Você pode usar "=" no lugar de "<-". Mas, avisamos desde já, há casos em que há ambiguidade e os símbolos não funcionam como esperado.

Vamos avançar.

Explorando sem olhar para a matriz de dados
No editor de planilhas estamos acostumados a ver os dados, célula a célula. Mas será que é realmente útil ficar olhando para os dados? Você perceberá com o tempo que olhar os dados é desnecessário e até contraproducente.

Você pode ver os dados clicando (aaaaaaargh!) no nome do objeto que está no "Environment" ou utilizando a função View (cuidado, o "V" é maiúsculo, algo raro em nomes de funções de R).

View(escolas)
Agora que carregamos o cadastro de escolas na memória, vamos conhecer um pouco sobre estes dados sem olhar para a matriz de dados.

Podemos rapidamente olhar para uma "amostra" dos dados com a função head, que nos apresenta as 6 primeiras linhas do conjunto de dados.

head(escolas)
Com apenas as 6 primeiras linhas do data frame temos noção de todo o conjunto. Sabemos rapidamente que existem informações sobre o nome das escolas, seus códigos de cadastro, de que tipo de escola se trata, à qual diretoria regional de ensino (DRE) pertence, etc.

Quantas escolas há? Há tantas escolas quantas linhas nos dados. Com nrow descobrimos quantas são.

nrow(escolas)
Quantas informações temos disponíveis para cada escola? Ou seja, quantas variáveis há no conjunto de dados?

ncol(escolas)
Qual é o nome das variáveis?

names(escolas)
Pausa para um comentário
Podemos fazer comentários no meio do código. Basta usar # e tudo que seguir até o final da linha não será interpertado pelo R como código. Por exemplo:

# Imprime o nome das variaveis do data frame cadastro
names(escolas)

names(escolas) # Repetindo o comando acima com comentario em outro lugar
Comentários são extremamente úteis para documentar seu código. Documentar é parte de programar e você deve pensar nas pessoas com as quais vai compartilhar o código e no fato de que com certeza não se lembrará do que fez em pouco tempo (garanto, você vai esquecer).

Argumentos ou parâmetros das funções
Note que em todas as funções que utilizamos até agora, escolas está dentro do parênteses que segue o nome da função. Essa sintaxe é característica das funções de R. O que vai entre parêntesis são os argumentos ou parâmetros da função, ou seja, os "inputs" que serão transformados.

Uma função pode receber mais de um argumento. Pode também haver argumentos não obrigatórios, ou seja, para os quais não é necessário informar nada se você não quiser alterar os valores pré-definidos. Por exemplo, a função head contém o argumento n, que se refere ao número de linhas a serem impressas na tela, pré-estabelecido em 6 (você pode conhecer os argumentos da função na documentação do R usando ? antes do nome da função). Para alterar o parâmetro n para 10, por exemplo, basta fazer:

head(x = escolas, n = 10)
x é o argumento que já havíamos utilizado anteriormente e indica em que objeto a função head será aplicada. Dica: você pode omitir tanto "x =" quanto "n =" se você já conhecer a ordem de cada argumento no uso da função.

Mais funções para explorar os dados
Todos os objetos em R tem uma estrutura. Você pode investigar essa estrutura utilizando a função str. No caso de data frames, o output é legível (para outras classes de objeto isso não é verdade necessariamente):

str(escolas)
Há informações sobre o nome das variáveis, dispostas na vertical, tipo de dados (texto -- char -- ou números -- num ou int) e uma amostra das primeiras observações.

Uma função semelhante, e com resultado um pouco mais "limpo", é glimpse, parte do dplyr:

glimpse(escolas)
Vamos agora renomear os dados.

Renomeando variáveis
Quando trabalhamos com dados que não coletamos, em geral, não vamos gostar dos nomes das variáveis que quem produziu os dados escolheu. Mais ainda, com certa frequência, obtemos dados cujos nomes das colunas são compostos ou contêm acentuação, cecedilha e demais caracteres especiais. Dá um tremendo trabalho usar nomes com tais característica, apesar de possível. O ideal é termos nomes sem espaço (você pode usar ponto ou subscrito para separar palavras em um nome composto) e que contenham preferencialmente letras minísculas sem acento e números.

Vamos começar renomeando algumas variáveis no nosso banco de dados, cujos nomes vemos com o comando abaixo:

names(escolas)
O primeiro argumento da função rename deve ser a base de dados cujos nomes das variáveis serão renomeados. Depois da primeira vírgula, inserimos todos as modificações de nomes, novamente separadas por vírgulas, e da seguinte maneira. Exemplo: nome_novo = nome_velho. Exemplo: nome_novo = Nome_Velho. Veja o exemplo, em que damos novos nomes às variáveis "tipoesc", "latitute" e "longitude":

escolas <- rename(escolas, tipo = tipoesc, lat = latitude, lon = longitude)
Simples, não?

Uma gramática, duas formas
No tidyverse, existe uma outra sintaxe para executar a mesma tarefa de (re)nomeação. Vamos olhar para ela (lembre-se de carregar novamente os dados, pois os nomes velhos já não existem mais e não existe Ctrl+Z em R):

escolas <- read_csv2(url_escolas)

escolas <- escolas %>%
  rename(tipo = tipoesc,
         lat = latitude,
         lon = longitude)
Usando o operador %>%, denominado pipe, retiramos de dentro da função rename o banco de dados cujas variáveis serão renomeadas. As quebras de linha depois do %>% e dentro da função rename são opcionais. Porém, o pardão é 'verticalizar o código' e colcar os 'verbos' à esquerda, o que torna sua leitura mais confortável.

Compare com o código que havíamos executado anteriormente:

escolas <- read_csv2(url_escolas)

escolas <- rename(escolas, tipo = tipoesc, lat = latitude, lon = longitude)
Essa outra sintaxe tem uma vantagem grande sobre a anterior: ela permite emendar uma operação de transformação do banco de dados na outra. Veremos adiante como fazer isso. Por enquanto, tenha em mente que o resultado é o mesmo para qualquer uma das duas formas.

Vamos trabalhar com várias variáveis (sic) de uma única vez. Reabra o banco de dados:

escolas <- read_csv2(url_escolas)
Renomeie as variáveis "dre", "codesc", "tipoesc", "nomesc", "diretoria", "latitude", "longitude" e "codinep".

escolas <- escolas %>%
  rename(dre_abreviatura = dre,
         codigo = codesc,
         tipo = tipoesc,
         nome = nomesc,
         dre = diretoria,
         lat = latitude,
         lon = longitude,
         codigo_inep = codinep)
Selecionando colunas
Algumas colunas podem ser dispensáveis em nosso banco de dados a depender da análise. Por exemplo, pode ser que nos interessem apenas as variáveis que já renomeamos. Para selecionar um conjunto de variáveis, utilizaremos o segundo verbo do dplyr que aprenderemos: select

escolas <- select(escolas, dre_abreviatura, codigo, tipo, nome, dre, lat, lon, codigo_inep)
ou usando o operador %>%, chamado pipe,

escolas <- escolas %>%
  select(dre_abreviatura,
         codigo,
         tipo,
         nome,
         dre,
         lat,
         lon,
         codigo_inep)
Operador %>% para "emendar" tarefas
O que o operador pipe faz é simplesmente colocar o primeiro argumento da função (no caso acima, o data frame), fora e antes da própria função. Ele permite lermos o código, informalmente, da seguinte maneira: "pegue o data frame x e aplique a ele esta função". Veremos abaixo que podemos fazer uma cadeia de operações ("pipeline"), que pode ser lida informalmente como: "pegue o data frame x e aplique a ele esta função, e depois essa, e depois essa outra, etc".

A grande vantagem de trabalharmos com o operador %>% é não precisar repetir o nome do data frame diversas vezes ao aplicarmos a ele um conjunto de operações.

Vejamos agora como usamos o operador %>% para "emendar" tarefas, começando da abertura desde dados. Note que o primeiro input é o url da base de dados e, que, uma vez carregados, vai sendo transformado a cada novo verbo.

escolas <- read_csv2(url_escolas) %>%
  rename(dre_abreviatura = dre,
         codigo = codesc,
         tipo = tipoesc,
         nome = nomesc,
         dre = diretoria,
         lat = latitude,
         lon = longitude,
         codigo_inep = codinep)  %>%
  select(dre_abreviatura,
         codigo,
         tipo,
         nome,
         dre,
         lat,
         lon,
         codigo_inep)
Em uma única sequência de operações, abrimos os dados, alteramos os nomes das variáveis e selecionamos as que permaneceriam no banco de dados. Esta forma de programa, tenha certeza, é bastante mais econômica e mais fácil de ler, para que possamos identificar erros mais facilmente.

Transformando variáveis
Usaremos a função mutate para operar transformações nas variáveis existentes e criar variáveis novas. Há inúmeras transformações possíveis e elas lembram bastante as funções de outros softwares, como MS Excel. Vamos ver algumas das mais importantes.

No nosso caso, o formato dos valores de latitude e longitude estão em formato diferente do convenional. Latitudes são representadas por números entre -90 e 90, com 8 casas decimais, e Longitudes por números entre -180 e 180, também com 8 casas decimais. Em nosso par de variáveis, latitude está sem separador de decimal está omitido. Faremos a correção divindo latitude por 1 milhão.

No caso de longitude, a situação é ainda pior. Há vários separadores e a variável foi lida como texto. Teremos que limpar todos os separadores, transformar a variável em número e, ao final, dividir por 1 milhão para colocar o separador no lugar certo.

escolas <- escolas %>% 
  mutate(lat = lat / 1000000, 
         lon = str_replace_all(lon, "\\.", ""),
         lon = as.numeric(lon),
         lon = lon / 1000000) 
Como utilizamos os nomes das próprias variáveis à esquerda da operação de transformação, produziremos uma substituição e não haverá novas colunas na base de dados.

Voltaremos ao verbo mutate no próximo tutorial e no exemplos abaixo.

Filtrando linhas
Por vezes, queremos trabalhar apenas com um conjunto de linhas do nosso banco de dados. Por exemplo, se quisermos selecionar apenas escolas municipais de educação infantil, utilizamos o verbo 'filter' com a condição desejada. Note que estamos criando um novo data frame (ou seja, um novo objeto) que contém a seleção de linhas produzida:

emeis <- escolas %>% 
  filter(tipo == "EMEI")
Além da igualdade, poderíamos usar outros símbolos: maior (>). maior ou igual (>=), menor (<), menor ou igual (<=) e diferente (!=) para selecionar casos. Para casos de NA, podemos usar a função is.na(), pois a igualdade '== NA' é inválida em R.

Vamos supor agora que todos centros de educação infantil (creche) da rede direta, indireta e conveniada. Como combinar condições?

creches <- escolas %>% 
  filter(tipo == "CEI DIRET" | tipo == "CEI INDIR" | tipo == "CR.P.CONV")
Note que, para dizer que para combinarmos as condições de seleção de linha, utilizamos uma barra vertical. A barra é o símbolo "ou", e indica que todas as observações que atenderem a uma ou outra condição serão incluídas.

Vamos supor que queremos estabelecer agora condições para a seleção de linhas a partir de duas variáveis. Por exemplo, queremos incluir as mesmas escolas já escolhidas e que também sejam da Diretoria Regional do Ipiranga. O símbolo da conjunção "e" é "&". Veja como utilizá-lo:

creches <- escolas %>% 
  filter(tipo == "CEI DIRET" | 
            tipo == "CEI INDIR" | 
            tipo == "CR.P.CONV")

Ao usar duas variáveis diferentes para filter e a conjunção "e", podemos escrever o comando separando as condições por vírgula e dispensar o operador "&":

creches_ipiranga <- escolas %>% 
  filter((tipo == "CEI DIRET" | 
            tipo == "CEI INDIR" | 
            tipo == "CR.P.CONV"),
           dre == "DIRETORIA REGIONAL DE EDUCACAO IPIRANGA")
Você pode combinar quantas condições precisar. Se houver ambiguidade quanto à ordem das condições, use parênteses, como fizemos acima.

Vamos uma aplicação interessante dos dados com os quais trabalhamos.

Produzindo mapas no R
Criamos acima um data frame que contém apenas centros de educação infantil com a informação de latitude e longitude já corrigida. Conseguimos "reduzir" e alterar os dados usando quatro "verbos" (funções) fundamentais de manipulação de dados: rename, select, mutate e filter.

Precisaremos do pacote ggmap e osmdata para "importar" mapas de rua de serviços da web (Google e Open Street Maps, por exemplo) para, depois, fazer a combinação dos mapas com os pontos (escolas, a partir da latitude e longitude).

# install.packages('osmdata')
# install.packages('ggmap')
library(ggmap)
library(osmdata)
Sem entrar em detalhes, vamos utilizar as funções get_map e getbb para obter um mapa sobre o qual inseriremos nossos pontos.

map_sp <- get_map(getbb("Sao Paulo"), 
                  maptype = "toner-background",
                  zoom = 13)
Podemos plotar o mapa que baixamos com a função plot:

plot(map_sp)
Mas ainda não é isso que queremos. Precisamos sobrepor ao mapa que baixamos os pontos correspondentes a cada uma dos CEIS. Veja como:

ggmap(map_sp) +
  geom_point(aes(lon, lat), data = creches)
Legal, não? Não muito bonito, mas estamos no caminho.

O código acima tem uma estrutura bastante diferente do que havíamos visto. Ele é parte de outra "gramática" do R, a "grammar o graphics" do pacote ggplot2. Veremos um pouco sobre ela em outro tutorial, mas vamos tentar destrinchar o código do mapa acima desde já.

Começamos plotando o mapa de São Paulo obtido nas APIs do Open Street Maps e Google com a função ggmap. Criamos, assim, a primeira camada do mapa e "organizará" o sistema de coordenadas. Com geom_point, adicionaremos pontos ao mapa. Os pontos vem do data frame "creches" -- por isso "data = creches" -- e a informação utilizada, "lat" e "lon", faz parte da "aesthetics" do mapa -- por isso dentro do parênteses "aes".

Se você quiser aprender um pouco mais sobre mapas no R (e fazer mapas mais bonitos) aqui.

Fim
Espero que com este tutorial você tenha se familiarizado com a linguagem R e compreendido como utilizá-la trabalhar com os dados abertos da educação municipal. Organizando o que fizemos em um único "bloco" de cógido, vemos que é preciso pouco código para fazer algo relevante:

library(tidyverse)
library(ggmap)
library(osmdata)

creches <- read_csv2(url_escolas) %>%
  rename(dre_abreviatura = dre,
         codigo = codesc,
         tipo = tipoesc,
         nome = nomesc,
         dre = diretoria,
         lat = latitude,
         lon = longitude,
         codigo_inep = codinep)  %>%
  select(dre_abreviatura,
         codigo,
         tipo,
         nome,
         dre,
         lat,
         lon,
         codigo_inep) %>% 
  mutate(lat = lat / 1000000, 
         lon = str_replace_all(lon, "\\.", ""),
         lon = as.numeric(lon),
         lon = lon / 1000000) %>% 
  filter(tipo == "CEI DIRET" | 
           tipo == "CEI INDIR" | 
           tipo == "CR.P.CONV")

map_sp <- get_map(getbb("Sao Paulo"), 
                  maptype = "toner-background",
                  zoom = 13)

ggmap(map_sp) +
  geom_point(aes(lon, lat), data = creches)


# Group by, Summarise, Arrange e Slice

## Novos verbos e dados de survey

No tutorial passado vimos 4 dos principais verbos do _dplyr_: _rename_, _select_, _mutate_ (para operações de colunas) e _filter_ (para seleção de casos). Não produzimos, entretanto, uma das operações mais importantes na manipulação de _data\_frames_: o agrupamento de casos a partir de uma ou mais variáveis. O agrupamento de casos em uma base de dados convencional é bastante simples, como veremos a seguir. 

## Fake data

Para esta atividade, vamos trabalhar com um banco de dados falso criado para a atividade.

Abra o banco de dados usando _read\_delim_:

```{r}
library(tidyverse)
url_fake_data <- "https://raw.githubusercontent.com/leobarone/ifch_intro_r/master/data/fake_data.csv"
fake <- read_delim(url_fake_data, delim = ";", col_names = T)
```
Fakeland é uma democracia muito estável que realiza eleições presidenciais a cada 4 anos. Vamos trabalhar com o conjunto de dados falso de cidadãos individuais de Fakeland que contém informações sobre suas características básicas e opiniões / posições políticas (falsas). A descrição das variáveis está abaixo:

- _age_: idade
- _sex_: sexo
- _educ_: nível educacional
- _income_: renda mensal medida em dinheiro falso (FM \ $)
- _savings_: Dinheiro falso total (FM \ $) na conta de poupança
- _marriage_: estado civil (sim = casado)
- _kids_: número de filhos
- _party_: afiliação partidária
- _turnout_: intenção de votar nas próximas eleições
- _vote\_history_: número de eleições presidenciais votou desde as eleições de 2002
- _economy_: opinião sobre o desempenho da economia nacional
- _incumbent_: opinião sobre o desempenho do presidente
- _candidate_: candidato preferido

## Agrupando com _filter_ e _pull_

Vamos supor que nos interessa comparar a renda entre grupos de sexo. Poderíamos, rapidamente selecionar as linhas de um dos grupos de sexo com o verbo _filter_:

```{r}
fake %>%
  filter(sex == "Male") 
```

```{r}
fake %>%
  filter(sex == "Female") 
```

Com o comando _pull_, podemos 'retirar' de um data frame uma coluna e tratá-la como um vetor destacado. _pull_ é mais um (de vários) verbos do _dplyr_:

```{r}
fake %>%
  filter(sex == "Male") %>%
  pull(income)
```

E, se adicionarmos à 'pipeline' um comando simples de estatística descritiva -- média, por exemplo -- calculamos uma estatística para o grupo para o qual selecionamos com _filter_:

```{r}
fake %>%
  filter(sex == "Male") %>%
  pull(income) %>%
  mean()
```

Note que não utilizamos o símbolo de atribuição '<-' e, portanto, não armazenamos o resultado em nenhum objeto.

Note também que podemos adicionar à pipeline qualquer função que não seja 'verbo' do _dplyr_, como comando _mean_.

Essa estratégia funciona para calcular uma medida qualquer para um grupo. Mas, em geral, interessa 'sumarizar' um variável -- como renda -- por uma variável de grupo -- como sexo -- sem destacar cada uma das categorias. Vamos ver como fazer isso.

## _summarise_

Uma maneira altenartiva ao que acabamos de realizar é utilizar o verbo _summarise_. Com ele, não precisamos extrair a variável do data frame para gerar um sumário estatístico. Veja como é simples:

```{r}
fake %>%
  filter(sex == "Male") %>%
  summarise(media_homens = mean(income))
```

```{r}
fake %>%
  filter(sex == "Female") %>%
  summarise(media_mulheres = mean(income))
```

## Agrupando com _group\_by_ by e _summarise_

Para agrupar os dados por uma ou mais variáveis na 'gramática' do _dplyr_ utilizamos o verbo _group\_by_ em combinação com _summarise_. Veja um exemplo antes de detalharmos seu uso:

```{r}
fake %>%
  group_by(sex) %>%
  summarise(media_renda = mean(income))
```

Veja que o resultado é uma tabela de duas linhas que contém a média de renda para grupo de sexo. O primeiro passo é justamente indicar qual é a variável -- discreta -- pela qual queremos agrupar os dados. Fazemos isso com _group\_by_

Na sequência, utilizamos _summarise_ para criar uma lista das operações que faremos em outras variáveis ao agrupar os dados. Por exemplo, estamos calculando a média da renda, que aparecerá com o nome 'media\_renda', para cada um dos grupos de sexo.

Execute novamente o código acima e observe atentamente sua estrutura antes de avançar.

O verbo _summarise_ permite mais de uma operação por agrupamento. Por exemplo, podemos calcular o desvio padrao da renda, a media da idade ('age') e a soma do número de eleições nas quais votou ('vote\_history'):

```{r}
fake %>%
  group_by(sex) %>%
  summarise(media_renda = mean(income),
            stdev_renda = sd(income),
            media_idade = mean(age),
            soma_eleicoes = sum(vote_history))
```

Simples, não? O comando _summarise_ é bastante flexível e aceita diversas operações. Veremos as mais comuns adiante.

E se quisermos, agora, utilizar mais de uma variável para agrupar os dados? Por exemplo, e se quisermos agrupar por sexo e candidato de preferência, como fazemos?

Basta adicionar outra variável dentro do comando _group\_by_:

```{r}
fake %>%
  group_by(sex, candidate) %>%
  summarise(media_renda = mean(income))
```

Observe bem a estrutura dos resultados que obtivemos. Em primeiro lugar, o resultado é sempre um data frame. Sempre que estivermos preparando os dados para gerar tabelas ou com gráficos, como veremos no tutorial seguinte, produziremos um data frame para servir de 'input' para o gráfico ou tabela.

Em segundo, cada variável utilizada para agrupamento aparece como uma coluna diferente no novo data frame. Os dados estão 'colapsados' ou 'achatados' em um número de linhas que corresponde ao total de combinações de categorias das variáveis de agrupamento (por exemplo, "Female e Rilari", "Female e Trampi", etc).

Se pararmos para pensar, o data frame resultante do último comando tem exatamente o número de células de uma tabela de duas entradas ('crosstab'), mas as informações das margens da tabela estão como variáveis. Veremos como modificar isso adiante.

Finalmente, cada nova variável gerada com _summarise_ em nosso data frame 'achatado' recebe uma coluna. Para 'sumarizar' uma variável -- tirar média, somatória, contar, etc -- precisamos sempre de uma função de sumário.

## Funções de sumário estatístico

Vamos ver exemplos das funções de sumário estatístico mais utilizadas dentro do verbo _summarise_.

1- Média

```{r}
fake %>%
  group_by(sex) %>%
  summarise(media = mean(income))
```

2- Desvio padrão

```{r}
fake %>%
  group_by(sex) %>%
  summarise(desvpad = sd(income))
```


3- Mediana

```{r}
fake %>%
  group_by(sex) %>%
  summarise(mediana = median(income))
```

4- Quantis (no exemplo, quantis 10\%, 25\%, 75\%, 90\%)

```{r}
fake %>%
  group_by(sex) %>%
  summarise(quantil_10 = quantile(income, probs = 0.1),
            quantil_25 = quantile(income, probs = 0.25),
            quantil_75 = quantile(income, probs = 0.75),
            quantil_90 = quantile(income, probs = 0.9))
```

5- Mínimo e máximo

```{r}
fake %>%
  group_by(sex) %>%
  summarise(minimo = min(income),
            maximo = max(income))
```

6- Contagem e soma

```{r}
fake %>%
  group_by(sex) %>%
  summarise(contagem = n(),
            soma = sum(age))
```

Importante: quando houver algum "NA" (missing value) em uma variável numérica, é preciso utilizar o argumento "na.rm = TRUE" dentro da função de sumário. Veja como ficaria o código caso houvesse algum "NA":

```{r}
fake %>%
  group_by(sex) %>%
  summarise(media = mean(income, na.rm = TRUE))
```

A sessão Useful [Summary Functions](https://r4ds.had.co.nz/transform.html#summarise-funs) do livro R for Data Science traz uma relação mais completa de funçoes que podem ser usandas com summarise. O [“cheatsheet” da RStudio](https://github.com/rstudio/cheatsheets/raw/master/data-transformation.pdf) oferece uma lista para uso rápido.

## Transformando um agrupamento em um "crosstab" e exportando

Vamos retomar o exemplo do agrupamento por duas variáveis, sexo e candidato de preferência:

```{r}
fake %>%
  group_by(sex, candidate) %>%
  summarise(media_renda = mean(income))
```

Esse formato não costuma ser o usual em apresentação de dados. O mais comum é termos a informação que consta em nossas duas primeiras colunas como margens em uma tabela de duas entradas.

Na linguagem de manipulação de dados, o resultado acima está no formato "long" e todas as variáveis são representadas como colunas. Uma tabela de 2 entradas corresponde ao formato "wide".

Há dois verbos no _dplyr_ que transformam "long" em "wide" e vice-versa: _spread_ e _gather_. Como _spread_, tranformamos o nosso resultado acima na tabela desejada:

```{r}
fake %>%
  group_by(sex, candidate) %>%
  summarise(media_renda = mean(income)) %>%
  spread(sex, media_renda)
```

_spread_ precisa de 2 argumentos: a "key", que a variável que irá para a margem superior da tabela, e "value", que é a variável que ficará em seu conteúdo.

É fácil, inclusive, exportá-la para um editor de planilhas com a função _write\_csv_ (do pacote _readr_) ao final do pipeline:

```{r}
fake %>%
  group_by(sex, candidate) %>%
  summarise(media_renda = mean(income)) %>%
  spread(sex, media_renda) %>%
  write_csv("tabela_candidato_sexo_renda.csv")
```

Vá à sua pasta de trabalho e verifique que sua tabela está lá.

Veja que, como introduzimos um comando de exportação ao final do pipelina, não geramos nenhum objeto. Não há símbolo de atribuição em nosso código. Esse é um dos objetivo do uso do pipe (%>%): reduzir o número de objetos intermediários gerados.

### Spread e Gather caindo em desuso

Há notícias de que os verbos _spread_ e _gather_ cairão em desuso. Seus substituos serão _pivot\_wider_ e _pivot\_longer_. As 4 funções são parte do pacote _tidyr_, componente do _tidyverse_. O uso das novas funções é bem similar ao das antigas, e veja como fica a substituição de _spread_ por _pivot\_wider_ no código que produzimos. É possível que sua instalação do _tidyverse_ não contenha as novas funções e que o código abaixo não funcione.

```{r}
fake %>%
  group_by(sex, candidate) %>%
  summarise(media_renda = mean(income)) %>%
  pivot_wider(names_from = sex,
              values_from = media_renda)
```

## Mutate com Group By

Vamos supor que queremos manter os dados no mesmo formato, ou seja, sem 'achatá-los' por uma variável discreta, mas queremos uma nova coluna que represente a soma de uma variável por grupo -- para calcular percentuais de renda dentro de cada grupo de sexo, por exemplo. Vamos observar o resultado do uso conjunto de _group\_by_ e _mutate_. Para podermos observar o resultado, vamos armazenar os novos dados em um objeto chamado 'fake2' e utilizar o comando _View_. A última coluna de nossos dados agora é a soma da renda dentro de cada grupo.

```{r}
fake2 <- fake %>% 
  group_by(sex) %>%
  mutate(renda_grupo = mean(income))

View(fake2)
```

Quando utilizarmos _group\_by_ sem o _summarise_, é importante "desagrupar" os data frame, ou "desligar o agrupamento". Caso contrário, o agrupamento continuará ativo e afetando todas as operações seguintes. Repetindo o código com o desagrupamento:

```{r}
fake2 <- fake %>% 
  group_by(sex) %>%
  mutate(renda_grupo = mean(income)) %>%
  ungroup()
```

## Mais verbos do _dplyr_: _arrange_ e _slice_

Se quisermos ordenar, de forma crescente, nossos dados por idade, por exemplo, basta usar o comando _arrange_:

```{r}
fake %>% 
  arrange(age)
```

Em ordem decrescente teríamos:

```{r}
fake %>% 
  arrange(-age)
```

Se quisermos 'desempatar' o ordenamento por idade por uma segunda variável, basta adicioná-la ao _arrange_:

```{r}
fake %>% 
  arrange(-age, vote_history)
```

Quando trabalhamos com bases de dados de survey faz pouco sentido ordená-las. Entretanto, quando trabalhamos numa escala menor, com poucas linhas, ou com a produção de tabelas, como nos exemplos acima, convém ordenar a tabela (veja que, neste ponto, faz pouco sentido diferenciar tabela de data frame, pois se tornam sinônimos) por alguma variável de interesse.

Por exemplo, podemos ordenar os grupos de candidato de preferência por média de renda:

```{r}
fake %>% 
  group_by(candidate) %>% 
  summarise(media_renda = mean(income)) %>% 
  arrange(media_renda)
```

Fácil e útil.

Finalmente, vamos supor que queremos extrair da base de dados apenas os 10 indivíduos de menor idade Como "recortar" linhas dos dados pela posição das linhas?

Em primeiro lugar, vamos ordenar os dados por idade. A seguir, vamos aplicar o verbo _slice_ para recortar as 10 primeiras linhas:

```{r}
fake %>% 
  arrange(age) %>% 
  slice(1:10)
```

Se quisessemos recortar do 25, por exemplo, ao último, sem precisar especificar qual é o número da última posição, utilizamos _n()_:

```{r}
fake %>% 
  arrange(age) %>% 
  slice(25:n())
```

Note que a aplicação de _slice_ não afeta em nada as colunas.
