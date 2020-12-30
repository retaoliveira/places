---
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  dados_grad:
    parent: Unidade 2 - Documentos reprodutíveis
    weight: 19
title: Documentos parametrizados
toc: true
type: docs
weight: 19
---

Um dos muitos benefícios de trabalhar com R Markdown é que você pode reproduzir análises com o clique de um botão. Isto torna muito fácil atualizar qualquer trabalho e alterar qualquer parâmetro de entrada dentro do relatório. Relatórios parametrizados estendem esse benefício e permitem aos usuários especificar um ou mais parâmetros para personalizar a análise. Isto é útil se você quiser criar um modelo de relatório que possa ser reutilizado em vários cenários similares. Como exemplos:

- Mostrar resultados para uma localização geográfica específica.

- Executar um relatório que cubra um período de tempo específico.

- Executar uma única análise várias vezes para diferentes suposições.


# Declaração de parâmetros 

Os parâmetros são especificados usando o campo dos parâmetros dentro da seção `YAML`. Podemos especificar um ou mais parâmetros com cada item em uma nova linha. A título de exemplo:

```{r}
---
title: My Document
output: html_document
params:
  year: 2018
  region: Europe
  printcode: TRUE
  data: file.csv
---
```

Todos os tipos de dados do `R` podem ser processados por `yaml::yaml.load()`, podendo ser incluídos como parâmetros, a saber: `character`, `numeric`, `integer` e `logical`. Também podemos usar objetos R incluindo `!r` antes das expressões `R`. Por exemplo, podemos incluir a data atual com o seguinte código R:

```{r}
---
title: My Document
output: html_document
params:
  date: !r Sys.Date()
---
```
Qualquer expressão no `R` incluída dentro dos parâmetros no `yaml` é executada antes de qualquer código no documento, portanto qualquer dependência de pacote deve ser explicitamente declarada usando o `pacote::função` notação (por exemplo, `!r lubridate::today()`), mesmo que o pacote seja carregado mais tarde no documento `Rmd`.

## `Knitting` com parâmetros

Há três maneiras de se fazer um relatório parametrizado:

- Usando o botão `Knit` dentro do RStudio.

- `rmarkdown::render()` com o argumento dos `params`.

- Usando uma interface de usuário interativa para inserir valores de parâmetros.

### O botão `Knit`

Usando o botão `Knit` no RStudio ou a função `rmarkdown::render()`, os valores-padrão listados nos metadados do `YAML` (quando especificados) serão utilizados.

### `Knitting` com parâmetros personalizados

Mesmo que seu documento tenha o campo de parâmetros nos metadados do `YAML`, você pode realmente substituí-lo fornecendo uma lista personalizada de valores de parâmetros para a função `rmarkdown::render()`. Por exemplo:

```{r echo=TRUE, message=FALSE, warning=FALSE}
rmarkdown::render("MyDocument.Rmd", params = list(
  year = 2017,
  region = "Asia",
  printcode = FALSE,
  file = "file2.csv"
))
```

Não temos que declarar explicitamente todos os parâmetros no argumento dos `params`. Qualquer parâmetro não especificado terá como padrão os valores especificados nos metadados do `YAML`. Por exemplo, a função a seguir somente anulará o parâmetro da região:

```{r echo=TRUE, message=FALSE, warning=FALSE}
rmarkdown::render("MyDocument.Rmd", params = list(
  region = "Asia"
))
```
Você pode querer integrar estas mudanças em uma função. Tal função também poderia ser usada para criar um arquivo de saída com um nome de arquivo diferente para cada uma das diferentes combinações de parâmetros. No exemplo a seguir, um novo arquivo Report-region year.pdf é criado para cada conjunto de parâmetros:

```{r echo=TRUE, message=FALSE, warning=FALSE}
render_report = function(region, year) {
  rmarkdown::render(
    "MyDocument.Rmd", params = list(
      region = region,
      year = year
    ),
    output_file = paste0("Report-", region, "-", year, ".pdf")
  )
}
```

### A interface interativa ao usuário

Podemos usar uma interface gráfica de usuário (`GUI`) baseada no `Shiny` para inserir interativamente os parâmetros de um relatório. A interface de usuário pode ser chamada por `rmarkdown::render("MyDocument.Rmd", params = "ask")` ou clicando no menu suspenso atrás do botão `Knit` e escolhendo `Knit with Parameters` no RStudio. A Figura a seguir apresenta a `GUI` do `rmarkdown` solicitando parâmetros de entrada.

Valores dos parâmetros de entrada interativamente para relatórios parametrizados.


![Valores dos parâmetros de entrada interativamente para relatórios parametrizados.](https://retaoliveira.github.io/relements/figures/params-input.png)


Os controles de entrada para diferentes tipos de parâmetros podem ser personalizados, especificando subitens adicionais dentro da especificação do parâmetro em `YAML`. Por exemplo, controles deslizantes, caixas de seleção e caixas de entrada de texto podem ser todos usados para controles de entrada.

Além disso, também podemos especificar as restrições dos valores permitidos em cada parâmetro. Por exemplo, podemos querer que nosso modelo só seja executado durante anos entre 2010 e 2018. Isto é particularmente benéfico se você gostaria que outros usuários interagissem com o relatório, pois impede que os usuários tentem executar relatórios fora dos limites projetados.

Adaptando nosso exemplo acima para incluir algumas configurações:

```{r echo=TRUE, message=FALSE, warning=FALSE}
---
title: My Document
output: html_document
params:
  year:
    label: "Year"
    value: 2017
    input: slider
    min: 2010
    max: 2018
    step: 1
    sep: ""
  region:
    label: "Region:"
    value: Europe
    input: select
    choices: [North America, Europe, Asia, Africa]
  printcode:
    label: "Display Code:"
    value: TRUE
  data:
    label: "Input dataset:"
    value: results.csv
    input: file
---
```
Isto resulta na interface do usuário para os parâmetros.

![Valores dos parâmetros de entrada interativamente para relatórios parametrizados.](https://retaoliveira.github.io/relements/figures/params-controls.png)

Controles personalizados para os parâmetros.
FIGURA 15.2: Controles personalizados para os parâmetros.

O tipo de controle Brilhante utilizado é controlado pelo campo de entrada. A Tabela 15.1 mostra os tipos de entrada atualmente suportados (veja a página de ajuda da função Shiny associada para atributos adicionais que podem ser especificados para personalizar a entrada, por exemplo, ?shiny::checkboxInput).

TABELA 15.1: Possíveis tipos de entrada e as funções Brilhantes associadas para relatórios parametrizados.
Input Type	Shiny Function
checkbox	checkboxInput
numeric	numericInput
slider	sliderInput
date	dateInput
text	textInput
file	fileInput
radio	radioButtons
select	selectInput
password	passwordInput