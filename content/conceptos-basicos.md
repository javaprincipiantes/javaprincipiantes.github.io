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

* Dentro de cada source folder, los archivos se deben agrupar en paquetes (packages). La forma de agruparlos deberá responder por la estructura o arquitectura del proyecto que adoptemos. La nomenclatura de un package por convención es: com.empresa.dominio. Se escribe desde lo más general (com) hasta lo más específico, siempre utilizando palabras en minúscula y separadas por puntos (.). En caso de tener un nombre compuesto como "Mi proyecto", se debe escribir como: com.miproyecto.dominio.

* El código fuente se escribe dentro de archivos con extensión .java. Muchos archivos con dicha extensión, las source folders y los paquetes, conforman el código fuente.

* Java posee palabras reservadas como: (public, private, int, return, final, entre otras) las cuales no podremos utilizar para definir, por ejemplo, variables.

* Es posible incluir comentarios de utilidad para el desarrollador. Para realizar esto se deberá utilizar dos barras (// Comentario) lo cual creará un comentario 
de una sola línea, o bien, barra asterisco - asterisco barra (/* líneas comentadas */) para comentar en múltiples líneas.

* Es posible comentar código que podría ejecutarse. El código comentado, no será tenido en cuanta a la hora de ejecutar el programa.

* Resulta necesario realizar la [configuración de las variables de entorno](https://www.java.com/es/download/help/path_es.html) para que Java pueda ejecutarse correctamente.

* Si bien es posible desarrollar un programa en Java con un editor de texto, es recomendable utilizar un [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado) (entorno de desarrollo integrado). Algunos de los IDE's mas utilizados son: [Eclipse](https://www.eclipse.org/downloads/), [VS Code](https://code.visualstudio.com/Download) o [IntelliJ Idea](https://www.jetbrains.com/es-es/idea/download/), entre otros. Siempre es necesario revisar la versión de Java instalada en el sistema operativo para que el IDE pueda ejecutarse correctamente.

## Variables

### Variables y constantes

* Las variables son un espacio de memoria que generará nuestro programa, donde podemos guardar datos.

Java es un lenguaje fuertemente tipado, con lo cual, cuando determinamos que necesitamos almacenar algún dato para que nuestro programa lo pueda usar (en una variable), debemos indicar el tipo de dato que puede almacenar.

La nomenclatura de variables por convensión es [camelCase](https://en.wikipedia.org/wiki/Camel_case), debiendo comenzar el nombre de la variable en minúscula (así como toda la palabra), y si existe una segunda palabra, esta última comenzará con la primera letra en mayúscula.

Las variables deben definirse siguiendo el siguiente orden: TipoDeDato nombreDeVariable;

Se denominan variables, porque puede cambiar su contenido.

El nombre de una variable no puede ser o comenzar con un número/s.

No pueden existir dos variables con el mismo nombre.

 Cuando definimos una variable con tipo de dato primitivo, Java la crea en un lugar conocido como pila en memoria (Stack Memory), esta porción de memoria reservada para esa variable es estática y, puede tanto consultarse como cambiarse el dato almacenado en esa porción de memoria. Luego, cuando esta variable no se utiliza más (por terminar el programa por ejemplo), esa pila en memoria se limpia (la memoria es liberada para que pueda ser utilizada para otro fin).
 
 Estas variables son creadas según el orden en las que las definimos en nuestro programa siguiendo la estructura LIFO (Last In First Out, el último en ingresar es el primero en salir). El sector donde se almacenan estas instrucciones es conocido como pila de llamadas (Call Stack).

```java
/* Definición de variable en Java
 * int -> tipo de dato
 * numero -> nombre de la variable
 * La definición debe terminar con un punto y coma (;)
 */

int espacioParaNumeroVariable;
```

* Las constantes, son parecidas a las variables (en cómo definirlas), pero en cambio, sólo pueden contener un dato el cual una vez asignado, no podrá cambiarse (será un valor constante).

Para definir una constante debemos incluir la palabra reservada `final`.

La convensión de nomenclatura para constantes es [snake_case](https://es.wikipedia.org/wiki/Snake_case), debiendo escribir todas las palabras en mayúscula, separándolas con guión bajo (_). 

```java
/* Definición de una constante en Java
 * final -> indica que será una constante
 * int -> tipo de dato
 * ESPACIO_PARA_NUMERO_CONSTANTE -> nombre de la constante
 */

final int ESPACIO_PARA_NUMERO_CONSTANTE;
```

Tanto las variables como las constantes pueden definirse asignando un valor en la misma línea (inicialización de variable o constante):
```java
// Definición e inicialización de variable y constante

int espacioParaNumeroVariable = 10;
final int ESPACIO_PARA_NUMERO_CONSTANTE = 100;
```
> **Nota:** en la sección de [operadores](./operadores.html) se explica el funcionamiento del operador igual (=).

## Tipos de datos primitivos

Tipo de dato: Representa la unidad de información que las variables pueden almacenar.

[Tipo de dato primitivo](https://es.wikipedia.org/wiki/Tipo_de_dato_elemental#:~:text=Se%20llama%20tipo%20primitivo%20o,Char%20(Car%C3%A1cter)): son los tipos de datos mas básicos y elementales que un lenguaje de programación tipado nos provee.

La nomenclatura de los tipos de datos primitivos es siempre en minúscula.

### Números enteros

Son tipos de datos que permiten almacenar en una variable o constante, números enteros (sin decimales). Esto nos indica que si un número es, por ejemplo, `120,35`, la variable o constante solo puede almacenar el número `120`. Los decimales se perderán.

El grupo de números enteros está compuesto por los tipos de dato primitivos `byte`, `short`, `int` y `long`.
Cada tipo de dato antes nombrado, posee una cantidad de bytes que utiliza para poder representar números.

| Tipo de dato | Cantidad de bytes | Rango de números posibles de representar                   |
|:-------------|:------------------|:-----------------------------------------------------------|
| byte         | 1                 | -128 hasta 127                                             |
| short        | 2                 | -32768 hasta 32167                                         |
| int          | 4                 | –2.147.483.648 hasta 2.147.483.647                         |
| long         | 8                 | –9.223.372.036.854.775.808 hasta 9.223.372.036.854.775.807 |

```java
byte edad = 21;
short cantidadDePuertas = 30000;
int cantidadDePersonasUnPais = 46000000;
long cantidadDePersonasEnUnPais = 7951000000000;
```

### Números con decimales

Son tipos de datos que permiten almacenar en una variable o constante, números con decimales. Ejemplo: `120,35`.

El grupo de los números con decimales está compuesto por los tipos de dato primitivos `float` y `double`.
Cada tipo de dato antes nombrado, posee una cantidad de bytes que utiliza para poder representar números.

| Tipo de dato | Cantidad de bytes | Rango aproximado de números posibles de representar        |
|:-------------|:------------------|:-----------------------------------------------------------|
| float        | 4                 | -3,4 x 10^38 hasta 3,4 x 10^38                             |
| double       | 8                 | -3,4 x 10^308 hasta 3,4 x 10^308                           |

```java
float pi = 3.1415926535f; 
double e = 2.718281828459045235360;
```

> **Nota:** Según la configuración regional o de idioma, puede utilizarse el punto (.) o la coma (,) para indicar el inicio de los decimales. Lo habitual es usar el punto (.).

### Valores de verdad

A diferencia de los tipos de datos primitivos antes nombrados, las variables o constantes que pueden representar valores de verdad (verdadero o falso) solo tienen un tipo: `boolean`.

Las variables o constantes que se definan con el tipo de dato boolean pueden almacenar solo un valor de verdad, representado por las palabras reservadas `true` (verdadero) o `false` (falso).

```java
boolean verdadero = true;
boolean falso = false;
```

### Caracteres

Existe un tipo de dato primitivo que nos permite almacenar un caracter. Dicho tipo de dato primitivo es `char`.
El contenido de la variable o constante para caracteres, debe utilizarse entre comillas simples (').
Es posible asignar un número que represente el caracter deseado, según (por ejemplo), la tabla [ASCII](https://elcodigoascii.com.ar/), donde por ejemplo el número `65` equivale al caracter `A` (en mayúscula).

```java
char letraACaracter = 'A';
char letraANumero = 65;
```

Las sentencias del ejemplo son equivalentes.

## Literales

Son valores posibles de asignar a variables o constantes, dependiendo del tipo de dato que la variable o constante pueda representar.

### Literales de números enteros

Para los tipos de dato primitivos que representan números enteros, el tipo de dato por defecto al escribir un literal (número) es `int`.

```java
// El número 20 es el literal entero
byte edad = 20;
short cantidadDePuertas = 20;
int cantidadDePersonasUnPais = 20;
long cantidadDePersonasEnUnPais = 20;
```

Para crear un literal de tipo long, se debe incluir la letra `L` al final del número.

```java
// Literal de tipo long
long cantidadDePersonasEnUnPais = 20L;
```

### Literales de números decimales

Para los tipos de dato primitivos que representan números con decimales, el tipo de dato por defecto al escribir un literal (número con decimales) es `double`.

```java
// La letra f al final del número indica que será un literal de tipo float
float pi = 3.1415926535f;
double e = 2.718281828459045235360;
```

### Literales de caracteres y cadenas

Para asignar un literal de tipo `char` debemos utilizar el caracter entre comillas simples (sin espacios intermedios).

```java
// 'A' -> literal de tipo char
char letraACaracter = 'A';
```

Java no provee un tipo de dato primitivo para palabras o textos. En su lugar deberemos utilizar la clase `String` (ver [clases](./clases.html) y notar la primera letra en mayúscula). Los literales de tipo `String` deben representarse entre comillas dobles (").

```java
// "Firulais" -> literal de String
String nombre = "Firulais";
```

## Contador

Posiblemente necesitemos en alguna operación contar. Para realizar esta tarea, podemos incluir sentencias de código como las siguientes.

```java
int numero = 0; // Definición e inicialización de variable de tipo int inicializada (su contenido es) con valor 0
numero = numero + 1; // Utiliza el valor actual de la variable número, le suma uno y la asigna a la misma variable. El nuevo dato o valor de numero es 1
numero = numero + 1; // El nuevo dato o valor de numero es 2.
numero += 1; // Forma simplificada de realizar la misma operación (sumar uno), sin necesidad de repetir el nombre de la variable. El nuevo dato o valor de numero es 3

numero -= 1; // Es posible de representar con la forma simplificada, las operaciones con los demás opeadores aritméticos. El nuevo dato o valor de numero es 2
numero *= 2; // El nuevo dato o valor de numero es 4
numero /= 2; // El nuevo dato o valor de numero es 2
```

Para contar podemos también utilizar [pre y post incremento o decremento](./operadores.html#operadores-unarios-y-ternarios):

```java
int numero = 0; // Definición e inicialización de variable de tipo int inicializada (su contenido es) con valor 0
++numero; // Pre incrementa en 1 el dato o valor de la variable numero. El nuevo dato o valor es 1
--numero; // Pre decrementa en 1 el dato o valor de la variable numero. El nuevo dato o valor es 0
```

## Acumulador

En ocasiones, podemos necesitar acumular valores que no sean de uno en uno. Para esto aplicaremos el concepto de acumulador.

```java
float precio = 1000;
precio = precio + 500; // Al dato o valor de la variable precio le agrega 500
precio += 500; // Al dato o valor de la variable precio le agrega 500, con la forma simplificada
```

[Volver](../)