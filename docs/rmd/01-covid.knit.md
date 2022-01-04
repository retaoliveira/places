---
title: "Mortes por COVID-19"
author: "Adaptado de Mine Çetinkaya-Rundel"
date: "2021-06-11"
output: 
  html_document: 
    toc: yes
    toc_float: yes
---

## Introdução

Países em todo o mundo estão respondendo a um surto de doença respiratória causada por um novo coronavírus, o COVID-19. O surto começou em Wuhan, China, mas foram identificados casos em um número crescente de outros locais internacionalmente, incluindo os Estados Unidos. Neste relatório, exploramos como a trajetória das mortes cumulativas em vários países.

Os dados vêm do pacote `coronavírus`, que coleta dados do repositório de Coronavírus do Centro de Ciência e Engenharia de Sistemas da Universidade Johns Hopkins. O pacote coronavírus fornece um conjunto de dados, em formato organizado, da epidemia de Coronavírus COVID-19 (2019-nCoV) de 2019. O pacote está disponível no GitHub [aqui](https://github.com/RamiKrispin/coronavirus) e é atualizado diariamente.

Para nossa análise, além do pacote de `coronavírus`, utilizaremos os seguintes pacotes para a discussão e visualização de dados.

- `tidyverse` para a discussão e visualização de dados
- `lubridate` pacote para manuseio de datas
- `glue` pacote para a construção de cadeias de texto
- `scales` pacote para formatação de eixos dos gráficos
- `ggrepel` pacote para rótulo dos países nos gráficos

Faremos uso do pacote `DT` para a exibição interativa da saída tabular no Anexo.


```r
library(coronavirus) # devtools::install_github("RamiKrispin/coronavirus")
library(tidyverse)
library(lubridate)
library(glue)
library(scales)
library(ggrepel)
library(DT)
```

## Preparação de dados

A tabela de dados chamado `coronavirus` no pacote coronavirus fornece um resumo diário dos casos de Coronavirus (COVID-19) por país. Cada linha no quadro de dados representa um país (ou, quando relevante, um estado/província). Uma lista completa dos países no quadro de dados é fornecida no [Apêndice]. Observe que os dados fornecidos neste pacote fornecem o número diário de mortes, casos confirmados e casos recuperados. Para este relatório, vamos nos concentrar nas mortes. 

Começaremos por fazer nossa seleção para os países que queremos explorar.


```r
countries <- c(
  "China",
  "France",
  "United Kingdom",
  "US",
  "Turkey", 
  "Brazil", 
  "Italy"
)
```

No seguinte trecho de código filtramos o quadro de dados para mortes nos países que especificamos acima e calculamos o número cumulativo de mortes. Somente visualizaremos os dados desde a 10ª morte confirmada. 


```r
country_data <- coronavirus %>%
  # filter for deaths in countries of interest
  filter(
    type == "death",
    country %in% countries
  ) %>%
  # fix county labels for pretty plotting
  mutate(
    country = case_when(
      country == "United Kingdom" ~ "UK",
      TRUE ~ country
    )
  ) %>%
  # calculate number of total cases for each country and date
  group_by(country, date) %>%
  summarise(tot_cases = sum(cases)) %>%
  # arrange by date in ascending order
  arrange(date) %>%
  # record daily cumulative cases as cumulative_cases
  mutate(cumulative_cases = cumsum(tot_cases)) %>%
  # only use days since the 10th confirmed death
  filter(cumulative_cases > 9) %>%
  # record days elapsed, end date, and end label
  mutate(
    days_elapsed = as.numeric(date - min(date)),
    end_date     = if_else(date == max(date), TRUE, FALSE),
    end_label    = if_else(end_date, country, NULL)
  ) %>%
  # ungroup
  ungroup()
```

```
## `summarise()` has grouped output by 'country'. You can override using the `.groups` argument.
```

Também precisamos tomar nota da "data" dos dados para que possamos rotular adequadamente nossa visualização.


```r
as_of_date <- country_data %>% 
  summarise(max(date)) %>% 
  pull()

as_of_date_formatted <- glue("{wday(as_of_date, label = TRUE)}, {month(as_of_date, label = TRUE)} {day(as_of_date)}, {year(as_of_date)}")
```

Estes dados são formatados conforme qui, mai 27, 2021.

## Visualização

A visualização a seguir mostra o número de casos acumulados versus dias decorridos desde a 10ª morte confirmada em cada país. O período de tempo previsto para cada país varia desde que alguns países começaram a ver (e relatar) mortes da COVID-19 muito mais tarde que outros.


```r
ggplot(data = country_data,
       mapping = aes(x = days_elapsed, 
                     y = cumulative_cases, 
                     color = country, 
                     label = end_label)) +
  # represent cumulative cases with lines
  geom_line(size = 0.7, alpha = 0.8) +
  # add points to line endings
  geom_point(data = country_data %>% filter(end_date)) +
  # add country labels, nudged above the lines
  geom_label_repel(nudge_y = 1, direction = "y", hjust = 1) + 
  # turn off legend
  guides(color = FALSE) +
  # use pretty colors
  scale_color_viridis_d() +
  # better formatting for y-axis
  scale_y_continuous(labels = label_comma()) +
  # use minimal theme
  theme_minimal() +
  # customize labels
  labs(
    x = "Dias desde a confirmação da 10a morte",
    y = "Quantidade de mortes acumuladas",
    title = "Mortes por COVID-19, países selecionados",
    subtitle = glue("Data inicial", as_of_date_formatted, .sep = " "),
    caption = "Source: github.com/RamiKrispin/coronavirus"
  )
```

<img src="01-covid_files/figure-html/visualise-1.png" width="672" />

## Apêndice

Uma lista de países no quadro de dados do `coronavírus` é fornecida abaixo.


```{=html}
<div id="htmlwidget-567fad55b4638500b678" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-567fad55b4638500b678">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104","105","106","107","108","109","110","111","112","113","114","115","116","117","118","119","120","121","122","123","124","125","126","127","128","129","130","131","132","133","134","135","136","137","138","139","140","141","142","143","144","145","146","147","148","149","150","151","152","153","154","155","156","157","158","159","160","161","162","163","164","165","166","167","168","169","170","171","172","173","174","175","176","177","178","179","180","181","182","183","184","185","186","187","188","189","190","191","192","193"],["Afghanistan","Albania","Algeria","Andorra","Angola","Antigua and Barbuda","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahamas","Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bhutan","Bolivia","Bosnia and Herzegovina","Botswana","Brazil","Brunei","Bulgaria","Burkina Faso","Burma","Burundi","Cabo Verde","Cambodia","Cameroon","Canada","Central African Republic","Chad","Chile","China","Colombia","Comoros","Congo (Brazzaville)","Congo (Kinshasa)","Costa Rica","Cote d'Ivoire","Croatia","Cuba","Cyprus","Czechia","Denmark","Diamond Princess","Djibouti","Dominica","Dominican Republic","Ecuador","Egypt","El Salvador","Equatorial Guinea","Eritrea","Estonia","Eswatini","Ethiopia","Fiji","Finland","France","Gabon","Gambia","Georgia","Germany","Ghana","Greece","Grenada","Guatemala","Guinea","Guinea-Bissau","Guyana","Haiti","Holy See","Honduras","Hungary","Iceland","India","Indonesia","Iran","Iraq","Ireland","Israel","Italy","Jamaica","Japan","Jordan","Kazakhstan","Kenya","Kiribati","Korea, South","Kosovo","Kuwait","Kyrgyzstan","Laos","Latvia","Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Marshall Islands","Mauritania","Mauritius","Mexico","Micronesia","Moldova","Monaco","Mongolia","Montenegro","Morocco","Mozambique","MS Zaandam","Namibia","Nepal","Netherlands","New Zealand","Nicaragua","Niger","Nigeria","North Macedonia","Norway","Oman","Pakistan","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Poland","Portugal","Qatar","Romania","Russia","Rwanda","Saint Kitts and Nevis","Saint Lucia","Saint Vincent and the Grenadines","Samoa","San Marino","Sao Tome and Principe","Saudi Arabia","Senegal","Serbia","Seychelles","Sierra Leone","Singapore","Slovakia","Slovenia","Solomon Islands","Somalia","South Africa","South Sudan","Spain","Sri Lanka","Sudan","Suriname","Sweden","Switzerland","Syria","Taiwan*","Tajikistan","Tanzania","Thailand","Timor-Leste","Togo","Trinidad and Tobago","Tunisia","Turkey","Uganda","Ukraine","United Arab Emirates","United Kingdom","Uruguay","US","Uzbekistan","Vanuatu","Venezuela","Vietnam","West Bank and Gaza","Yemen","Zambia","Zimbabwe"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>country<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"order":[],"autoWidth":false,"orderClasses":false,"columnDefs":[{"orderable":false,"targets":0}]}},"evals":[],"jsHooks":[]}</script>
```

---

_Créditos_

Este tutorial é parte do maravilhoso trabalho de Mine Çetinkaya-Rundel: [Data Science Box](https://datasciencebox.org/) 
