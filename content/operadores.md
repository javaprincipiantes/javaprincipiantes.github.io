---
layout: default
---

[Volver](../)

# Operadores

Los operadores son símbolos que nos permiten realizar diversas operaciones, así como también manipular los datos en las variables.

## Operadores de asignación

Para asignar un valor a una variable o constante debemos utilizar el operador igual (=).
El valor presente a la derecha del igual será asignado como contenido a la variable definida a la izquierda del igual.

```java
// Operador igual para asignar la palabra Firulais a la variable nombre

String nombre = "Firulais";
```

> **Importante:** el tipo de dato se escribe una sola vez, cuando declaramos la variable. Si más adelante queremos cambiar su contenido, no debemos repetirlo.

```java
String nombre = "Firulais";
nombre = "Javier"; // Asignación a una variable declarada anteriormente
```

Cada operador aritmético tiene además una forma abreviada de asignación (`+=`, `-=`, `*=`, `/=`, `%=`). Ver [formas abreviadas](./conceptos-basicos.html#formas-abreviadas-de-los-operadores-aritméticos).

## Operadores aritméticos

Son operadores que nos permiten realizar operaciones aritméticas como la suma, la resta, la multiplicación, la división y el cálculo del resto.

| Operador | Función                                                                            |
|:---------|:-----------------------------------------------------------------------------------|
| +        | Sumar dos números. En caso de que alguno de los operandos sea un String, los concatena |
| -        | Restar dos números                                                                 |
| *        | Multiplicar dos números                                                            |
| /        | Dividir dos números                                                                |
| %        | Obtener el resto de la división de dos números                                     |

```java
// Operaciones asignadas a variables

float precio = 1000 + 500;   // Valor asignado: 1500
int edad = 2024 - 2000;      // Valor asignado: 24
int total = 12 * 3;          // Valor asignado: 36
int mitad = 10 / 2;          // Valor asignado: 5
int resto = 10 % 3;          // Valor asignado: 1 (10 dividido 3 da 3, y sobra 1)
```

> **Importante: la división entre enteros es entera.** Si los dos operandos son de un tipo entero (`byte`, `short`, `int`, `long`), el resultado también es entero y los decimales se descartan, aunque el resultado se asigne a una variable con decimales.

```java
int resultadoEntero = 5 / 2;       // Valor asignado: 2, no 2.5
double resultadoMalCalculado = 5 / 2;   // Valor asignado: 2.0. La división ya se resolvió entre enteros
double resultadoCorrecto = 5.0 / 2;     // Valor asignado: 2.5. Al menos uno de los operandos tiene decimales
```

El operador `%` (resto o módulo) es muy útil para saber si un número es múltiplo de otro:

```java
int numero = 8;
boolean esPar = numero % 2 == 0; // true, porque el resto de dividir 8 por 2 es cero
```

## Operadores unarios y ternarios

Los operadores **unarios** son los que necesitan un solo operando para funcionar.

| Operador | Función                                                    |
|:---------|:-----------------------------------------------------------|
| +        | Indicar que un número es positivo                          |
| -        | Invertir el signo de un número                             |
| ++       | Incrementar el valor de una variable en 1                  |
| \-\-     | Decrementar el valor de una variable en 1                  |
| !        | Invertir un valor de verdad (de true a false y viceversa)  |

```java
// Operadores unarios y variables

float precio = 1000 + 500; // Valor asignado: 1500
precio = -precio;          // Valor asignado: -1500
boolean existe = true;     // Valor asignado: true
existe = !existe;          // Valor asignado: false
```

> **Nota:** `-precio` y `!existe` calculan un valor nuevo, pero por sí solos no modifican la variable. Es la asignación (`precio = ...`) la que reemplaza su contenido. La excepción son `++` y `--`, que sí modifican la variable sobre la que se aplican.

* Pre y post incremento o decremento

Al anteponer o posponer los operadores `++` o `--` a una variable entera, pre incrementamos (o decrementamos) o post incrementamos (o decrementamos) el valor de la variable, según corresponda.

Al **pre** incrementar o decrementar, primero se actualiza el valor de la variable y luego se utiliza el valor ya actualizado. Por el contrario, al **post** incrementar o decrementar, primero se utiliza el valor actual y recién después se actualiza la variable.

```java
int cantidad = 1;
int resultado = ++cantidad; // Primero incrementa (cantidad pasa a 2) y después asigna. resultado: 2, cantidad: 2
resultado = cantidad++;     // Primero asigna (2) y después incrementa. resultado: 2, cantidad: 3

resultado = --cantidad;     // Primero decrementa (cantidad pasa a 2) y después asigna. resultado: 2, cantidad: 2
resultado = cantidad--;     // Primero asigna (2) y después decrementa. resultado: 2, cantidad: 1
```

El **operador ternario** es el único operador de Java que necesita tres operandos, y por eso lleva ese nombre. Está explicado más abajo, junto a los [operadores condicionales](#operadores-condicionales).

## Operadores de igualdad y relacionales

Son los operadores que nos permiten comparar dos valores. La comparación siempre devuelve un valor de verdad (`true` o `false`).

| Operador | Descripción             |
|:---------|:------------------------|
| ==       | Igual a                 |
| !=       | No igual a (o distinto) |
| >        | Mayor que               |
| >=       | Mayor o igual que       |
| <        | Menor que               |
| <=       | Menor o igual que       |

```java
int edad = 21;

boolean esIgualA21     = edad == 21; // true
boolean esDistintoDe21 = edad != 21; // false
boolean esMayorA21     = edad > 21;  // false
boolean esMayorOIgualA21 = edad >= 21; // true
boolean esMenorA21     = edad < 21;  // false
boolean esMenorOIgualA21 = edad <= 21; // true
```

> **Importante:** `==` compara el contenido solo cuando trabajamos con tipos de dato **primitivos**. Con objetos (por ejemplo un `String`) compara si las dos variables apuntan al mismo objeto en memoria, no si tienen el mismo contenido. Para comparar el contenido de dos objetos se usa el método `equals()`.

```java
String nombre = "Firulais";
String otroNombre = new String("Firulais"); // Creamos un objeto String nuevo, con el mismo contenido

boolean sonElMismoObjeto = nombre == otroNombre;        // false: son dos objetos distintos en memoria
boolean tienenElMismoTexto = nombre.equals(otroNombre); // true: el contenido es el mismo. Esta es la forma correcta
```

Esta distinción es una de las principales fuentes de errores para quien empieza: **con `String` y con cualquier objeto, usá siempre `equals()`**.

## Operadores lógicos

Son los operadores que nos permiten combinar más de una expresión booleana en una sola.

| Operador   | Descripción                  |
|:-----------|:-----------------------------|
| &&         | Operador condicional AND (y) |
| \|\|       | Operador condicional OR (o)  |
| !          | Operador de negación NOT (no) |

Cuando utilizamos `&&` necesitamos que **todas** las expresiones booleanas implicadas sean verdaderas para obtener `true` como resultado final.

Cuando utilizamos `||` necesitamos que **al menos una** de las expresiones booleanas implicadas sea verdadera para obtener `true` como resultado final.

```java
int edad = 25;

boolean estaEnLaFranja  = edad > 20 && edad < 30;  // La edad es mayor a 20 y además menor a 30. Resultado: true
boolean esVeinticincoOTreinta = edad == 25 || edad == 30; // La edad es igual a 25 (no hace falta que también sea 30). Resultado: true

boolean casoUno   = edad > 20 && edad < 23;  // Es mayor a 20, pero no es menor que 23. Resultado: false
boolean casoDos   = edad < 25 || edad == 30; // No es menor a 25 y tampoco es igual a 30. Resultado: false
boolean casoTres  = edad < 20 || edad == 25; // No es menor a 20, pero sí es igual a 25. Resultado: true
```

* Evaluación en cortocircuito

Ambos operadores dejan de evaluar apenas conocen el resultado final. A esto se lo llama evaluación en cortocircuito.

Cuando utilizamos `&&`, si una expresión es **false**, el resultado final ya no puede ser `true`, así que no se evalúan las expresiones siguientes.

Cuando utilizamos `||`, si una expresión es **true**, el resultado final ya no puede ser `false`, así que no se evalúan las expresiones siguientes.

```java
int cantidad = 0;

// La segunda expresión nunca se evalúa, porque la primera ya es false
boolean resultado = cantidad > 10 && cantidad < 100;
```

Esto es muy útil para evitar errores: si la primera expresión verifica que algo se puede usar, la segunda solo se evalúa cuando esa verificación pasó.

## Operadores condicionales

* Operador ternario

El operador ternario es un operador condicional (ver [estructuras](./estructuras.html)).
Evalúa una expresión y, en caso de cumplirse (ser `true`), devuelve un valor; en caso contrario (ser `false`), devuelve otro. En general se utiliza en asignaciones.

La forma de utilizarlo es escribir la expresión a evaluar, luego el caracter `?` seguido del valor para el caso verdadero, y luego el caracter `:` seguido del valor para el caso falso.

```java
int edad = 25;
String esMayorA25 = edad > 25 ? "Si" : "No"; // A la variable esMayorA25 se le asigna "No"
```

Es una forma abreviada de escribir esto:

```java
int edad = 25;
String esMayorA25;

if (edad > 25) {
    esMayorA25 = "Si";
} else {
    esMayorA25 = "No";
}
```

## Precedencia de operadores

Cuando una expresión combina varios operadores, no se resuelven de izquierda a derecha: cada operador tiene una **precedencia** que determina cuál se resuelve primero. Es la misma idea que en matemática, donde la multiplicación se resuelve antes que la suma.

```java
int resultado = 2 + 3 * 4; // 14, no 20: primero se resuelve 3 * 4 y después se suma 2
```

De mayor a menor precedencia, los operadores que vimos se agrupan así:

| Precedencia | Operadores                  |
|:------------|:----------------------------|
| 1 (mayor)   | `()` paréntesis             |
| 2           | `++` `--` `!` unarios       |
| 3           | `*` `/` `%`                 |
| 4           | `+` `-`                     |
| 5           | `<` `<=` `>` `>=` `instanceof` |
| 6           | `==` `!=`                   |
| 7           | `&&`                        |
| 8           | `\|\|`                      |
| 9           | `?:` ternario               |
| 10 (menor)  | `=` `+=` `-=` `*=` `/=` `%=` |

Que los operadores relacionales tengan más precedencia que los lógicos es lo que permite escribir una condición sin paréntesis:

```java
int edad = 25;

// Primero se resuelven las dos comparaciones y después el &&
boolean estaEnLaFranja = edad > 20 && edad < 30;
```

Y que la asignación sea la de menor precedencia es lo que permite que toda la expresión de la derecha se resuelva antes de asignarse.

Donde sí conviene prestar atención es al mezclar `&&` con `||`, porque `&&` se resuelve primero:

```java
boolean esFinDeSemana = false;
boolean esFeriado = true;
boolean hayTrabajoPendiente = true;

// Se interpreta como: esFinDeSemana || (esFeriado && hayTrabajoPendiente)
boolean resultado = esFinDeSemana || esFeriado && hayTrabajoPendiente; // true
```

> **Recomendación:** no hace falta memorizar la tabla. Ante la menor duda, **usá paréntesis**: no cambian el resultado cuando el orden ya era el correcto, y vuelven la intención explícita para quien lea el código.

```java
// La misma expresión, con la intención escrita de manera explícita
boolean resultado = esFinDeSemana || (esFeriado && hayTrabajoPendiente);

// Y si lo que queríamos era lo otro, los paréntesis son imprescindibles
boolean otroResultado = (esFinDeSemana || esFeriado) && hayTrabajoPendiente;
```

## Operador instanceof

El operador `instanceof` nos permite identificar si un objeto es de una clase en específico (ver [objetos](./clases.html#objetos)). Devuelve un valor de verdad.

```java
String nombre = "Firulais";

boolean esUnString = nombre instanceof String; // true
```

[Volver](../)
