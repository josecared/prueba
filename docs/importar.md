## Introducción

Con el material visto hasta ahora, estamos bastante preparados para representar datos ordenados de forma lógica y agradable. Existen muchísimas más opciones para graficar empleando _ggplot2_, aunque en este tutorial únicamente hemos mostrado lo que nos parece esencial (para saber más, puedes revisar el resto de posibilidades [aquí](https://r4ds.had.co.nz/)). 

Sin embargo, aunque ya sepamos mucho sobre graficación, todavía no hemos enseñado cómo importar nuestros propios datos y emplear todo lo estudiado en nuestros propios trabajos, tema que vamos a ver a continuación.

Vamos a emplear el paquete de Tidyverse **_readr_**, que es el que se encarga de importar los datos. Abrimos RStudio y activamos la librería:

```r
library(tidyverse)
```

## _Tibbles_

El código base de R utiliza ```data.frame``` a la hora de representar datos en tablas. Sin embargo, estos son un poco antiguos y a veces se hace un poco engorroso trabajar con ellos. Tidyverse trata de solucionar esto empleando el paquete **_tibble_**.

Los _tibbles_ funcionan muy parecido a los ```data.frame```, pero presentan características que los hace mucho más sencillo trabajar con ellos:

- Son mucho **más rápidos**.
- **No transforman** los vectores de caracteres **a factores**, cosa que sí ocurre con los ```data.frame```.
- Son **más reproducibles**, es decir, es más probable que aquellos que trabajen con los mismos datos que tú lleguen a los mismos resultados.

Podemos transformar cualquier ```data.frame``` en un _tibble_ empleando ```as_tibble()```. Empleemos esta función con ```iris```, un ```data.frame``` incluido en R:

```r
as_tibble(iris)
```
```
# A tibble: 150 x 5
   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
          <dbl>       <dbl>        <dbl>       <dbl> <fct>  
 1          5.1         3.5          1.4         0.2 setosa 
 2          4.9         3            1.4         0.2 setosa 
 3          4.7         3.2          1.3         0.2 setosa 
 4          4.6         3.1          1.5         0.2 setosa 
 5          5           3.6          1.4         0.2 setosa 
 6          5.4         3.9          1.7         0.4 setosa 
 7          4.6         3.4          1.4         0.3 setosa 
 8          5           3.4          1.5         0.2 setosa 
 9          4.4         2.9          1.4         0.2 setosa 
10          4.9         3.1          1.5         0.1 setosa 
# ... with 140 more rows
```

También puedes crear tus propios _tibbles_ desde cero. Para ello, empleamos la función ```tibble()```, que construye las tablas por columnas. Por ejemplo:

```r
tibble(
  "Columna 1" = 1:5,
  "Columna 2" = 2,
  "Columna 3" = c(2, 7, 4, 1, 4),
)
```
```
# A tibble: 5 x 3
  `Columna 1` `Columna 2` `Columna 3`
        <int>       <dbl>       <dbl>
1           1           2           2
2           2           2           7
3           3           2           4
4           4           2           1
5           5           2           4
```

Los _tibbles_ ofrecen muchas posibilidades a la hora de crear tablas de datos. Si quieres saber más, puedes usar el comando ```?tibble```, o puedes consultar el manual oficial de _Tidyverse_ [aquí](https://r4ds.had.co.nz/tibbles.html).

## Importando datos

Importar archivos de datos es muy sencillo, simplemente usa una de las siguientes funciones, dependiendo de 

| FUNCIÓN             | DESCRIPCIÓN                                 |
| --------------------| --------------------------------------------|
| ```read_csv()```    |Lee archivos delimitados por comas           |
| ```read_csv2()```   |Lee archivos delimitados por punto y comas   |
| ```read_tsv()```    |Lee archivos delimitados por tabulaciones    |
| ```read_table()```  |Lee archivos delimitados por espacios        |

Existen más funciones parecidas. Puedes revisarlas todas con ```?read_delim```.

A partir de ahora, salvo excepciones, vamos a utilizar datos no incluidos dentro del paquete _Tidyverse_.

| VARIABLE          | DESCRIPCIÓN                                             |
|-------------------|---------------------------------------------------------|
| _Plate_           |Número de la placa de petri                              |
| _Lane_            |Linea en cada placa de petri                             |
| _Species_         |Especie                                                  |
| _Specimen_        |Individuo (espécimen) concreto                           |
| _Host_            |Huésped                                                  |
| _ICES.rectangle_  |Zonas geográficas de los que se obtuvieron las muestras  |
| _GPI, LDH..._     |Genotipos                                                |












!!! cite "Referencias"
    - [***R for Data Science***; Hadley Wickham, Garrett Grolemund et al.](https://r4ds.had.co.nz/)
    - [***Morphometric discrimination of two allozymically diagnosed sibling species***; Wayland, Matthew T. et al.](https://doi.org/10.5061/dryad.hd5c7)