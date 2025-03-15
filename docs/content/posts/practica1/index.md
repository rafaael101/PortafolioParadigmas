+++
date = '2025-02-21T08:43:05-08:00'
draft = false
title = 'Práctica 1: Elementos básicos de los lenguajes de programación'
summary = 'Edgar Rafael Garcia Ceseña'
+++

# Introducción
  En esta práctica, el objetivo principal es identificar los elementos fundamentales del lenguaje de programación manejado en el programa de biblioteca el cual es Lenguaje C, lo que tenemos que identificar es lo siguiente: nombres, marcos de activación, bloques de alcance, administración de memoria, expresiones, comandos, control de secuencia como lo es; selección, iteración y recursión, subprogramas, y tipos de datos.

# Desarrollo
  En esta parte, mostraré los elementos fundamentales que se encuentran en los archivos .c y .h, y describiré la función que tienen cada uno. El [Código](https://github.com/rafaael101/PortafolioParadigmas/tree/master/docs/content/posts/practica1/biblioteca/src) completo lo puedes consultar en el link adjunto. En este reporte solo se mostrarán unas partes de este mismo.

## 1. Nombres
  Los **nombres** son la forma más fundamental de abstracción, proveen un mecanismo para
  referirse a cualquier cosa; desde simples valores, hasta complejos conjuntos de datos y  comportamientos en programación orientada a objetos, a librerías enteras en la forma de
  módulos.

  Ejemplos de nombre encontrados en el código:
  ```C
  // En Funciones
  addBook(), displayMembers(), freeMembers(), displayBooks().

  // En estructuras
  book_t, member_t, genre_t.

  // En variables
  count, members, new_book, genre.
  ```
## 2. Marcos de activación
Un **marco de activación** es una estructura de datos que se crea cada vez que una función es llamada. Sirve para almacenar información necesaria para ejecutar esa función y, cuando la función termina, el marco de activación se destruye.

Ejemplo de marco de activación en el código:
```C
int main(){
    case 1:
        addBook(&library, &bookCount); // Se crea un marco de activación para addBook
        break;
}

void addBook(book_t **library, int* count ){
    // Asignacion de memoria en el heap
    // Aqui se ejecuta toda la logica de la fucnion mientras el marco de activacion esta activo.
    book_t *new_book = (book_t *)malloc(sizeof(book_t));
    if (!new_book) {
        printf("Error al asignar memoria para el nuevo libro.\n");
        return;
    }
    incrementHeapAllocations(new_book, sizeof(book_t));
    printf("Memoria asignada para un nuevo libro (ID: %d) en el heap\n", new_book->id);

    printf("\nIngresa ID del libro: ");
    scanf("%d", &new_book->id);

    printf("Ingresa titulo del libro: ");
    getchar();
    fgets(new_book->title, 100, stdin);
    new_book->title[strcspn(new_book->title, "\n")] = '\0';

    printf("Ingresa nombre del autor: ");
    fgets(new_book->author, 100, stdin);
    new_book->author[strcspn(new_book->author, "\n")] = '\0';

    printf("Ingresa el ano de publicacion: ");
    scanf("%d", &new_book->publication_year);

    printf("Ingresa el genero del libro (0: FICTION, 1: NON_FICTION, 2: SCIENCE, 3: HISTORY, 4: FANTASY, 5: BIOGRAPHY, 6: OTHER): ");
    int genre;
    scanf("%d", &genre);
    new_book->genre = (genre_t)genre;

    printf("Ingresa la cantidad de libros: ");
    scanf("%d", &new_book->quantity);

    new_book->next = *library;
    *library = new_book;
    (*count)++;

    printf("\nEl libro fue agregado exitosamente!\n");
    displayMemoryUsage();
    // El marco de activación se destruye al termino de la funcion addBook.
}
```
## 3. Bloques de alcance
Los **bloques** son una unidad fundamental de
organización de programas. Un bloque es una
sección de texto de programa que contiene enlaces de nombres que son locales para el bloque. Así, un bloque corresponde a un marco en el entorno.

En C, los bloques se suelen definir con llaves **{ }** las cuales muestran el inicio y el final del bloque, aquí se muestran unos ejemplos:
```C
// Bloque de la funcion 1 delimitados por las llaves {}
void displayBooks(book_t *library) {
    if (!library) {
        printf("\nNo hay libros disponibles.\n");
        return;
    }

    printf("\nLibros disponibles en biblioteca:\n");
    displayBooksRecursive(library);
    displayMemoryUsage();
}

// Bloque de la funcion 2 delimitados por las llaves {}
void displayBooksRecursive(book_t *library) {
    if (!library) {
        return;
    }
    printf("\nID libro: %d\nTitulo: %s\nAutor: %s\nAno de publicacion: %d\nGenero: %s\nCantidad: %d\n",
        library->id, library->title, library->author, library->publication_year, genreToString(library->genre), library->quantity);
    displayBooksRecursive(library->next);
}
```
## 4. Administración de memoria
Los programas operan con datos que se almacenan en la memoria. En general, el conjunto de datos que se utilizan en un
programa puede variar con el tiempo (memoria dinámica) y la cantidad de almacenamiento requerido por un programa no se
puede predecir en el momento de la compilación. Como resultado, un lenguaje y su implementación deben proporcionar
mecanismos para gestionar el uso de la memoria de un programa.

En el programa se logra observar el manejo de los siguientes tipos de memoria:

**Memoria Estática**

La memoria estática en el programa se puede observar en estos ejemplos:
```C
// Variable estatica global
static int static_var = 0; 
```
Esto es manejo de memoria estática ya que la variable ya que se puede acceder a ella en cualquier punto del programa y esta misma tiene una vida útil que abarca todo el programa.

**Memoria Dinámica**

La memoria dinámica en el programa se puede observar en estos ejemplos:
```C
void addBook(book_t **library, int* count ) {
    // Asignacion de memoria dinámica
    book_t *new_book = (book_t *)malloc(sizeof(book_t));
    //Resto de codigo
}
```
 Se dice que esto es manejo de memoria dinámica debido a que esta variable tiene una vida útil la cual no esta vinculada a la ejecución de algun fragmento de código específico. En C, para liberar esta memoria es necesario el uso de free(), ya que si no se utiliza, la memoria se perderá y podrá causar errores. Al ser memoria dinámica, su tamaño puede variar con el paso del tiempo hasta ser liberada.
 
**Memoria Automática**

La memoria automática en el programa se puede observar en estos ejemplos:
```C
void returnBook(book_t *library, member_t *members) {
    // Asignacion de memoria automática
    int bookID, memberID;
    // Resto del código
}
```
Esto es manejo de memoria automática debido a que las variables se crearon al inicio del alcance de la variable y se destruirá al salir de la función.
## 5. Expresiones
Una expresión es una combinación de valores, variables, operadores y llamadas a funciones que produce un valor.

Ejemplos de expresion en el programa:
```C
if (bookFound && memberFound) //Esta expresión genera un valor booleano al evaluar ambas condiciones.
bookFound->quantity++; //Expresión aritmética que incrementa el valor de quantity.
```
## 6. Comandos
Algunos comandos que se pueden observar en el programa son:

**Asignación**
```C
 book_t *current = library;

 book_t *next = current->next;

 member_t *current = members;
```
**Llamada a función**
```C
loadLibraryFromFile(&library, &bookCount, "library.txt");
loadMembersFromFile(&members, &memberCount, "members.txt");
```
**Incremento**
```C
i++;

bookFound->quantity++;
```
## 7. Control de secuencia
**Selección**

La selección permite tomar decisiones y alterar el flujo de ejecución del programa en función de ciertas condiciones.

Ejemplo en el código:
```C
if (!members) {
        printf("\nNo hay miembros disponibles.\n");
        return;
    }

// Tambien usa switch
 switch (choice) {
            case 1:
                addBook(&library, &bookCount);
                break;
 }
```
**Iteración** 

La iteración permite repetir la ejecución de un conjunto de instrucciones, ya sea un número determinado de veces o hasta que se cumpla una condición.

Ejemplo en el código:
```C
while (current) {
        if (current->id == memberID) {
            printf("\nID miembro: %d\nNombre: %s\nCantidad de libros prestados: %d\n",
                current->id, current->name, current->issued_count);
            for (int i = 0; i < current->issued_count; i++) {
                book_t *book = findBookById(library, current->issued_books[i]);
                if (book) {
                    printf("  Libro ID: %d\n  Titulo: %s\n  Autor: %s\n", book->id, book->title, book->author);
                }
            }
            displayMemoryUsage();
            return;
        }
        current = current->next;
    }
```
**Recursión**

La recursión ocurre cuando una función se llama a sí misma para resolver un problema más pequeño o más simple.

Ejemplo en el código:
```C
void displayBooksRecursive(book_t *library) {
    if (!library) {
        return;
    }
    printf("\nID libro: %d\nTitulo: %s\nAutor: %s\nAno de publicacion: %d\nGenero: %s\nCantidad: %d\n",
        library->id, library->title, library->author, library->publication_year, genreToString(library->genre), library->quantity);
    displayBooksRecursive(library->next); //Aqui se llama a si misma la funcion
}
```
**Subprogramas**

Los subprogramas se ven como funciones en el código, las funciones son bloques de código independientes y reutilizables que pueden aceptar entradas (parámetros) y devolver resultados.

Ejemplo en el código:
```C
void freeLibrary(book_t *library) {
    book_t *current = library;
    while (current) {
        book_t *next = current->next;
        incrementHeapDeallocations(current);
        free(current);
        current = next;
    }
    displayMemoryUsage();
}
```
**Tipos de datos**

Los tipos de datos determinan qué tipo de valor puede almacenar una variable. En C, a diferencia de algunos otros lenguajes, es necesario especificar el tipo de dato.

Ejemplo en el código:
```C
typedef struct _book {
    int id; // Dato entero
    char title[100]; // Arreglo de caracteres
    char author[100];// Arreglo de caracteres
    int publication_year; // Dato entero
    genre_t genre; // Dato de tipo genre_t que es un struct
    int quantity; // Dato entero
    struct _book *next; // Dato puntero del tipo struct _book
} book_t; // Nombre del tipo de dato nuevo definido
```

# Conclusión
En conclusión, esta práctica me sirvió mucho para conocer mejor aún la sintaxis del lenguaje y la estructura de este mismo. Aprender todo esto hace que mejoremos la manera en la cual escribimos el código para que sea más legible y esté bien organizado. Así como también vi más acerca de la importancia del manejo de memoria, porque en un lenguaje como C es muy importante, ya que nosotros somos los responsables de liberar la memoria en caso de ser dinámica pero también es de suma importancia saber el como funcionan los otros tipos de memoria.

 ## Links
[REPOSITORIO](https://github.com/rafaael101/PortafolioParadigmas)
  
[PAGINA](https://rafaael101.github.io/PortafolioParadigmas/)