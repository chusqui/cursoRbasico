# Curso Básico de R

Este es el entorno de desarrollo colaborativo de los apuntes del [Curso Básico de R](http://cursorbasico.usar.org.es/).


## Licencia

El contenido de este respositorio tiene licencia [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/). Estás invitado a ayudarnos a continuar su desarrollo. 

## Generación de los apuntes

Los apuntes pueden generarse usando [pandoc](http://johnmacfarlane.net/pandoc/). El fichero `knit` del directoro `utils` puede usarse para exportar el documento a una variedad de formatos.

Desde el directorio base (el padre de `utils`), hay que ejecutar


```bash
utils/knit epub    # EPub ebook
utils/knit html    # a single html page
utils/knit pdf     # PDF through XeLaTeX
utils/knit github  # markdown for github
````

Para generar el fichero .pdf es necesario disponer de ciertas dependencias: LaTeX, xelatex, los tipos de letras que aparecen en `template.tex`, etcc.


`knit` ha sido desarrollado por ...

Los ficheros fuente están en el directorio `src` del repositorio. El resto son ficheros markdown generados por el script `knit`. Para editar los apuntes, por lo tanto, basta con cambiar los ficheros de `src`: los del directorio anterior se generan automáticamente a partir de los anteriores.

