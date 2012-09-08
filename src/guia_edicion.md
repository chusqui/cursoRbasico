# Guía de edición de la documentación del curso básico de R

Este documento es una guía para la edición de la documentación del curso básico de R. En el primer apartado discute las cuatro herramientas que se van a utilizar para generar la documentación. En en el segundo indica la manera en que se integran así como pautas de uso.

## Infraestructura

Esta sección contiene cuatro apartados claramente diferenciados. Cada uno de ellos cubre una función distinta y son mutuamente independientes.

### git, github y edición colaborativa

Siendo este un proyecto colaborativo, se ha planteado la conveniencia de utilizar una plataforma que permite la edición simultánea por parte de varios autores desde ubicaciones remotas gestionando adecuadamente los cambios, las versiones, los conflictos de edición, etc.

El conocimiento de git en particular y de los sistemas de gestión de versiones en general puede resultar útil para otros proyectos aparte de este: muchos desarrolladores, escritores, etc., utilizan este tipo de herramientas para organizar su trabajo. Incluso para proyectos individuales.

Vamos a utilizar github, un servicio centralizado que permite la gestión de proyectos. github mantiene el código en sus servidores, permite el acceso de los colaboradores al código en modo de lectura y escritura y el de terceros en modo de lectura. github utiliza internamente git, un gestor de versiones moderno similar a otros tal vez más conocidos como subversion o CVS.

Los usuarios de git mantienen en su máquina local una copia del proyecto. Una sesión típica de trabajo consiste en lo siguiente:

* Actualizar el respositorio local descargando a la máquina los cambios que han podido haber realizado otros.
* Editar en local usando las herramientas (editores de texto, etc.) favoritos de cada cual.
* Subir los cambios realizados al respositorio central para que queden disponibles para los demás.

github proporciona interfaces gráficos para realizar estas operaciones con comodidad para usuarios de [Windows](http://windows.github.com/) y [Mac](http://mac.github.com/). Los usuarios de Linux pueden utilizar git desde la línea de comandos:

* `git checkout`, para crear un repositorio en local idéntico al existente en github
* `git pull`, para actualizar el respositorio local a imagen del remoto
* `git add` y `git rm` para añadir y eliminar ficheros
* `git commit`, para incluir cambios en el repositorio local
* `git push`, para subir los cambios a github

Existen diversos tutoriales en internet sobre el uso de git desde la línea de comandos que incluyen aspectos (que no serán necesarios aquí) como la gestión de distintas ramas de desarrollo (_branches_), etc.

Es importante indicar qué cambios se han realizado en los ficheros en cada commit.


### markdown: formato de texto

La documentación se va a redactar en markdown. markdown es un lenguaje de marcas simple para generar documentación. Da formato al texto utilizando un pequeño conjunto de etiquetas para indicar las secciones (títulos, capítulos, etc.), negritas, cursivas, listas, etc. Existen multitud de manuales (y son todos muy breves) al respecto. Incluso la página de [markdown en la Wikipedia](http://en.wikipedia.org/wiki/Markdown) es bastante completa.

Por ejemplo, esto es una **negrita** y esto es una _cursiva_. Los enlaces se indican [así](http://r-es.org).

Para usar LaTeX se puede escribir $2\pi$, es decir, rodeando el código LaTeX de símbolos del dólar.


### knitr e inclusión de código y salida de R en el documento

knitr es un paquete de R que permite incluir _trozos_ de código en R dentro de ficheros markdown. El paquete se encarga luego de procesarlos y generar un fichero de markdown puro que incluye la salida generada por R en el resultado final.

Por ejemplo, si se escribe dentro de un párrafo `'el valor es {% 6 * pi %}'`, es decir, usando las marcas `{%` y `%}`, knitr _resolverá_ `6 * pi` llamando a R para que resuelva la operación matemática correspondiente e imprima el resultado.

Se pueden insertar gráficos (en esta ocasión llamando al paquete **ggplot2**) utilizando expresiones del tipo 

``` {r intro-plot, message=FALSE, fig.cap='A sample plot in a dynamic report.'}
library(ggplot2)
qplot(hp, mpg, data = mtcars) + geom_smooth()
````

También se pueden insertar tablas (aquí usando el paquete **xtable**) de esta otra manera:

``` {r intro-table, results='asis'}
library(xtable)
xtable(head(mtcars[, 1:5]))
````

En la red existen minitutoriales de knitr como [este](https://github.com/yihui/knitr-examples/blob/master/001-minimal.Rmd), colecciones de [ejemplos](http://yihui.name/knitr/demos), etc.


### pandoc, LaTeX y generación del documento en diversos formatos

[`pandoc`](http://johnmacfarlane.net/pandoc/) es un programa que permite generar documentos en una variedad de formatos. Puede transformar documentos de OpenOffice en LaTeX, LaTeX en HTML, etc. 

En nuestro caso, lo vamos a utilizar para transformar los ficheros que se van a escribir en `markdown` en HTML, PDF y ePub.


## Uso para la generación de la documentación

### Carpetas

El repositorio que se ha creado en github para la documentación contiene varias carpetas:

* carpeta base
* `figure`, que almacena los gráficos generados por `knitr`
* `src`, que contiene los ficheros que hay que editar
* `utils`, que contiene unos programas que facilitan las llamadas a `knitr` y `pandoc`.

Los ficheros editables de `src` contienen texto en `markdown` y son precisamente sobre los que hay que trabajar. La labor de generación de documentación consiste en editarlos y subir los cambios al servidor.

Es importante tener presente que **no hay que editar a mano otros ficheros que los contenidos en `src`**. La siguiente sección explica cómo los cambios realizados en ficheros del directorio `figure` o la carpeta base no son persistentes.

### Generación automática de la documentación

Una vez editados los ficheros de la carpeta `src`:

1. Se usará `knitr` para transformalos en otros ficheros también en `markdown`.
2. Se usará `pandoc` para convertir estos últimos a HTML, PDF o ePub.

En el primer paso `knitr` procesará los pedazos de código en los ficheros de `src` que contengan código en R y colocará la salida en la carpeta base. También se generarán los gráficos pertinentes, que se colocarán en `figure`.

Este es el motivo por el que no hay que introducir modificaciones en esos directorios donde se ubica la salida de `knitr`.

El directorio `utils` contiene dos programas. Realmente sólo es necesario llamar a uno de ellos, haciendo, por ejemplo,

`utils/knit pdf`

desde el directorio raíz del respositorio. Este comando debería:

1. _compilar_ los ficheros de `src` con `knitr` y generar los gráficos oportunos,
2. llamar a `pandoc` y crear un documento en PDF.

Otras opciones son

* `utils/knit github`
* `utils/knit epub`
* `utils/knit html`

para generar la documentación en esos otros formatos.

### Dependencias

Para generar la documentación hace falta tener instaladas una serie de dependencias. Por un lado, `knitr` requiere disponer tanto del paquete `knitr`en sí como todos los paquetes de R que se utilicen dentro del código de los ficheros de `src`.

La generación de salidas en otros formatos requiere de otros programas externos. En particular, de `pandoc`, de LaTeX y de una serie de extensiones de LaTeX.

### Notas

Los programas para la generación de la documentación, etc., son una versión de los que usa el autor de `knitr` para su [libro](https://github.com/yihui/knitr-book). Las dependencias (algunas de ellas algo exóticas) que precisa sirven para dar un formato elegante al resultado final.

Las dependencias faltantes pueden deducirse de los mensajes de error generados por las llamadas a `pandoc` que realiza el _script_ `knit` mencionado más arriba.

El uso de estos `scripts` puede resultar complicado en sistemas como Windows. Eso no significa que sea imposible aportar contenido al curso usando Windows. Pero sí que puede resultar complicado generar la salida en PDF.

## Quiero colaborar... ¿qué hago?

Si quieres colaborar, lo primero que tienes que hacer es leer esta guía.

Después tienes que abrir una cuenta en [https://github.com/](github) y solicitar acceso para editar el código (escribiendo al [creador del repositorio](https://github.com/cjgb)).

A partir de ese momento puedes hacer _checkout_ del proyecto, editar, subir los cambios, etc. De acuerdo con las instrucciones de esta guía.