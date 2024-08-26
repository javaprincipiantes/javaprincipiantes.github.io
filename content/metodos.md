---
layout: default
---

[Volver](../)

# Métodos / funciones

Los métodos son un conjunto de sentencias o instrucciones ordenadas y relacionadas de manera específica ([algoritmo](https://es.wikipedia.org/wiki/Algoritmo)) con el fin de resolver un problema.

Es importante que cada método definido tenga (en lo posible) solo un objetivo, resolver una operación aritmética, por ejemplo. Si un método tiene la responsabilidad de realizar más de una operación, sumar y restar por ejemplo, generaremos [acoplamiento de código](https://es.wikipedia.org/wiki/Acoplamiento_(inform%C3%A1tica)), lo cual no es una buena práctica.

Siempre es mejor definir muchos métodos específicos (que resuelvan tareas puntuales), en lugar de un método que resuelva varias tareas.

Los métodos ejecutan las sentencias de manera estructurada, tal y como se expresan las sentencias de código (en ese orden, de arriba hacia abajo), incluidas al momento de definir el método.

Además, los métodos pueden incluir [estructuras de decisión](./estructuras.html#estructuras-de-decisión) (if-else o switch) o [estructuras de iteración](./estructuras.html#estructuras-de-iteración-bucles) (while, do-while, for), según sea necesario.

La nomenclatura de los métodos en Java debe seguir los lineamientos de [camelCase](https://es.wikipedia.org/wiki/Camel_case). La primera letra en minúscula (al igual que el resto) y si existe otra palabra debe comenzar en mayúscula, con las siguientes letras de la palabra en minúscula.

Ejemplo de nombre de método: mostrarMensaje

## ¿Cómo definir un método/función? 

En Java, los métodos se definen indicando el [modificador de acceso](./clases.html#modificadores-de-acceso), el tipo de dato que retornan (pueden ser tipos de dato primitivos o personalizados, ver [Clases](./clases.html)), el nombre del método o función, un conjunto de paréntesis donde se podrán recibir [parámetros](./metodos.html#Par%C3%A1metros) (o no) y un conjunto de llaves que indican las sentencias que se ejecutarán por el método que estamos definiendo.

Cuando se define un tipo de dato de retorno como por ejemplo `int`, es obligatorio incluir en el cuerpo del método (entre las llaves), la palabra reservada `return`, seguida de un dato que cumpla con el tipo de dato definido en el método. Caso contrario, tendremos un error de compilación.

```java
/* public -> modificador de acceso
 * int -> tipo de dato que devuelve el método
 * sumar -> nombre del método
 * int operadorUno, int operadorDos -> parámetros (datos o valores) que recibe el método 
*/
public int sumar (int operadorUno, int operadorDos) {
    return operadorUno + operadordos; // Primero se resuelve la operación y luego se devuelve el resultado de la misma.
}
```

Es posible que un método no devuelva un dato o valor, solo ejecute una o varias sentencias de código. En ese caso, en el lugar del tipo de dato, se debe utilizar la palabra reservada `void`. Si el método tiene la palabra reservada `void`, no se debe incluir la palabra reservada `return`. Caso contrario obtendremos un error de compilación.

Método que no recibe parámetros (nada entre los paréntesis) y no devuelve un dato o valor (void).

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
*/
public void mostrarMensajePorPantalla () {
    System.out.println("Hola");
}
```

Método que muestra un mensaje por pantalla, recibiendo un texto o palabra como parámetro. No devuelve un dato o valor (void).

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
 * String mensaje -> parámetro con el dato o valor que debe mostrarse por pantalla
*/
public void mostrarMensajePorPantalla (String mensaje) {
    System.out.println(mensaje);
}
```

Los métodos pueden, entre sus sentencias a ejecutar, invocar o llamar a otros métodos.
Basta con escribir el nombre del método, seguido de los paréntesis. Si el método al que invocamos espera recibir parámetros, debemos proveer de dichos datos o valores ([literales](./conceptos-basicos.html#Literales) o [ingresados por el usuario](./entrada-y-salida-por-consola.html#par%C3%A1metros)).

Es posible definir variables dentro de un método, con la salvedad de que sólo se podrán utilizar dentro del método. En otras palabras, las variables definidas dentro de las llaves de un método sólo puede utilizarse en el método y no en otro método por ejemplo.

```java
// Método para sumar dos operadores
public int sumar (int operadorUno, int operadorDos) {
    return operadorUno + operadordos; // Primero se resuelve la operación y luego se devuelve el resultado de la misma.
}

/* Ejemplo de método que invoca a otro método
 * public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarResultadoDeSumaPorPantalla -> nombre del método
 * int operadorUno, int operadorDos -> parámetros (datos o valores) que recibe el método 
*/
public void mostrarResultadoDeSumaPorPantalla () {
    // Definimos una variable "local" al método, nombrada resultado
    int resultado = sumar(2 + 3); // Invocación al método sumar antes definido el cual calculará la suma de los valores 2 y 3, y asignará el resultado a la variable resultado

    System.out.println(resultado); // Se muestra por pantalla el contenido de la variable resultado -> 5
}
```

## Parámetros

Un parámetro, definido para un método (dentro de los paréntesis del método), es una variable que solo existe dentro del método y tendrá asignado un dato o valor proporcionado al momento de ser invocado. Los métodos pueden no recibir parámetros, recibir un parámetro o recibir varios parámetros.

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
 * String mensaje -> parámetro con el dato o valor que debe mostrarse por pantalla
*/
public void mostrarMensajePorPantalla (String mensaje) {
    System.out.println(mensaje);
}
```

* Concepto de una entrada, múltiples salidas.

Un método siempre tiene una entrada (inicio de las sentencias que se incluyen como cuerpo del método) y puede tener mas de una salida (mas de un `return`). Por ejemplo si incluimos un `if`.

```java
public float dividir (float numerador, float denominador) {
    if(denominador == 0) {
        // No es posible dividir por cero.
        return 0;
    } else {
        return numerador / denominador;
    }
}
```

Otra forma de representar el mismo código con el mismo resultado:

```java
public float dividir (float numerador, float denominador) {
    if(denominador == 0) {
        // No es posible dividir por cero.
        return 0;
    } 
    
    return numerador / denominador;
}
```

En este segundo ejemplo, no se incluyó el bloque `else`, ya que, para este algoritmo, no es estrictamente necesario.

* Concepto de una entrada, una salida.

El mismo ejemplo puede representarse evitando tener mas de un `return`.

```java
public float dividir (float numerador, float denominador) {
    float resultado = 0;
    
    if(denominador != 0) {
        resultado = numerador / denominador
    } 

    return resultado;
}
```

## Sobrecarga de métodos/funciones

Es posible definir mas de un método con el mismo nombre, con la salvedad de que no puede coincidir en la misma cantidad de parámetros y el mismo orden de tipos de dato de los parámetros que recibe (si es que recibe parámetros).

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
*/
public void mostrarMensajePorPantalla () {
    System.out.println("Hola");
}

// Sobrecarga del método mostrarMensajePorPantalla que recibe un parámetro
public void mostrarMensajePorPantalla (String mensaje) {
    System.out.println(mensaje);
}

// Ejemplo inválido de sobrecarga por tener un método con el mismo nombre que recibe un parámetro String (no importa el nombre del parámetro)
public void mostrarMensajePorPantalla (String otroMensaje) {
    System.out.println(mensaje);
}

// Ejemplo válido de sobrecarga, el método recibe dos parámetros de tipo String, a pesar de que existe otro método que recibe un parámetro de tipo String
public void mostrarMensajePorPantalla (String mensaje, String otroMensaje) {
    System.out.println(mensaje + otroMensaje); // En presencia de un String, el operador + funciona como concatenador
}
```

[Volver](../)