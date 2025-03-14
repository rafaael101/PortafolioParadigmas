+++
date = '2025-02-21T08:43:05-08:00'
draft = true
title = 'Práctica 0: Uso de repositorios'
summary = 'Edgar Rafael Garcia Ceseña'
+++

# Introducción
  Esta práctica se divide en 3 partes, en las cuales llevamos a cabo un uso de las diversas funciones que tienen el markdown, Git y GitHub y también Hugo y GitHub Actions para generar nuestras propuas páginas estáticas, en esta práctica es muy importante ya que nos ayuda a saber lo esencial de lo antes mencionado.

# Desarrollo
  ## Primera sesión: Sintaxis y uso de markdown
  En esta esta sesión, conocimos acerca de algunas de las funciones que tiene markdown adentrandonos mas en la sintaxis para despues poder crear nuestros reportes correctamente. Aquí mostraré lo visto en clase junto con una breve explicación.
<!-- estos es un comentario -->
**En esta primera parte, se nos enseño como se podian poner los encabezados y era mediante el uso de el simbolo "#".**
# Encabezado 1
## Encabezado 2
### Encabezado 3
#### Encabezado 4
##### Encabezado 5

**En esta parte se nos mostró el como utilizar los diversos tipos de letras, para las italicas el uso de 1 * o también 1 _ , para negritas es doble * o doble _ y para texto rayado es doble ~.**
<!-- Italicas -->
Este es un texto en *italicas*

Este es un texto en _italicas_

<!-- Negritas -->
Este es un texto en **negritas**

Este es un texto en **negritas**

<!-- Rayado -->
Este "es" un texto ~~rayado~~

**Aquí, para el uso de listas, se utiliza * o numeros como 1, 2, 3, etc. y para lista dentro de la lista es igual, pero con una indentación.**
<!-- UL -->

* Elemento 1
* Elemento 2
* Elemento 3
  * Elemento 3.1
  * Elemento 3.2
* Elemento 4

<!-- OL -->
1. Elemento 1
2. Elemento 2
3. Elemento 3
   1. Elemento 3.1
   2. Elemento 3.2
4. Elemento 4

**Para los enlaces, se utiliza los [] para poner dentro el titulo del link y para poner el link se utilizan () donde debe de ir el link dentro. También se puede utilizar "" dentro de los parentesis para poner un titulo personalizado al poner el cursor encima del link.**
<!-- Enlaces -->
[UABC](www.uabc.mx)

[UABC](www.uabc.mx "Titulo personalizado")

**Para el uso de imagenes es parecido a los links, solo que ahora dentro de los [] va un texto para que aparezca en caso de que no se cargue la imagen, y se utiliza un ! antes de los corchetes. También se puede adjuntar un link a la imagen, metiendo todo el texto de la imagen dentro de unos [] y fuera poniendo entre () el link que quieres.**
<!-- Imagenes -->
![Yo](images/yowe.png "Peso pumba")
[![Yo](images/yowe.png "Peso pumba")](www.uabc.mx)
<img src="images/yowe.png" alt="vscode image" width="150" height = "auto">

**Para escribir bloques de código, se utilizan las ``` para iniciar el bloque y se ocupa de nuevo escrbir esas comillas al final para cerrarlo, despues de las primeras comillas, puedes especificar el codigo que quieras que aparezca.**
<!-- Bloques de codigo -->
```
This is a code block
This is the second line of the code block
```

```python
print("Hello world")
```

```Javascript
console.log("Hello world!")

const test = ()
```

```html
<h1>Hello World</h1>
```
**Para el manejo de tablas se utiliza el simbolo | y para las tareas se utiliza el * y para marcar tareas se utilizan los [] y dentro una x si se quiere marcar.**
<!-- Tablas -->
| Productos | Precio | Cantidad |
| --- | --- | --- |
| Laptop | 3.33 | 2 |
| Mouse | 10.33 | 1 |

| Productos | Precio | Cantidad |
| --------- | ------ | -------- |
| Laptop    | 3.33   | 2        |
| Mouse     | 10.33  | 1        |

<!-- Tareas -->
* [x] Primera tarea
* [ ] Segunda tarea
* [ ] Tercera tarea
* [x] Cuarta tarea

<!-- Menciones -->
@rafaael101 :+1: :smile:

  ## Segunda sesión: Git y GitHub
  En esta esta sesión, conocimos acerca de algunas de las funciones que tiene Git y GitHub, en la cual se nos mostraron algunos de los comandos que se pueden utilizar para hacer acciones con Git y GitHub como es el caso de crear y actualizar nuestros repositorios.

  Algunos de los comandos utilizados en la terminal bash fueron los siguientes:
  * **git init** — Inicializa un nuevo repositorio de Git en el directorio actual.
  * **git status** — Muestra el estado actual del repositorio: archivos modificados, añadidos, o pendientes de commit.
  * **git add <file>** — Añade un archivo específico al área de preparación (staging area) para incluirlo en el próximo commit.
  * **git commit** — Registra los cambios en el repositorio. Por lo general, se usa con el argumento -m "mensaje" para añadir una descripción breve del cambio.
  * **git config user.name "Your Name"** — Configura el nombre del usuario para los commits.
  * **git config user.email "name@example.com"** — Configura el correo del usuario para los commits.
  * **git log** — Muestra el historial de commits, con detalles como el autor, la fecha y el mensaje del commit.
  * **git branch** — Lista las ramas existentes en el repositorio.
  * **git switch** — Cambia a otra rama específica.
  * **git diff** — Muestra las diferencias entre archivos modificados y lo que está en el área de preparación o entre commits.
  * **git push** — Envía los commits locales a un repositorio remoto (como GitHub).
  
  En esta sesión, utilizamos los comandos necesarios para la creación de un repositorio especial de la materia en el cual estaremos subiendo las prácticas y reportes que hagamos.

  ## Tercera sesión: Creación de página estática con Hugo y GitHub Actions
  