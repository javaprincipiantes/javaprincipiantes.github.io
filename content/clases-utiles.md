---
layout: default
---

[Volver](../)

# Clases útiles

En esta sección se describen algunos métodos y constantes estáticas que ayudan con el desarrollo de ciertos algoritmos.

## Math

Esta clase contiene constantes y métodos estáticos de utilidad para resolver operaciones matemáticas. No se puede instanciar: siempre se la usa escribiendo `Math.` seguido del método o la constante. Pertenece al paquete `java.lang`, así que no necesita `import`.

```java
// Constantes
double valorNumeroPi = Math.PI; // Valor aproximado de PI como double (relación entre la circunferencia de un círculo y su diámetro)
double valorNumeroE = Math.E; // Valor aproximado de E como double (la base de los logaritmos naturales)

// Valor absoluto (abs): devuelve el número sin signo
int valorAbsolutoInt = Math.abs(-10);       // Devuelve 10
long valorAbsolutoLong = Math.abs(-10L);    // Devuelve 10
float valorAbsolutoFloat = Math.abs(-10f);  // Devuelve 10.0
double valorAbsolutoDouble = Math.abs(-10D); // Devuelve 10.0

// Mayor valor entre dos números
int valorMayorInt = Math.max(2, 3);              // Devuelve 3
long valorMayorLong = Math.max(2L, 3L);          // Devuelve 3
float valorMayorFloat = Math.max(2.2f, 1.3f);    // Devuelve 2.2
double valorMayorDouble = Math.max(2.2D, 1.3D);  // Devuelve 2.2

// Menor valor entre dos números
int valorMenorInt = Math.min(2, 3);              // Devuelve 2
long valorMenorLong = Math.min(2L, 3L);          // Devuelve 2
float valorMenorFloat = Math.min(2.2f, 1.3f);    // Devuelve 1.3
double valorMenorDouble = Math.min(2.2D, 1.3D);  // Devuelve 1.3

// Potencia
double base = 2;
double exponente = 3;
double potencia = Math.pow(base, exponente); // Devuelve 8.0. Eleva 2 al cubo

// Raíz cuadrada
double raiz = Math.sqrt(9); // Devuelve 3.0
```

### Redondeos

Los tres métodos de redondeo hacen cosas distintas, y conviene no confundirlos:

```java
// ceil: redondea siempre hacia arriba, sin importar los decimales. Devuelve un double
double siguienteValor = Math.ceil(1.2); // Devuelve 2.0
double otroValorCeil = Math.ceil(1.9);  // Devuelve 2.0

// floor: redondea siempre hacia abajo, sin importar los decimales. Devuelve un double
double valorDelEntero = Math.floor(1.8); // Devuelve 1.0
double otroValorFloor = Math.floor(1.2); // Devuelve 1.0

// round: redondea al entero más cercano (si la parte decimal es 5 o más, hacia arriba). Devuelve un long
long valorRedondeado = Math.round(1.5); // Devuelve 2
long otroValorRound = Math.round(1.4);  // Devuelve 1
```

> **Nota:** `ceil` y `floor` devuelven un `double` (por eso `2.0` y no `2`), mientras que `round` devuelve un `long`. Si necesitamos el resultado como `int`, debemos convertirlo: `int redondeado = (int) Math.round(1.5);`

### Números aleatorios

`Math.random()` devuelve un `double` mayor o igual a 0 y **menor** a 1. Para obtener un número entero entre dos cotas, incluyéndolas, hay que llevar ese valor al rango deseado:

```java
int minimo = 1;
int maximo = 10;

// (maximo - minimo + 1) es la cantidad de valores posibles; sumar minimo desplaza el rango
int numeroAleatorio = (int) (Math.random() * (maximo - minimo + 1)) + minimo; // Un número entre 1 y 10, ambos incluidos
```

> **Importante:** la fórmula `(int) (Math.random() * maximo) + minimo` solo da el resultado esperado cuando `minimo` vale 1. Conviene usar siempre la fórmula completa.

## String

La clase `String` representa textos. Además de sus métodos, tiene una característica fundamental: **un String es inmutable**. Ningún método modifica el texto original; todos devuelven un String **nuevo**. Por eso, si queremos conservar el resultado, hay que asignarlo.

```java
String texto = "java";
texto.toUpperCase();  // Devuelve "JAVA", pero se descarta: texto sigue valiendo "java"
texto = texto.toUpperCase(); // Ahora sí, texto vale "JAVA"
```

Pertenece al paquete `java.lang`, así que tampoco necesita `import`.

```java
String texto = String.join("-", "Java", "es", "cool"); // Devuelve "Java-es-cool". El guión es el caracter que se usa para unir las palabras

char caracter = texto.charAt(0); // Devuelve 'J'. Obtiene un caracter del String por su posición. Las posiciones empiezan en 0 (cero)
texto = texto.concat("-Yeah"); // texto pasa a ser "Java-es-cool-Yeah". Concatena al final el String suministrado como parámetro
boolean contiene = texto.contains("Java");    // Devuelve true. Verifica si el String contiene "Java"
boolean empiezaCon = texto.startsWith("Java"); // Devuelve true. Verifica si el String empieza con "Java"
boolean terminaCon = texto.endsWith("Yeah");   // Devuelve true. Verifica si el String termina con "Yeah"
boolean estaEnBlanco = texto.isBlank(); // Devuelve false. Verifica si el String está vacío o si solo contiene espacios (disponible desde Java 11)
boolean estaVacio = texto.isEmpty();    // Devuelve false. Verifica si el String está vacío (length() == 0)
int largo = texto.length(); // Devuelve 17: es la cantidad de caracteres que contiene el String

texto = texto.replace("-", " "); // texto pasa a ser "Java es cool Yeah", reemplazando los guiones por espacios

String subCadena = texto.substring(4); // Devuelve " es cool Yeah". Genera otro String desde el índice 4 hasta el final
String subCadenaInicioFin = texto.substring(0, 4); // Devuelve "Java". Desde el índice 0 hasta el 4 SIN incluirlo (es decir, los índices 0, 1, 2 y 3)

String aMinuscula = texto.toLowerCase(); // Devuelve "java es cool yeah". El contenido de texto no cambia
String aMayuscula = texto.toUpperCase(); // Devuelve "JAVA ES COOL YEAH". El contenido de texto no cambia

boolean igualExacto = texto.equals("Java es cool Yeah"); // Devuelve true. Compara el contenido con el String provisto como parámetro
boolean igualIgnorandoMayusculasOMinusculas = texto.equalsIgnoreCase("JAVA ES COOL YEAH"); // Devuelve true. Compara el contenido sin distinguir mayúsculas de minúsculas

String[] palabras = texto.split(" "); // Devuelve un array de 4 elementos: "Java", "es", "cool" y "Yeah"

String conEspacios = "     Java      ";
String sinEspacios = conEspacios.trim(); // Devuelve "Java", sin los espacios del inicio y del final
```

> **Importante:** para comparar el contenido de dos String siempre se usa `equals()` (o `equalsIgnoreCase()`), nunca `==`. Ver [operadores de igualdad](./operadores.html#operadores-de-igualdad-y-relacionales).

## Random

Esta clase contiene métodos útiles para generar números aleatorios. A diferencia de `Math` y `String`, pertenece al paquete `java.util`, con lo cual **debemos importarla** (ver [imports](./introduccion-a-java.html#imports)).

A diferencia de `Math.random()`, `Random` sí se instancia: creamos un objeto y le pedimos los números que necesitemos.

```java
import java.util.Random;

public class MiPrograma {

    public static void main(String[] args) {
        Random random = new Random();

        // Un número entero aleatorio entre dos cotas, incluyéndolas
        int minimo = 1;
        int maximo = 10;
        int numeroAleatorio = random.nextInt((maximo - minimo) + 1) + minimo; // Un número entre 1 y 10, ambos incluidos

        System.out.println(numeroAleatorio);
    }
}
```

Otros métodos de un objeto `Random`:

```java
Random random = new Random();

int numeroEntero = random.nextInt(10);   // Un número entre 0 y 9 (el 10 no se incluye)
double numeroConDecimales = random.nextDouble(); // Un número mayor o igual a 0.0 y menor a 1.0
boolean valorDeVerdad = random.nextBoolean();    // true o false
```

> **Nota:** alcanza con crear un solo objeto `Random` y reutilizarlo cada vez que necesitemos un número. No hace falta crear uno nuevo en cada vuelta de un bucle.

[Volver](../)
