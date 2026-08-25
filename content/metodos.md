---
layout: default
---

[Volver](../)

# Métodos / funciones

Los métodos son un conjunto de sentencias o instrucciones ordenadas y relacionadas de manera específica ([algoritmo](https://es.wikipedia.org/wiki/Algoritmo)) con el fin de resolver un problema.

Es importante que cada método definido tenga (en lo posible) un solo objetivo: resolver una operación aritmética, por ejemplo. Si un método tiene la responsabilidad de realizar más de una tarea (sumar y restar, por ejemplo), generamos [acoplamiento de código](https://es.wikipedia.org/wiki/Acoplamiento_(inform%C3%A1tica)), lo cual no es una buena práctica.

Siempre es mejor definir muchos métodos específicos, que resuelvan tareas puntuales, en lugar de un método que resuelva varias tareas a la vez.

Los métodos ejecutan las sentencias en el orden en el que fueron escritas, de arriba hacia abajo.

Además, los métodos pueden incluir [estructuras de decisión](./estructuras.html#estructuras-de-decisión) (if-else o switch) o [estructuras de iteración](./estructuras.html#estructuras-de-iteración-bucles) (while, do-while, for), según sea necesario.

La nomenclatura de los métodos en Java sigue los lineamientos de [camelCase](https://es.wikipedia.org/wiki/Camel_case): la primera letra en minúscula y, si el nombre está formado por más de una palabra, cada palabra siguiente comienza con mayúscula.

Ejemplo de nombre de método: `mostrarMensaje`. Como los métodos representan acciones, sus nombres suelen empezar con un verbo.

## ¿Cómo definir un método/función?

En Java, los métodos se definen indicando el [modificador de acceso](./clases.html#modificadores-de-acceso), el tipo de dato que retornan (puede ser un tipo de dato primitivo o una clase, ver [clases](./clases.html)), el nombre del método, un conjunto de paréntesis donde se podrán recibir [parámetros](#parámetros) (o no) y un conjunto de llaves que delimitan las sentencias que ejecutará el método.

Cuando definimos un tipo de dato de retorno, como por ejemplo `int`, es obligatorio incluir en el cuerpo del método (entre las llaves) la palabra reservada `return`, seguida de un valor que cumpla con ese tipo de dato. Caso contrario, tendremos un error de compilación.

```java
/* public -> modificador de acceso
 * int -> tipo de dato que devuelve el método
 * sumar -> nombre del método
 * int primerNumero, int segundoNumero -> parámetros (datos o valores) que recibe el método
 */
public int sumar (int primerNumero, int segundoNumero) {
    return primerNumero + segundoNumero; // Primero se resuelve la operación y luego se devuelve el resultado
}
```

> **Nota:** los valores que recibe un método se llaman **operandos** o, en este caso, sumandos. No hay que confundirlos con los [operadores](./operadores.html), que son los símbolos de la operación (`+`, `-`, `*`, etc).

Es posible que un método no devuelva ningún dato y solo ejecute una o varias sentencias. En ese caso, en el lugar del tipo de dato se debe utilizar la palabra reservada `void`. Si el método está definido como `void`, no debe devolver ningún valor con `return`; caso contrario obtendremos un error de compilación.

Método que no recibe parámetros (nada entre los paréntesis) y no devuelve un dato o valor (void):

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
 */
public void mostrarMensajePorPantalla () {
    System.out.println("Hola");
}
```

Método que muestra un mensaje por pantalla recibiendo un texto como parámetro. No devuelve un dato o valor (void):

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

### Invocar a un método

Los métodos pueden, entre sus sentencias, invocar o llamar a otros métodos.
Basta con escribir el nombre del método seguido de los paréntesis. Si el método al que invocamos espera recibir parámetros, debemos proveer esos datos, separados por comas y en el mismo orden en el que fueron definidos. Pueden ser [literales](./conceptos-basicos.html#literales), variables o valores [ingresados por el usuario](./entrada-y-salida-por-consola.html#entrada-por-consola-scanner).

Es posible declarar variables dentro de un método, con la salvedad de que solo se podrán utilizar dentro de él. En otras palabras, las variables declaradas dentro de las llaves de un método no existen para el resto de la clase. A estas variables se las llama **variables locales**.

```java
// Método para sumar dos números
public int sumar (int primerNumero, int segundoNumero) {
    return primerNumero + segundoNumero;
}

/* Ejemplo de método que invoca a otro método
 * public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarResultadoDeSumaPorPantalla -> nombre del método
 */
public void mostrarResultadoDeSumaPorPantalla () {
    // Declaramos una variable local al método, llamada resultado
    int resultado = sumar(2, 3); // Invocación al método sumar, que calcula 2 + 3 y devuelve 5

    System.out.println(resultado); // Se muestra por pantalla el contenido de la variable resultado -> 5
}
```

> **Importante:** los argumentos se separan con coma. `sumar(2, 3)` invoca al método con dos valores; `sumar(2 + 3)` le pasa un único valor (el 5) y no compila, porque el método espera dos parámetros.

## Parámetros

Un parámetro, definido para un método (dentro de los paréntesis del método), es una variable que solo existe dentro del método y tendrá asignado el dato o valor proporcionado al momento de la invocación. Los métodos pueden no recibir parámetros, recibir uno o recibir varios.

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

Cuando invocamos al método, el valor que enviamos se copia dentro del parámetro:

```java
mostrarMensajePorPantalla("Hola"); // Dentro del método, el parámetro mensaje contiene "Hola"

String saludo = "Buenas!";
mostrarMensajePorPantalla(saludo); // Dentro del método, el parámetro mensaje contiene "Buenas!"
```

El orden y el tipo de los valores enviados deben coincidir con los de los parámetros declarados. Si el método espera `(String, int)`, no podemos invocarlo con `(int, String)`.

## Entradas y salidas de un método

* Concepto de una entrada, múltiples salidas

Un método siempre tiene una entrada (el comienzo de las sentencias de su cuerpo) y puede tener más de una salida (más de un `return`). Por ejemplo, si incluimos un `if`.

```java
public float dividir (float numerador, float denominador) {
    if (denominador == 0) {
        // No es posible dividir por cero
        return 0;
    } else {
        return numerador / denominador;
    }
}
```

Otra forma de representar el mismo código con el mismo resultado:

```java
public float dividir (float numerador, float denominador) {
    if (denominador == 0) {
        // No es posible dividir por cero
        return 0;
    }

    return numerador / denominador;
}
```

En este segundo ejemplo no se incluyó el bloque `else`, ya que para este algoritmo no es estrictamente necesario: si se cumple el `if`, el método termina en el `return` y nunca llega a la línea siguiente.

* Concepto de una entrada, una salida

El mismo ejemplo puede representarse evitando tener más de un `return`.

```java
public float dividir (float numerador, float denominador) {
    float resultado = 0;

    if (denominador != 0) {
        resultado = numerador / denominador;
    }

    return resultado;
}
```

> **Nota:** devolver `0` cuando el denominador es cero es una decisión discutible, porque el método le miente a quien lo invoca: no se puede distinguir una división inválida de una división que legítimamente dio cero. Se usa acá para mantener el ejemplo simple. En un programa real conviene validar el denominador antes de invocar al método, o bien informar el problema (por ejemplo, con una excepción).

## Sobrecarga de métodos/funciones

Es posible definir más de un método con el mismo nombre, siempre que se diferencien en la cantidad de parámetros o en los tipos de dato de esos parámetros (y su orden). Al conjunto formado por el nombre y los parámetros se lo llama **firma** del método: dos métodos con el mismo nombre no pueden tener la misma firma.

El nombre de los parámetros no forma parte de la firma, así que cambiarlo no alcanza para diferenciar dos métodos.

```java
/* public -> modificador de acceso
 * void -> no devuelve un dato o valor
 * mostrarMensajePorPantalla -> nombre del método
 */
public void mostrarMensajePorPantalla () {
    System.out.println("Hola");
}

// Sobrecarga válida: mismo nombre, pero recibe un parámetro
public void mostrarMensajePorPantalla (String mensaje) {
    System.out.println(mensaje);
}

// Sobrecarga válida: recibe dos parámetros de tipo String
public void mostrarMensajePorPantalla (String mensaje, String otroMensaje) {
    System.out.println(mensaje + otroMensaje); // En presencia de un String, el operador + funciona como concatenador
}

// Sobrecarga válida: recibe un parámetro, pero de otro tipo de dato
public void mostrarMensajePorPantalla (int numero) {
    System.out.println(numero);
}

/* Sobrecarga INVÁLIDA: ya existe un método con el mismo nombre que recibe un único
 * parámetro String. El nombre del parámetro no diferencia la firma, así que esto es
 * un error de compilación.
 */
public void mostrarMensajePorPantalla (String otroMensaje) {
    System.out.println(otroMensaje);
}
```

> **Nota:** el tipo de dato de retorno tampoco forma parte de la firma. Dos métodos que solo se diferencien en lo que devuelven no son una sobrecarga válida.

[Volver](../)
