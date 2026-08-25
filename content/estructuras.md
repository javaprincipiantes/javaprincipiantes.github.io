---
layout: default
---

[Volver](../)

# Estructuras

Como muchos lenguajes de programación, Java nos provee de ciertas estructuras definidas que nos permiten realizar distintas tareas. Estas estructuras poseen sus propias palabras reservadas, que utilizaremos para definirlas y utilizarlas.

## Estructuras de decisión

### if-else

Es una estructura que nos permite evaluar una o varias expresiones booleanas.
La palabra reservada para definirla es **if** y, a continuación, debemos indicar entre paréntesis la expresión (o expresiones) que se evaluarán para determinar qué debemos hacer.

`if (expresion1 && expresion2)`

La estructura se completa con dos llaves, una de apertura y otra de cierre ({ }). Estas llaves delimitan las sentencias de código que deberán ejecutarse en caso de que el resultado de las expresiones incluidas entre los paréntesis sea verdadero (true).

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

//                            true como resultado final
//                 true       &&                true
if (cantidadDeFrutas > 1 && cantidadDeFrutas < 10) {
    // Sentencias que se ejecutan cuando el resultado final de las expresiones evaluadas es true
    hayFrutasSuficientes = true; // La cantidad de frutas está comprendida en el rango 1-10, con lo cual asignamos true
}
```

Cuando solo tenemos una sentencia dentro de las llaves de la estructura if, podemos omitirlas.

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes = false;

if (cantidadDeFrutas > 1 && cantidadDeFrutas < 10)
    hayFrutasSuficientes = true; // Única sentencia que se ejecuta si el resultado es true
```

En caso de existir más de una sentencia a ejecutar, se deben incluir las llaves de manera obligatoria.

> **Recomendación:** aunque haya una sola sentencia, escribir siempre las llaves evita errores difíciles de detectar. Si más adelante agregamos una segunda línea y olvidamos las llaves, esa línea se ejecutará **siempre**, sin importar el resultado del if.

La estructura **if** cuenta con otro bloque adicional (no obligatorio) que nos permite ejecutar sentencias en caso de que la expresión (o expresiones del if) no se cumplan. Para ello debemos incluir la palabra reservada **else** luego de la llave de cierre del caso verdadero del if.

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes;

//                            false como resultado final
//                 false      &&               (no se evalúa)
if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
    // Estas sentencias no se ejecutan, porque el resultado final es false
    hayFrutasSuficientes = true;
} else {
    // Sentencias que se ejecutan cuando el resultado final de las expresiones evaluadas es false
    hayFrutasSuficientes = false; // La cantidad de frutas no satisface la condición del if
}
```

> **Nota:** en el ejemplo anterior, `cantidadDeFrutas > 5` es `false`. Como se trata de un `&&`, el resultado final ya no puede ser `true`, así que la segunda expresión ni siquiera se evalúa (ver [evaluación en cortocircuito](./operadores.html#operadores-lógicos)).

Al igual que con las llaves del **if**, si el bloque **else** solo tiene una sentencia, se pueden omitir las llaves. Si las sentencias a ejecutar son más de una, se deben incluir de manera obligatoria.

```java
int cantidadDeFrutas = 3;
boolean hayFrutasSuficientes;

if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10)
    hayFrutasSuficientes = true;
else
    hayFrutasSuficientes = false;
```

**Dato:** los comentarios no cuentan como sentencias de código ejecutables. Un `if` sin llaves seguido de un comentario y de una sentencia sigue teniendo una sola sentencia.

Es posible incluir un nuevo **if** luego del **else**, si necesitamos evaluar una nueva expresión únicamente cuando la primera no se cumple.

```java
int cantidadDeFrutas = 7;
boolean hayFrutasSuficientes = false;

if (cantidadDeFrutas == 1) {
    // No se ejecuta: la cantidad de frutas no es 1
    hayFrutasSuficientes = false;
} else if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
    // Se ejecuta esta rama: 7 es mayor a 5 y menor a 10
    hayFrutasSuficientes = true;
} else {
    // Se ejecutaría solo si ninguna de las condiciones anteriores se cumpliera
    hayFrutasSuficientes = false;
}
```

Podemos usar la cantidad de `else if` que necesitemos. Es importante notar que **solo se ejecuta la primera rama cuya condición sea verdadera**: el resto se descarta.

Además, es posible incluir (anidar) un if dentro de otro if, aunque no es muy recomendable porque el código se vuelve difícil de leer.

```java
int cantidadDeFrutas = 7;
boolean hayFrutasSuficientes = false;

if (cantidadDeFrutas > 1) {
    // Entra, porque 7 es mayor a 1

    if (cantidadDeFrutas > 5 && cantidadDeFrutas < 10) {
        hayFrutasSuficientes = true; // Entra también, porque 7 está entre 5 y 10
    }
}
```

En general, este ejemplo puede escribirse mejor con un solo if combinando las expresiones con `&&`.

### switch

La estructura de decisión múltiple (switch) nos permite evaluar el contenido de una variable y ejecutar sentencias de código según el caso que aplique.

La palabra reservada es **switch** y va acompañada de dos paréntesis, donde debemos colocar la variable a evaluar (no expresiones lógicas).

Luego, con la palabra reservada **case**, podremos indicar los distintos valores posibles y las sentencias que se deben ejecutar para cada uno. Para indicar que un caso termina, se debe incluir la palabra reservada **break**.

En caso de no incluir el `break`, la ejecución continuará en "modo cascada" hacia los casos siguientes, sin importar su valor, hasta encontrar un `break` o el final del switch. Esto nos permite "agrupar" casos.

Switch nos provee además de la palabra reservada **default**, para ejecutar sentencias cuando ningún caso aplique.

```java
int diaDeLaSemana = 1;
String nombreDelDia;

switch (diaDeLaSemana) {
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
        // Se ejecuta si el contenido de diaDeLaSemana no coincide con ninguno de los casos anteriores
        nombreDelDia = "Día inexistente";
}
```

En general usamos **switch** cuando no necesitamos evaluar expresiones y contamos con más de 2 casos.

Ejemplo de agrupación de casos:

```java
int diaDeLaSemana = 1;
boolean seTrabaja;

switch (diaDeLaSemana) {
    case 2:
    case 3:
    case 4:
    case 5:
    case 6:
        // Los casos 2 a 6 comparten estas sentencias, porque ninguno de ellos tiene su propio break
        seTrabaja = true;
        break;
    case 1:
    case 7:
        seTrabaja = false;
        break;
    default:
        seTrabaja = false;
}
```

> **Importante:** conviene incluir siempre el bloque **default**. Si asignamos una variable dentro del switch y omitimos el default, puede haber un camino en el que la variable nunca reciba un valor, y Java nos dará un error de compilación al intentar usarla.

Lo más habitual es evaluar el contenido de variables de tipo entero o `char`. Desde la versión 1.7 de Java, se permite también evaluar variables de tipo `String`.

## Estructuras de iteración (bucles)

Las estructuras de iteración definidas a continuación nos permitirán ejecutar una o varias sentencias de código tantas veces como necesitemos.

### while

Esta estructura, de palabra reservada **while**, evalúa una o varias expresiones lógicas (incluidas entre paréntesis) y ejecuta el código comprendido entre sus llaves **mientras el resultado sea verdadero**. La expresión se evalúa antes de cada repetición, incluida la primera: si de entrada es falsa, el bloque no se ejecuta ninguna vez.

La estructura **while** suele utilizarse cuando no sabemos de antemano cuántas iteraciones debemos realizar.

```java
int cantidadDeFrutas = 0;

while (cantidadDeFrutas < 10) {
    cantidadDeFrutas++; // Se post incrementa el valor de la variable. Se repite mientras la cantidad de frutas sea menor a 10
}

// Al salir del bucle, cantidadDeFrutas vale 10
```

Al igual que en la estructura if, es posible omitir las llaves si solo se debe ejecutar una sentencia.

```java
int cantidadDeFrutas = 0;

while (cantidadDeFrutas < 10)
    cantidadDeFrutas++;
```

**Importante:** el valor de `cantidadDeFrutas` debe cambiar dentro del bucle de manera que la expresión pueda, en algún momento, ser falsa y así terminar la iteración. Si eso no sucede, entramos en una iteración infinita y el programa nunca termina.

```java
int cantidadDeFrutas = 0;

// Iteración infinita: cantidadDeFrutas nunca cambia, la expresión siempre es true
while (cantidadDeFrutas < 10) {
    System.out.println("Sigo contando frutas");
}
```

Es posible incluir más de una expresión usando operadores lógicos.

```java
int cantidadDeFrutas = 0;
boolean hayLugarEnElCajon = true;

while (cantidadDeFrutas < 10 && hayLugarEnElCajon) {
    cantidadDeFrutas++; // Se repite mientras haya menos de 10 frutas y además quede lugar en el cajón
}
```

Una forma de entender esta estructura es pensar: "ejecutá este bloque **mientras** esto ocurra".

### do-while

Esta estructura es similar a **while**, con la diferencia de que el bloque se ejecuta **al menos una vez**, porque la expresión se evalúa recién al final de cada repetición. Se debe incluir la palabra reservada **do**, seguida de las llaves con las sentencias a ejecutar, y luego la palabra reservada **while** con la expresión entre paréntesis y un punto y coma final.

```java
int numero = 0;

do {
    numero++; // Se ejecuta al menos una vez, aun si la expresión del while fuera falsa desde el principio
} while (numero <= 3);

// Al salir del bucle, numero vale 4
```

Para entenderla, sirve pensar: "ejecutá las sentencias y repetilas **mientras se cumpla** la expresión del while".

Es la estructura de iteración más utilizada para validar datos ingresados por el usuario, justamente porque primero hay que pedir el dato y recién después se puede verificar:

```java
Scanner scanner = new Scanner(System.in);
int edad;

do {
    System.out.println("Ingrese una edad mayor a 0:");
    edad = scanner.nextInt();
} while (edad <= 0); // Vuelve a pedir el dato mientras la edad no sea válida
```

### for

Es la estructura de iteración que se suele utilizar cuando conocemos exactamente cuántas veces debemos iterar. Su palabra reservada es **for** y viene acompañada de paréntesis que incluyen tres bloques para controlar la iteración, separados por punto y coma (;):

1. **Inicialización:** la variable de control y su valor inicial (desde). Se ejecuta una sola vez, al comenzar.
2. **Condición:** la expresión que debe ser verdadera para seguir iterando (hasta). Se evalúa antes de cada repetición.
3. **Actualización:** cómo cambia la variable de control después de cada repetición.

Incluye llaves que delimitan las sentencias que se ejecutan en cada iteración. Si la sentencia a ejecutar es única, pueden omitirse.

```java
int contador = 0;

//         desde              hasta            cómo se incrementa (en este ejemplo, de 1 en 1)
for (contador = 1; contador <= 10; contador++) {
    // Sentencias a ejecutar. Este bloque se ejecuta 10 veces
}
```

Lo habitual es declarar la variable de control dentro de la propia estructura for. De esa manera, la variable solo existe dentro del bucle.

```java
for (int contador = 1; contador <= 10; contador++) {
    // Sentencias a ejecutar
}

// Acá la variable contador ya no existe
```

También es posible combinar más de una expresión en la condición usando operadores lógicos.

```java
int cantidadDeFrutas = 20;

for (int contador = 1; contador <= 10 && contador < cantidadDeFrutas; contador++) {
    // Sentencias a ejecutar
}
```

Por último, podemos elegir de qué manera se actualiza la variable de control. No está obligada a avanzar de 1 en 1, e incluso puede decrecer.

```java
//         desde              hasta        cómo se incrementa (en este ejemplo, de 3 en 3)
for (int contador = 1; contador <= 10; contador += 3) {
    // Se ejecuta con contador valiendo 1, 4, 7 y 10
}

// También podemos recorrer al revés
for (int contador = 10; contador >= 1; contador--) {
    // Se ejecuta con contador valiendo 10, 9, 8 ... hasta 1
}
```

Para entender la sentencia `contador += 3` ver [acumulador](./conceptos-basicos.html#acumulador).

[Volver](../)
