---
layout: default
---

[Volver](../)

# Conceptos básicos

## Introducción

Para comenzar con el lenguaje, debemos tener presentes los siguientes conceptos:

* Se debe crear un proyecto Java.

* Un proyecto en Java siempre debe tener asignada una versión de Java.

* El código fuente debe estar contenido dentro de una carpeta de origen (source folder), comúnmente nombrada `src`. Podemos tener más de una source folder.

* Dentro de cada source folder, los archivos se deben agrupar en paquetes (packages). La forma de agruparlos deberá responder a la estructura o arquitectura del proyecto que adoptemos. La nomenclatura de un package por convención es: com.empresa.dominio. Se escribe desde lo más general (com) hasta lo más específico, siempre utilizando palabras en minúscula y separadas por puntos (.). En caso de tener un nombre compuesto como "Mi proyecto", se debe escribir como: com.miproyecto.dominio.

* El código fuente se escribe dentro de archivos con extensión .java. Muchos archivos con dicha extensión, las source folders y los paquetes, conforman el código fuente.

* Todo el código que escribamos vive dentro de una [clase](./clases.html), y todo el código que se ejecuta vive dentro de un [método](./metodos.html). Los fragmentos de esta guía se muestran sueltos por claridad, pero para poder correrlos hay que ubicarlos dentro de un programa: ver [tu primer programa](./introduccion-a-java.html#tu-primer-programa).

* Si una clase que necesitamos usar no pertenece al paquete `java.lang` (por ejemplo `Scanner` o `Random`), debemos importarla con `import` al principio del archivo. Ver [imports](./introduccion-a-java.html#imports).

* Java posee palabras reservadas como `public`, `private`, `int`, `return` o `final`, entre otras, las cuales no podremos utilizar para nombrar, por ejemplo, variables.

* Es posible incluir comentarios de utilidad para el desarrollador. Para esto se deben utilizar dos barras (`// Comentario`), lo cual crea un comentario de una sola línea, o bien barra-asterisco / asterisco-barra (`/* líneas comentadas */`) para comentar en múltiples líneas.

* Es posible comentar código que podría ejecutarse. El código comentado no será tenido en cuenta a la hora de ejecutar el programa.

* Resulta necesario realizar la [configuración de las variables de entorno](https://www.java.com/es/download/help/path_es.html) para que Java pueda ejecutarse correctamente.

* Si bien es posible desarrollar un programa en Java con un editor de texto, es recomendable utilizar un [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado) (entorno de desarrollo integrado). Algunos de los IDE más utilizados son [Eclipse](https://www.eclipse.org/downloads/), [VS Code](https://code.visualstudio.com/Download) o [IntelliJ Idea](https://www.jetbrains.com/es-es/idea/download/), entre otros. Siempre es necesario revisar la versión de Java instalada en el sistema operativo para que el IDE pueda ejecutarse correctamente.

## Variables

Las variables son un espacio de memoria que generará nuestro programa, donde podemos guardar datos. Se denominan variables porque su contenido puede cambiar.

### Declaración

Java es un lenguaje fuertemente tipado. Cuando necesitamos almacenar algún dato para que nuestro programa lo pueda usar (en una variable), debemos indicar el tipo de dato que esa variable puede almacenar.

Las variables se declaran siguiendo este orden: `TipoDeDato nombreDeVariable;`

```java
/* Declaración de variable en Java
 * int -> tipo de dato
 * espacioParaNumeroVariable -> nombre de la variable
 * La declaración debe terminar con un punto y coma (;)
 */

int espacioParaNumeroVariable;
```

Reglas y convenciones para el nombre de una variable:

* La nomenclatura por convención es [camelCase](https://en.wikipedia.org/wiki/Camel_case): el nombre comienza en minúscula y, si está formado por más de una palabra, cada palabra siguiente comienza con mayúscula. Ejemplo: `cantidadDeFrutas`.
* El nombre no puede ser un número ni comenzar con un número.
* El nombre no puede ser una palabra reservada del lenguaje.
* No pueden existir dos variables con el mismo nombre **dentro del mismo ámbito** (por ejemplo, dentro del mismo método). Dos métodos distintos sí pueden tener, cada uno, una variable llamada `resultado`.

Podemos declarar una variable y asignarle un valor en la misma línea. A esto se lo llama **inicialización**:

```java
// Declaración e inicialización de una variable
int espacioParaNumeroVariable = 10;
```

> **Nota:** en la sección de [operadores](./operadores.html) se explica el funcionamiento del operador igual (=).

**Importante:** una variable local (declarada dentro de un método) debe ser inicializada antes de poder usarse. Si intentamos leerla sin haberle asignado nunca un valor, obtendremos un error de compilación.

### Variables y constantes

Las constantes se parecen a las variables en la forma de declararlas, pero solo pueden contener un dato que, una vez asignado, no podrá cambiarse (será un valor constante).

Para definir una constante debemos incluir la palabra reservada `final`.

La convención de nomenclatura para constantes es [UPPER_SNAKE_CASE](https://es.wikipedia.org/wiki/Snake_case): todas las palabras en mayúscula, separadas con guión bajo (_).

```java
/* Declaración e inicialización de una constante en Java
 * final -> indica que será una constante
 * int -> tipo de dato
 * ESPACIO_PARA_NUMERO_CONSTANTE -> nombre de la constante
 */

final int ESPACIO_PARA_NUMERO_CONSTANTE = 100;
```

Lo habitual es asignarle el valor a la constante en la misma línea en la que la declaramos, tal como en el ejemplo. Si intentamos asignarle un nuevo valor más adelante, obtendremos un error de compilación:

```java
final int ESPACIO_PARA_NUMERO_CONSTANTE = 100;
ESPACIO_PARA_NUMERO_CONSTANTE = 200; // Error de compilación: no se puede reasignar una constante
```

### Dónde viven las variables

Cuando declaramos una variable con un tipo de dato primitivo dentro de un método, Java reserva para ella un espacio en un sector de memoria conocido como pila (Stack Memory). Ese espacio tiene un tamaño fijo, determinado por el tipo de dato, y su contenido puede consultarse y cambiarse mientras la variable exista.

Cuando el método termina, el espacio que ocupaban sus variables se libera automáticamente (queda disponible para otro uso).

La pila funciona con la estructura LIFO (Last In First Out, el último en ingresar es el primero en salir): la última variable declarada es la primera en liberarse. El sector donde se registran las llamadas a métodos en curso se conoce como pila de llamadas (Call Stack).

> **Nota:** los objetos se almacenan de otra manera. Ver [garbage collector](./clases.html#garbage-collector).

## Tipos de datos primitivos

Tipo de dato: representa la unidad de información que las variables pueden almacenar.

[Tipo de dato primitivo](https://es.wikipedia.org/wiki/Tipo_de_dato_elemental): son los tipos de datos más básicos y elementales que un lenguaje de programación tipado nos provee.

La nomenclatura de los tipos de datos primitivos es siempre en minúscula.

### Números enteros

Son tipos de datos que permiten almacenar en una variable o constante números enteros (sin decimales).

El grupo de números enteros está compuesto por los tipos de dato primitivos `byte`, `short`, `int` y `long`.
Cada tipo de dato antes nombrado posee una cantidad de bytes que utiliza para poder representar números. Cuantos más bytes, más grande es el rango de números que puede representar.

| Tipo de dato | Cantidad de bytes | Rango de números posibles de representar                   |
|:-------------|:------------------|:-----------------------------------------------------------|
| byte         | 1                 | -128 hasta 127                                             |
| short        | 2                 | -32.768 hasta 32.767                                       |
| int          | 4                 | -2.147.483.648 hasta 2.147.483.647                         |
| long         | 8                 | -9.223.372.036.854.775.808 hasta 9.223.372.036.854.775.807 |

```java
byte edad = 21;
short cantidadDeAlumnos = 850;
int cantidadDeHabitantesDeUnPais = 46000000;
long cantidadDeHabitantesDelPlaneta = 8100000000L; // La L final es obligatoria: el número no entra en un int
```

> **Importante:** el tipo de dato elegido debe poder representar el número que queremos guardar. `byte edad = 200;` no compila, porque 200 está fuera del rango de `byte`.

Si intentamos guardar un número con decimales en una variable de tipo entero, **no compila**:

```java
int numero = 120.35; // Error de compilación
```

Si realmente queremos quedarnos solo con la parte entera, debemos pedirlo de manera explícita con un *cast* (una conversión):

```java
int numero = (int) 120.35; // El contenido de numero es 120. Los decimales se descartan (no se redondea)
```

### Números con decimales

Son tipos de datos que permiten almacenar en una variable o constante números con decimales. Ejemplo: `120.35`.

El grupo de los números con decimales está compuesto por los tipos de dato primitivos `float` y `double`.
Cada tipo de dato antes nombrado posee una cantidad de bytes que utiliza para poder representar números.

| Tipo de dato | Cantidad de bytes | Rango aproximado de números posibles de representar        |
|:-------------|:------------------|:-----------------------------------------------------------|
| float        | 4                 | -3,4 x 10^38 hasta 3,4 x 10^38                             |
| double       | 8                 | -1,7 x 10^308 hasta 1,7 x 10^308                           |

```java
float pi = 3.1415926535f;
double e = 2.718281828459045235360;
```

> **Nota:** en el código fuente de Java el separador decimal es **siempre** el punto (.), sin importar la configuración regional del sistema operativo. La coma se usa para separar parámetros, nunca decimales.

### Valores de verdad

A diferencia de los tipos de datos primitivos antes nombrados, las variables o constantes que pueden representar valores de verdad (verdadero o falso) solo tienen un tipo: `boolean`.

Las variables o constantes que se definan con el tipo de dato boolean pueden almacenar solo un valor de verdad, representado por las palabras reservadas `true` (verdadero) o `false` (falso).

```java
boolean verdadero = true;
boolean falso = false;
```

### Caracteres

Existe un tipo de dato primitivo que nos permite almacenar un caracter: `char`.
El contenido de una variable o constante de tipo `char` debe escribirse entre comillas simples (').
También es posible asignar un número que represente el caracter deseado según, por ejemplo, la tabla [ASCII](https://elcodigoascii.com.ar/), donde el número `65` equivale al caracter `A` (en mayúscula).

```java
char letraACaracter = 'A';
char letraANumero = 65;
```

Las dos sentencias del ejemplo son equivalentes: ambas variables contienen el caracter `A`.

## Literales

Son los valores que escribimos directamente en el código y que podemos asignar a variables o constantes, dependiendo del tipo de dato que la variable o constante pueda representar.

### Literales de números enteros

Para los tipos de dato primitivos que representan números enteros, el tipo de dato por defecto al escribir un literal (número) es `int`.

```java
// El número 20 es el literal entero
byte edad = 20;
short cantidadDeAlumnos = 20;
int cantidadDeHabitantesDeUnPais = 20;
long cantidadDeHabitantesDelPlaneta = 20;
```

Como el literal es `int`, si el número que necesitamos escribir supera el rango de un `int`, debemos incluir la letra `L` al final para convertirlo en un literal de tipo `long`.

```java
// Literal de tipo long
long cantidadDeHabitantesDelPlaneta = 8100000000L;

// Sin la L, esto es un error de compilación: "integer number too large"
long cantidadDeHabitantesDelPlaneta = 8100000000;
```

### Literales de números decimales

Para los tipos de dato primitivos que representan números con decimales, el tipo de dato por defecto al escribir un literal (número con decimales) es `double`. Por eso, para asignarlo a un `float` debemos agregarle la letra `f` al final.

```java
// La letra f al final del número indica que será un literal de tipo float
float pi = 3.1415926535f;

// Sin la f, esto es un error de compilación: un double no entra en un float
float pi = 3.1415926535;

// Un literal con decimales es double por defecto, así que no necesita ningún sufijo
double e = 2.718281828459045235360;
```

### Literales de caracteres y cadenas

Para asignar un literal de tipo `char` debemos escribir el caracter entre comillas simples.

```java
// 'A' -> literal de tipo char
char letraACaracter = 'A';
```

Java no provee un tipo de dato primitivo para palabras o textos. En su lugar deberemos utilizar la clase `String` (ver [clases](./clases.html) y notar la primera letra en mayúscula). Los literales de tipo `String` deben escribirse entre comillas dobles (").

```java
// "Firulais" -> literal de String
String nombre = "Firulais";
```

## Contador

Un contador es una variable que usamos para llevar la cuenta de cuántas veces ocurre algo. Siempre avanza de a **una unidad**.

```java
int cantidadDeFrutas = 0; // Inicializamos el contador en 0
cantidadDeFrutas = cantidadDeFrutas + 1; // Toma el valor actual de la variable, le suma uno y lo asigna a la misma variable. El nuevo valor es 1
cantidadDeFrutas = cantidadDeFrutas + 1; // El nuevo valor es 2
cantidadDeFrutas += 1; // Forma abreviada de la misma operación, sin repetir el nombre de la variable. El nuevo valor es 3
cantidadDeFrutas++; // Forma aún más breve, exclusiva para sumar uno. El nuevo valor es 4
```

Para contar también podemos utilizar [pre y post incremento o decremento](./operadores.html#operadores-unarios-y-ternarios):

```java
int cantidadDeFrutas = 0; // Inicializamos el contador en 0
++cantidadDeFrutas; // Pre incrementa en 1 el valor de la variable. El nuevo valor es 1
--cantidadDeFrutas; // Pre decrementa en 1 el valor de la variable. El nuevo valor es 0
```

## Acumulador

Un acumulador es una variable que usamos para ir sumando valores que **no son siempre de a uno**. La diferencia con el contador es esa: el contador responde "cuántas veces", el acumulador responde "cuánto en total".

```java
float precioTotal = 0; // Inicializamos el acumulador en 0, porque no afecta a la suma
precioTotal = precioTotal + 1000; // Al valor actual le agrega 1000. El nuevo valor es 1000
precioTotal += 500; // Al valor actual le agrega 500, con la forma abreviada. El nuevo valor es 1500
```

### Formas abreviadas de los operadores aritméticos

Todas las operaciones aritméticas tienen una forma abreviada que evita repetir el nombre de la variable:

```java
int numero = 10;

numero += 5; // Equivale a: numero = numero + 5. El nuevo valor es 15
numero -= 5; // Equivale a: numero = numero - 5. El nuevo valor es 10
numero *= 2; // Equivale a: numero = numero * 2. El nuevo valor es 20
numero /= 2; // Equivale a: numero = numero / 2. El nuevo valor es 10
numero %= 3; // Equivale a: numero = numero % 3. El nuevo valor es 1
```

[Volver](../)
