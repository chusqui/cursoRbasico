# Semana 2


No sé qué hacer para **impedir** que _knitr_ entienda que esto es un párrafo y no la continuación del título. ¡Lo he probado todo ya sin éxito! ¿Y si pongo una fórmula en $\LaTeX{}$?

¿Y si pruebo con dos párrafos?

## Y con un subtítulo

¿Será que tengo suerte?


And here is a table created with the **xtable** package:


```r
library(xtable)
xtable(head(mtcars[, 1:5]))
```

% latex table generated in R 2.15.1 by xtable 1.7-0 package
% Sun Aug  5 18:06:27 2012
\begin{table}[ht]
\begin{center}
\begin{tabular}{rrrrrr}
  \hline
 & mpg & cyl & disp & hp & drat \\ 
  \hline
Mazda RX4 & 21.00 & 6.00 & 160.00 & 110.00 & 3.90 \\ 
  Mazda RX4 Wag & 21.00 & 6.00 & 160.00 & 110.00 & 3.90 \\ 
  Datsun 710 & 22.80 & 4.00 & 108.00 & 93.00 & 3.85 \\ 
  Hornet 4 Drive & 21.40 & 6.00 & 258.00 & 110.00 & 3.08 \\ 
  Hornet Sportabout & 18.70 & 8.00 & 360.00 & 175.00 & 3.15 \\ 
  Valiant & 18.10 & 6.00 & 225.00 & 105.00 & 2.76 \\ 
   \hline
\end{tabular}
\end{center}
\end{table}



