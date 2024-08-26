---
layout: default
---

[Volver](../)

# Estructuras

Como muchos lenguajes de programación, Java nos provee de ciertas estructuras definidas que nos permiten realizar distintas tareas. Estas estructuras poseen sus propias palabras reservadas que utilizaremos para definirlas y utilizarlas.

## Estructuras de decisión

### if-else

Es una estructura que nos permite evaluar una o varias expresiones booleanas.
La palabra reservada para definirla es **if** y seguido a esta palabra reservada, debemos indicar la expresión (o expresiones) que se evaluarán para determinar que debemos hacer. 

`if (expresion1 && expresion2)`

La estructura se completa con dos llaves, una de apertura y otra de cierre ({ }). Estas llaves nos indican las sentencias de código que deberán ejecutarse en caso de que el resultado de todas la expresiones incluidas entre los paréntesis (luego del if), sean verdaderas (true).

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

//                      true como valor final
//              true     &&                 true
if (cantidadDeFrutas > 1 && cantidadDeFrutas < 10) {
    // Sentencias que se ejecutan cuando el valor final de las expresiones evaluadas es true
    hayFrutasSuficientes = true; // La cantidad de frutas está compendida entre el rango (1-10), con lo cual, asignamos true a la variable hayFrutasSuficientes.
}

```

Cuando sólo tenemos una línea dentro de las llaves de la estructura if, podemos no escribir las llaves.

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

if (cantidadDeFrutas > 1 && cantidadDeFrutas < 10) 
    hayFrutasSuficientes = true; // La cantidad de frutas está compendida entre el rango 1-10, con lo cual, asignamos true a la variable hayFrutasSuficientes.

```

En caso de existir más de una línea o sentencia a ejecutar, se deben incluir las llaves de manera obligatoria.

La estructura **if** cuenta con otro bloque adicional (no obligatorio) que nos permite ejecutar sentencias en caso de que la expresión (o expresiones del if) no se cumplan. Para ello, debemos incluir la palabra reservada **else** luego de la llave de cierre del caso verdadero del if.

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

//                      false como valor final
//              false     &&                 false
if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
    // Sentencias que se ejecutan cuando el valor final de las expresiones evaluadas es true. En este caso, estas sentencias no se ejecutan.
    hayFrutasSuficientes = true;
} else {
    // Sentencias que se ejecutan cuando el valor final de las expresiones evaluadas es false.
    hayFrutasSuficientes = false; // La cantidad de frutas no satisface a las expresiones que evalua el if. Se ejecutan las sentencias del bloque else.
}

```

Al igual que con las llaves del **if**, si el bloque **else** solo tiene una línea, se puede evitar escribir las llaves. Si las sentencias a ejecutar son más de una, se deben incluir las llaves de manera obligatoria.


```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

//                      false como valor final
//              false     &&                 false
if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) 
    // Sentencias que se ejecutan cuando el valor final de las expresiones evaluadas es true. En este caso, estas sentencias no se ejecutan.
    hayFrutasSuficientes = true;
else 
    // Sentencias que se ejecutan cuando el valor final de las expresiones evaluadas es false.
    hayFrutasSuficientes = false; // La cantidad de frutas no satisface a las expresiones que evalua el if. Se ejecutan las sentencias del bloque else.

```

**Dato:** Los comentarios no representan sentencias de código ejecutables.

Es posible incluir un nuevo **if** luego de su **else** si es que necesitamos evaluar una nueva expresión, si y solo si, la primera expresión no se cumple.

```java
int cantidadDeFrutas = 5;
boolean hayFrutasSuficientes = false; 

if (cantidadDeFrutas == 1) {
    hayFrutasSuficientes = false;
} else if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
    hayFrutasSuficientes = true;
} else {
    // Alguna otra sentencia
}

```

Podemos usar la cantidad de if-else que necesitemos.

Además, es posible incluir (anidar) un if, dentro de otro if (aunque no es muy recomendable).

```java
int cantidadDeFrutas = 5;
boolean hayFrutasSuficientes = false; 

if (cantidadDeFrutas > 1) {
    // Entra por ser verdadero
    
    if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
        hayFrutasSuficientes = true; // Ejecuta esta sentencia por tener la cantidad de frutas necesarias.
    }
} 

```

### switch

La estructura de decisión múltiple (switch), nos permite evaluar el contenido de una variable y así poder ejecutar sentencias de código según el caso que aplique.

La palabra reservada será **switch** y también está acompañada de dos paréntesis donde debemos colocar alguna variable (no expresiones lógicas). 

Luego, con la palabra reservada **case** podremos indicar los distintos casos posibles para determinar las sentencias se deberán ejecutar. Para indicar que un caso termina, se debe incluir la palabra reservada **break**. 

En caso de no incluir esta sentencia, la ejecución continuará en "modo cascada" sin importar los casos, hasta que se encuentre un **break**. Esto nos permite "agrupar" casos.

Switch nos provee de una palabra reservada para ejecutar sentencias en caso de que ningun valor (de la variable evaluada) determinado en cada caso aplique. Esta palabra reservada es **default**.

```java
int diaDeLaSemana = 1; // Domingo
String nombreDelDia = ""; // Inicializamos la variable con vacío

switch(diaDeLaSemana) {
    case 1:
        nombreDelDia = "Domingo";
        break;
    case 2:
        nombreDelDia = "Lunes";
        break;
    case 3:
        nombreDelDia = "Martes";
        break;
    case 4:
        nombreDelDia = "Miércoles";
        break;
    case 5:
        nombreDelDia = "Jueves";
        break;
    case 6:
        nombreDelDia = "Viernes";
        break;
    case 7:
        nombreDelDia = "Sábado";
        break;
    default:
        nombreDelDia = "Día inexistente"; // Esta sentencia se ejecuta si el contenido de la variable diaDeLaSemana no aplica a alguno de los casos anteriores
}
```

En general usamos **switch** cuando no debemos evaluar expresiones y contamos con mas de 2 casos.

Ejemplo de agrupación de casos:

```java
int diaDeLaSemana = 1; // Domingo
boolean seTrabaja;

switch(diaDeLaSemana) {
    case 2:
    case 3:
    case 4:
    case 5:
    case 6:
        seTrabaja = true;
        break;
    case 1:
    case 7:
        seTrabaja = false;
        break;
}
```

Si no necesitamos tener sentencias por defecto (que no apliquen en los casos definidos), podemos incluir la palabra reservada **default**.

Lo más habitual es evaluar el contenido de variables de tipos de dato entero o char. Desde la versión 1.7 de Java, se permite evaluar el contenido de variables de tipo String.

## Estructuras de iteración (bucles)

Las estructuras de iteración definidas a continuación, nos permitirán ejecutar una o varias sentencias de código tantas veces como necesitemos.

### while

Esta estructura, de palabra reservada **while** nos permite evaluar distintas expresiones lógicas (incluidas entre paréntesis) que determinarán cuantas veces se debe ejecutar el código (o sentencias) comprendido entre sus llaves (en caso de que la expresion o expresiones sean verdaderas).

La estructura **while** suele utilizarse cuando no tenemos claro cuantas iteraciones debemos realizar (dependen de una o varias expresiones lógicas).

```java
int cantidadDeFrutas = 0;

while (cantidadDeFrutas < 10) {
    cantidadDeFrutas++; // Se post incrementa el valor de la variable cantidadDeFrutas. Esta sentencia se ejecuta mientras la cantidad de frutas sea menor a 10.
}
```

Al igual que para la estructura if, es posible evitar las llaves si solo se debe ejecutar una sentencia.

```java
int cantidadDeFrutas = 0;

while (cantidadDeFrutas < 10)
    cantidadDeFrutas++; // Se post incrementa el valor de la variable cantidadDeFrutas. Esta sentencia se ejecuta mientras la cantidad de frutas sea menor a 10.
```
**Importante:** Es necesario tener presente que el valor de la variable cantidadDeFrutas debe cambiar de manera que la expresión pueda, en algún momento, ser falsa y así terminar la iteración. En caso de que esto no suceda, entraremos en una iteración infinita.

Es posible incluir más de una expresión usando operadores lógicos.

```java
int cantidadDeFrutas = 0;

while (cantidadDeFrutas >= 0 && cantidadDeFrutas < 10) {
    cantidadDeFrutas++; // Se post incrementa el valor de la variable cantidadDeFrutas. Esta sentencia se ejecuta mientras la cantidad de frutas sea menor a 10.
}
```

Una forma de entender esta estructura es pensar: Ejecuta este bloque (o conjunto de sentencias) mientras esto (expresiones) ocurra.

### do-while

Esta estructura es similar a la estructura **while** con la diferencia que, nos permite ejecutar al menos una sentencia una vez. Se deben incluir las palabras reservadas **do** seguido de las llaves que incluyen las sentencias que se deben ejecutar y luego la palabra reservada **while** con las expresiones necesarias para definir hasta cuando iterar (entre paréntesis).

```java
int numeroValido = 0;

do {
    ++numeroValido; // Se pre incrementa el contenido de la variable al menos una vez
} while (numeroValido <= 3); 

```

Para entender mejor, es válido considerar lo siguiente: Ejecutá las sentencias, mientras no se cumpla la expresión definida en el while.

Es la estructura de iteración mas utilizada para validaciones.

### for

Es la estrcutura de iteración que se suele utilizar cuando conocemos exactamente cuantas veces debemos iterar. Su palabra reservada es **for** y viene acompañada de paréntesis que incluyen sentencias para controlar la iteración.

Dichas sentencias están separadas en tres bloques: variable con valor inicial (desde), expresión de fin (hasta) y cómo incrementar la variable con valor inicial. Estos bloques se separan con punto y coma (;). Incluye llaves que indican las sentencias que se deben ejecutar en cada iteración. Si la sentencia a ejecutar es única, pueden no incluirse las llaves.

```java
int valorInicial = 0;

//        desde                    hasta       cómo se incrementa (en este ejemplo, de 1 en 1)
for (valorInicial = 1; valorInicial <= 10; valorInicial++) {
    // Sentencias a ejecutar
}

```

Es posible definir la variable con valor inicial dentro de la estructura for.  

```java
//        desde                    hasta       cómo se incrementa (en este ejemplo, de 1 en 1)
for (int valorInicial = 1; valorInicial <= 10; valorInicial++) {
    // Sentencias a ejecutar
}

```

También es posible agregar más de una expresión de fin.

```java
//        desde                    hasta       cómo se incrementa (en este ejemplo, de 1 en 1)
for (int valorInicial = 1; valorInicial >= 1 && valorInicial <= 10 ; valorInicial++) {
    // Sentencias a ejecutar
}
```

Para completar, es posible determinar la forma de incrementar el valor de la variable que define el fin de la iteración. 
Tambien se peude invocar a un método que realice el cálculo del incremento.

```java
//        desde                    hasta       cómo se incrementa (en este ejemplo, de 3 en 3)
for (int valorInicial = 1; valorInicial >= 1 && valorInicial <= 10 ; valorInicial += 3) { // Se incrementa de 3 en 3
    // Sentencias a ejecutar
}
```

Para entender la sentencia `valorInicial += 3` ver [Acumulador](./conceptos-basicos.html#Acumulador).

[Volver](../)