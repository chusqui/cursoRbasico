# Curso Básico de R

Este es el entorno de desarrollo colaborativo de los apuntes del [Curso Básico de R](http://cursorbasico.usar.org.es/).


## Licencia

El contenido de este respositorio tiene licencia [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/). Estás invitado a ayudarnos a continuar su desarrollo. 

## Generación de los apuntes

Los apuntes pueden generarse usando [pandoc](http://johnmacfarlane.net/pandoc/). El fichero `knit` del directoro `utils` puede usarse para exportar el documento a una variedad de formatos.


```bash
./knit epub    # EPub ebook
./knit html    # a single html page
./knit pdf     # PDF through XeLaTeX
./knit github  # markdown for github
````

`knit` ha sido desarrollado por ...

Los ficheros fuente están en el directorio `src` del repositorio. El resto son ficheros markdown generados por el script `knit`. 

