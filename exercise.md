---
title: "Exercise"
author: "Jiaxin Shen"
format: html
execute: 
  keep-md: true
---


::: {.cell}

```{.r .cell-code}
here::i_am("r-101-grade-analysis.Rproj")
library(here)
library(vroom) ## or readr
library(dplyr)
library(tidyr)
library(ggplot2)
```
:::


## Exercise 1


::: {.cell}

```{.r .cell-code}
grades <- vroom(here("grades.csv"))
```
:::


##Exercise2


::: {.cell}

```{.r .cell-code}
T1 <- grades |>
  summarise(min_Grade=min(Exam,na.rm=TRUE),
            max_Grade=max(Exam,na.rm=TRUE),
            mean_Grade=mean(Exam,na.rm=TRUE),
            median_Gradem=median(Exam,na.rm=TRUE))
knitr::kable(T1)
```

::: {.cell-output-display}
| min_Grade| max_Grade| mean_Grade| median_Gradem|
|---------:|---------:|----------:|-------------:|
|         0|        20|   7.148729|           6.5|
:::
:::


## Exercise 3


::: {.cell}

```{.r .cell-code}
N <- sum(is.na(grades$Exam))
```
:::

The number of students who did not take the final exam is  60

## Exercise 4

::: {.cell}

```{.r .cell-code}
ggplot(grades, aes(x = Exam)) +
  geom_bar(fill="lightblue")+
  xlab("Grade") +
  ylab("Number of the students")
```

::: {.cell-output-display}
![](exercise_files/figure-html/unnamed-chunk-5-1.png){width=672}
:::
:::
