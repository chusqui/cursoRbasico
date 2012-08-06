# Semana 2


No sé qué hacer para **impedir** que _knitr_ entienda que esto es un párrafo y no la continuación del título. ¡Lo he probado todo ya sin éxito! ¿Y si pongo una fórmula en $\LaTeX{}$?

¿Y si pruebo con dos párrafos?

## Y con un subtítulo

¿Será que tengo suerte?


And here is a table created with the **xtable** package:

``` {r intro-table, results='asis'}
library(xtable)
xtable(head(mtcars[, 1:5]))
````


