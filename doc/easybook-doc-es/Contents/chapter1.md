# Publicando tu primer libro #

**easybook** es una aplicación que te permite publicar fácilmente libros en diferentes formatos electrónicos. Inicialmente se ideó para publicar libros técnicos de programación, pero con **easybook** puedes publicar cualquier tipo de libro, manual o documentación.

Para utilizar **easybook** tienes que tener instalado en tu ordenador PHP 5.3.2 o superior. Si no entiendes la frase anterior, coméntaselo a algún amigo informático y envíale un enlace a esta página para que pueda ayudarte. Si no lo haces, no vas a poder continuar. Para comprobar qué versión de PHP tienes instalada, abre una consola de comandos y ejecuta lo siguiente:

    php -v

**easybook** es una aplicación gratuita y de software libre. Esto significa que puedes hacer con ella lo que quieras, incluso venderla y ganar dinero. Las únicas condiciones que debes cumplir son:

  1. Mantener siempre el archivo `LICENSE.md`, que explica la licencia de la aplicación y quién es su autor original.
  2. Todo tu trabajo debes publicarlo con la misma licencia, así que otra gente también podrá vender y beneficiarse de todo tu trabajo.

Los libros que escribas con **easybook** son de tu entera propiedad, lo que incluye todos los derechos de autor aplicables en cada país. No estás obligado a compartir estas obras de ninguna manera, incluso aunque te beneficies de ellas económicamente.

## Descargando easybook ##

Antes de descargar **easybook**, crea un directorio para guardarlo, como por ejemplo:
  
  * Si utilizas Windows: `C:\Users\javier\proyectos\easybook`
  * Si utilizas Mac OS X: `/Users/javier/proyectos/easybook`
  * Si utilizas Linux: `/home/javier/proyectos/easybook`

Si conoces y utilizas la herramienta Git, abre una consola de comandos y ejecuta lo siguiente para clonar el repositorio público de **easybook** (reemplaza `<directorio>` por la ruta del directorio creado anteriormente):

    $ git clone http://github.com/javiereguiluz/easybook.git <directorio>

Si no utilizas Git, puedes descargar **easybook** mediante un archivo comprimido `.zip`. No es algo tan chulo como usar Git, pero funciona igual de bien. Descarga el siguiente archivo y descomprímelo en el directorio creado anteriormente: <http://github.com/javiereguiluz/easybook/zipball/master>

### Probando easybook ###

Una vez descargado/descomprimido, abre una consola de comandos, entra en el directorio donde has guardado **easybook** y comprueba que se ha descargado correctamente ejecutando el siguiente *script* de PHP:

    $ ./book

Si todo va bien, deberías ver el siguiente mensaje de bienvenida de **easybook**:

                        |              |    
    ,---.,---.,---.,   .|---.,---.,---.|__/ 
    |---',---|`---.|   ||   ||   ||   ||  \ 
    `---'`---^`---'`---|`---'`---'`---'`   `
                   `---'

    easybook is the easiest and fastest tool to generate
    technical documentation, books, manuals and websites.

    Available commands:
      help      Displays help for a command
      list      Lists commands
      new       Creates a new empty book
      publish   Publishes an edition of a book
      version   Shows installed easybook version

Si se produce algún error al ejecutar `./book`, prueba a ejecutarlo como `php book`. Si se siguen produciendo errores, comprueba los permisos de ejecución del *script* `book`. Si todo lo anterior falla, pregunta a algún amigo o familiar informático.

El *script* `./book` es el punto de acceso a todos los comandos internos de **easybook**. Así por ejemplo, para conocer qué versión de **easybook** tienes instalada, debes ejecutar el comando `version` a través del *script* `book`:

    $ ./book version


                        |              |    
    ,---.,---.,---.,   .|---.,---.,---.|__/ 
    |---',---|`---.|   ||   ||   ||   ||  \ 
    `---'`---^`---'`---|`---'`---'`---'`   `
                   `---'

    easybook installed version: 4.0

## Creando el libro ##

En esta sección vas a crear el primer libro de prueba con **easybook**. Si lo que quieres es probar lo más rápidamente posible las características de **easybook**, es mejor que utilices cualquiera de los dos libros de prueba ya creados: `easybook-doc-es` (documentación de **easybook** en español) y `easybook-doc-en` (documentación de **easybook** en inglés). En este caso, puedes saltar directamente hasta la sección *Publicando el libro*.

**easybook** requiere para su funcionamiento que tu libro tenga una determinada estructura de archivos y directorios. Para que no tengas que hacerlo a mano, los libros de **easybook** se crean con el comando `new` :

    $ ./book new "El origen de las especies"

Después del comando `new` deja un espacio en blanco y escribe el título de tu libro encerrándolo entre comillas. El resultado de este comando es un directorio llamado `el-origen-de-las-especies` dentro del directorio `doc/` de **easybook**. Dentro del nuevo directorio deberías ver la siguiente estructura:

    <easybook>/
        doc/
            el-origen-de-las-especies/
                config.yml
                Contents/
                    chapter1.md
                    chapter2.md
                    images/
                Output/

A continuación se explica el propósito de cada archivo y directorio creado por **easybook**:

  * `config.yml`, este archivo contiene todas las opciones de configuración del libro. Más adelantes se explican con detalle todas las opciones, pero de momento puedes modificar la opción `author` para indicar el nombre del autor del libro (por ejemplo, `Charles Darwin`). También puedes poner `es` en la opción `language` para indicar que el libro está escrito en español.
  * `Contents/`, en este directorio se encuentran todos los contenidos del libro (tanto texto como imágenes). **easybook** crea por defecto dos capítulos de prueba (`chapter1.md` y `chapter2.md`) y un directorio vacío llamado `images/`.
  * `Output/`, inicialmente este directorio está vacío, pero es muy importante porque aquí se guardan los libros publicados.

## Escribiendo el libro ##

Los contenidos del libro se escriben en archivos de texto normales utilizando el formato Markdown. Este formato se ha convertido en el estándar *de facto* para escribir documentación en Internet. Si a pesar de ello no conoces su funcionamiento, lee la [guía de referencia de Markdown](http://daringfireball.net/projects/markdown/syntax) (en inglés). Aunque Markdown es el único formato que por el momento soporta **easybook**, en el futuro se añadirá soporte para reStructuredText, Textile y cualquier otro formato suficientemente utilizado.

Así que olvida por un momento **easybook**, coge tu editor de textos favorito (`vi`, *Notepad*, *TextMate*, *SublimeText*, etc.) y escribe los capítulos de tu libro utilizando el formato Markdown.

La estructura de un libro puede ser muy compleja (portada, página de título, agradecimientos, dedicatoria, capítulos, secciones, etc.). **easybook** soporta todos los tipos de contenido comunes de los libros, pero de momento sólo vamos a centrarnos en los capítulos. Puedes crear tantos capítulos como quieras y cada uno puede ser tan pequeño o tan grande como necesites. Lo único que debes hacer es añadir en la opción `contents` del archivo `config.yml` todos los capítulos que forman el libro:

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 1, content: chapter1.md }
            - { element: chapter, number: 2, content: chapter2.md }

Cada línea de la opción `contents` indica un contenido del libro. Los elementos `cover` (portada) y `toc` (índice de contenidos) son especiales y se explican con detalle más adelante. Los capítulos se añaden mediante elementos de tipo `chapter`. Para cada uno debes indicar su número con la opción `number` y el nombre del archivo que tiene sus contenidos mediante la opción `content`.

La principal característica de **easybook**, además de su increíble rapidez, es su flexibilidad, ya que nunca te obliga a trabajar de una determinada manera. ¿Quiéres numerar tus capítulos no consecutivamente? Pensarán que estás loco, pero puedes hacerlo:

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 100, content: chapter1.md }
            - { element: chapter, number: 56,  content: chapter2.md }

¿Quiéres utilizar letras en vez de números? Esto es más propio de los apéndices que de los capítulos, pero también puedes hacerlo:

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: A, content: chapter1.md }
            - { element: chapter, number: B, content: chapter2.md }

Igualmente, puedes utilizar cualquier nombre para el arhivo de los contenidos del capítulo, como en el siguiente ejemplo que mezcla varios idiomas:

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 1, content: chapter1.md }
            - { element: chapter, number: 2, content: capitulo2.md }

También puedes utilizar nombres de archivo más significativos para que te sea más fácil localizar los contenidos del libro:

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 1, content: publica-tu-primer-libro.md  }
            - { element: chapter, number: 2, content: publica-tu-segundo-libro.md }

Lo más importante de la opción `contents` es el orden en el que defines los contenidos. El libro publicado siempre estará formado por esos contenidos y en ese orden. Así que por ejemplo, la siguiente configuración mostraría la portada del libro entre los dos capítulos y el índice de contenidos justo al final (completamente delirante, pero con **easybook** es muy fácil hacerlo):

    book:
        ...
        contents:
            - { element: chapter, number: 1, content: publica-tu-primer-libro.md  }
            - { element: cover }
            - { element: chapter, number: 2, content: publica-tu-segundo-libro.md }
            - { element: toc   }

Por defecto todos los archivos de contenidos se guardan directamente en el directorio `Contents/`. No obstante, si tu libro es muy complejo, puedes dividir los contenidos en subdirectorios . Después, sólo tienes que indicarlo en la opción `content` (si la ruta del archivo tiene espacios, no olvides encerrarlo entre comillas):

    book:
        ...
        contents:
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 1, content: introduccion/capitulo1.md }
            - { element: chapter, number: 2, content: introduccion/capitulo2.md }
            - { element: chapter, number: 3, content: avanzado/capitulo1.md }

La configuración anterior significa que que los contenidos de tu libro están estructurados de la siguiente manera:

    <tu-libro>/
        ...
        Contents/
            introduccion/
                capitulo1.md
                capitulo2.md
            avanzado/
                capitulo1.md


## Publicando el libro ##

Cuando termines de escribir todos los capítulos y de añadirlos en el archivo `config.yml`, abre una consola de comandos y ejecuta lo siguiente (cambia `el-origen-de-las-especies` por el nombre del directorio donde se encuentra tu libro):

    $ ./book publish 'el-origen-de-las-especies' web

Si todo funciona bien, en el directorio `Output/` del libro verás que se ha creado un directorio llamado `web` y en su interior encontrarás el archivo `book.html`. Este es el libro completo en formato HTML, listo para publicar en Internet.

Ejecuta a continuación el siguiente comando :

    $ ./book publish 'el-origen-de-las-especies' website

Ahora en el directorio `Output/` del libro se ha creado el directorio `website` y en su interior verás varias páginas HTML, una para cada capítulo del libro. Abre el archivo `index.html` en un navegador y verás que **easybook** ha convertido tu libro en todo un sitio web listo para publicar en Internet.

Por último, ejecuta el siguiente comando:

    $ ./book publish 'el-origen-de-las-especies' print

Dentro del directorio `Output/` verás el directorio `print` y en su interior, un archivo llamado `book.pdf` que contiene la versión PDF del libro, lista para imprimir. La conversión a PDF se realiza con ayuda de una aplicación externa llamada [PrinceXML](http://www.princexml.com/). Si no la tienes instalada en tu ordenador, puedes descargar una versión de prueba completamente funcional en <http://www.princexml.com/download/>

Como acabas de ver, **easybook** te permite publicar un mismo libro de muchas maneras diferentes. Cada una de estas maneras se denomina **edición** y su funcionamiento se explica con detalle en el siguiente capítulo.

## Opciones de configuración del libro ##

En las secciones anteriores has modificado las opciones `author` y `language` para indicar el autor y el idioma del libro. En realidad, los libros de **easybook** cuentan con muchas más opciones que se configuran en el archivo `config.yml`. Sus valores por defecto se muestran a continuación:

    book:
        title:            "(el título que escribiste al crear el libro)"
        author:           "Change this: Author Name"
        edition:          "First edition"
        language:         en
        publication_date: ~

        generator: { name: easybook, version: 4.0 }

        contents:
            # available element types: acknowledgement, appendix, author, chapter,
            # cover, dedication, edition, license, part, title, toc
            - { element: cover }
            - { element: toc   }
            - { element: chapter, number: 1, content: chapter1.md }
            - { element: chapter, number: 2, content: chapter2.md }

        editions:
            print:
                # (esta opción es compleja, se explica más adelante)
            web:
                # (esta opción es compleja, se explica más adelante)
            website:
                # (esta opción es compleja, se explica más adelante)

Las dos últimas opciones son las más complejas y se explican con detalle en los próximos capítulos: `contents` define los contenidos del libro y su orden; `editions` define las características de cada edición del libro.

El resto de opciones son las que establecen la información básica del libro:

  * `title`, es el título del libro. Por defecto se utiliza el mismo valor que escribiste al crear el libro, pero puedes modificarlo tantas veces como quieras.
  * `author`, es el nombre del autor del libro. Si el libro tiene varios autores, escríbelos todos seguidos separándolos con una coma: `"Nombre1 Apellido1, Nombre2 Apellido2, ..."`
  * `edition`, es el texto que describe la edición del libro. Normalmente, se utilizan los valores *primera edición*, *segunda edición*, etc. pero puedes utilizar cualquier valor que quieras para describir la edición actual del libro, ya que **easybook** lo mostrará tal cual.
  * `language`, idioma en el que está escrito el libro. El idioma se indica con un código de dos letras: `es` para español, `en` para inglés, `fr` para francés, `it` para italiano, `de` para alemán, `ca` para catalán, `eu` para euskera, etc.
  * `publication_date`, fecha de publicación del libro. Por defecto su valor es `~`, que significa que no se ha establecido ninguna fecha. En este caso, **easybook** asigna automáticamente el valor del día en el que se publica el libro. Si quieres establecer una fecha de publicación fija, indícala con el formato `día-mes-año`. Ejemplo: `23-11-2012`.
