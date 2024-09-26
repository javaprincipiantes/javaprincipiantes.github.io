---
layout: default
---

[Volver](../)

# Operadores

Los operadores son caracteres que nos permiten realizar diversas operaciones, así como también, manipular los datos en las variables.

## Operadores de asignación

Para asignar un valor a una variable o constante, debemos utilizar el operador igual (=).
El valor presente a la derecha del igual, será asignado como contenido a la variable definida a la izquierda del igual.


```java
// Operador igual para asignar la palabra Firulais a la variable nombre.

String nombre = "Firulais";
```

> **Importante:** Luego de definir una variable, no es válido repetir el tipo de dato en caso de querer cambiar el contenido de la misma.

```java
String nombre = "Firulais";
nombre = "Javier"; // Asignación a variable definida anteriormente
```

## Operadores aritméticos

Son operadores que nos permite realizar operaciones aritméticas como la suma, resta, multiplicación, división y el cálculo del resto.

| Operador | Función                                                                            |
|:---------|:-----------------------------------------------------------------------------------|
| +        | Sumar dos números. En caso de que las variables sean de tipo String, las concatena |
| -        | Restar dos números                                                                 |
| *        | Multiplicar dos números                                                            |
| /        | Dividir dos números                                                                |
| %        | Obtener el resto de la división de dos números                                     |

```java
// Operaciones asignadas a variables.

float precio = 1000 + 500; // valor asignado: 1500
int edad = 2024 - 2000; // Valor asignado: 24
int resto = 10 / 2; // Valor asignado: 0
```

## Operadores unarios y ternarios

Son los operadores que sólo necesitan un operando para funcionar.

| Operador | Función                                                    |
|:---------|:-----------------------------------------------------------|
| +        | Indicar que un número es positivo                          |
| -        | Indicar que un número es negativo                          |
| ++       | Incrementar el valor de una variable en 1                  |
| \-\-     | Decrementar el valor de una variable en 1                  |
| !        | Invertir el valor boolean de una variable de tipo boolean  |

```java
// Operadores unarios y variables.

float precio = 1000 + 500; // valor asignado: 1500
precio = -precio; // valor asignado: -1500 
boolean existe = true; // Valor asignado: true
existe = !existe; // Valor asignado: false
```
> **Nota:** Los operadores antepuestos antes del valor, no cambian el contenido original de la variable. Solo la asignación reemplaza el contenido de la variable.

* Pre y post incremento o decremento

Al anteponer los operadores `++` o `--` antes de o después de variables enteras (por ejemplo), pre incrementa (o decrementa) o post incrementa (o decrementa) el valor de la variable según corresponda.

Al pre incrementar o decrementar, primero se actualiza el valor la variable y luego se utiliza el mismo. Por su contrario, al post incrementar o decrementar, primero se usa el valor de la variable, para luego realizar la tarea.

```java
int cantidad = 1; // valor asignado: 1
int resultado = ++cantidad; // valor asignado: 2
resultado = cantidad++; // valor asignado: 2. El valor de la variable cantidad, luego de esta sentencia será 3

resultado = --cantidad; // valor asignado: 2
resultado = cantidad--; // valor asignado: 2. El valor de la variable cantidad, luego de esta sentencia será 1
```

## Operadores de igualdad y relacionales

Son los operadores que, principalmente, nos permiten comparar el contenido de dos variables (por ejemplo). La comparación siempre devuelve un valor de verdad (true o false).

| Operador | Descripción             |
|:---------|:------------------------|
| ==       | Igual a                 |
| !=       | No igual a (o distinto) |
| >        | Mayor que               |
| >=       | Mayor o igual que       |
| <        | Menor que               |
| <=       | Menor o igual que       |

```java
int edad = 21 
edad == 21      // true
edad != 21      // false
edad > 21       // false
edad >= 21      // true
edad < 21       // false
edad <= 21      // true
```

## Operadores lógicos

Son los operadores que nos permiten evaluar más de una expresión booleana.

| Operador   | Descripción                  |
|:-----------|:-----------------------------|
| &&         | Operador condicional AND (y) |
| \|\|       | Operador condicional OR (o)  |
| ?:         | Operador ternario            |
| instanceof | Operador instanceof          |


* AND y OR

Los operadores `&&` y `||` nos permiten evaluar mas de una expresión booleana. Mientras que el operador ternario y el operador `instanceof`, funcionan de manera distinta.

Cuando utilizamos `&&` necesitamos que todas las expresiones booleanas implicadas sean verdaderas para obtener true como último valor.

Cuando utilizamos `||` necesitamos que al menos una de las expresiones booleanas implicadas sea verdadera para obtener true como último valor.

```java
int edad = 25 
edad > 20 && edad < 30 // El contenido de la variable edad es mayor a 20 y, además es menor a 30. El resultado es true.
edad == 25 || edad == 30 // El contenido de la variable edad es igual a 25, pero no es igual a 30. El resultado es true.

edad > 20 && edad < 23 // El contenido de la variable edad es mayor a 20, pero no es menor que 23. El resultado es false.
edad < 25 || edad == 30 // El contenido de la variable edad no es menor a 25 y tampoco es igual a 30. El resultado es false.
edad < 20 || edad == 25 // El contenido de la variable edad no es menor a 20 pero si es igual a 25. El resultado es true.
```

Cuando utilizamos `&&`, si la primera expresión es **false**, no continua evaluando las demás expresiones (todas deben ser true).

Cuando utilizamos `||`, si la primera expresión es **false**, continua evaluando las demaás expresiones (al menos necesita que una sea true).

* Operador ternario

El operador ternario es un operador condicional (ver [estructuras](./estructuras.html)).
Evalua una expresión y en caso de cumplirse (ser true) permite realizar una acción, caso contrario (ser false), permite realizar otra accion. En general se utiliza con asignaciones.

La forma de utilizarlo es evaluando una expresión, y luego con el caracter `?` (caso verdadero) podemos definir que se asigna si se cumple dicha expresión. Con el caracter `:` (caso falso) podremos asignar algo, en caso de que la expresión no se cumpla.

```java
int edad = 25;
String mayorA25 = edad > 25 ? "Si" : "No"; // A la variable mayorA25 se asigna "No".
```

* Operador instanceof

El operador `instanceof` es especial, nos permite identificar si un objeto es de una clase en específico (ver [clases](./clases.html#Objetos)). 

```java
String nombre = "Firulais";

nombre instanceof String; // true
```

[Volver](../)