---
layout: default
---

[Volver](../)

# Clases útiles

En esta sección se describen algunos métodos y constantes estáticas que ayudan con el desarrollo de ciertos algoritmos.

## Math

Esta clase contiene constantes y métodos estáticos (no se puede instanciar un objeto) de utilidad para resolver operaciones matemáticas.

```java
// Constantes
double valorNumeroPi = Math.PI; // Valor aproximado a PI expresado como double (relación entre la circunferencia de un círculo y su diámetro)
double valorNumeroE = Math.E; // Valor aproximado a E como double (la base de los logaritmos naturales)

// Métodos estáticos

// Valor absoluto (abs)
int valorAbsolutoInt = Math.abs(10);
long valorAbsolutoLong = Math.abs(10L);
float valorAbsolutoFloat = Math.abs(10f);
double valorAbsolutoDouble = Math.abs(10D);

// Redondeos
double siguienteValor = Math.ceil(1.2); // Devuelve 2, no importa que decimales contenga el número como parámetro
double valorDelEntero = Math.floor(1.8); // Devuelve 1, no importa si los decimales son 5  o más
double valorRedondeado = Math.round(1.5); // Devuelve 2, si los decimales son 5 o más, redondea hacia el siguiente entero

// Mayor valor entre dos números
int valorMayorInt = Math.max(2, 3); // Devuelve el número mayor (int) entre los proporcionados como parámetros
long valorMayorLong = Math.max(2L, 3L); // Devuelve el número mayor (long) entre los proporcionados como parámetros
float valorMayorFlat = Math.max(2.2f, 1.3f); // Devuelve el número mayor (float) entre los proporcionados como parámetros
float valorMayorFloat = Math.max(2.2f, 1.3f); // Devuelve el número mayor (float) entre los proporcionados como parámetros
double valorMayorDouble = Math.max(2.2D, 1.3D); // Devuelve el número mayor (double) entre los proporcionados como parámetros

// Menor valor entre dos números
int valorMenorInt = Math.min(2, 3); // Devuelve el número menor (int) entre los proporcionados como parámetros
long valorMenorLong = Math.min(2L, 3L); // Devuelve el número menor (long) entre los proporcionados como parámetros
float valorMenorrFlat = Math.min(2.2f, 1.3f); // Devuelve el número menor (float) entre los proporcionados como parámetros
float valorMenorFloat = Math.min(2.2f, 1.3f); // Devuelve el número menor (float) entre los proporcionados como parámetros
double valorMenorDouble = Math.min(2.2D, 1.3D); // Devuelve el número menor (double) entre los proporcionados como parámetros

// Potencia
double base = 2;
double exponente = 3;
double potencia = Math.pow(base, exponente); // Devuelve 8. Eleva 2 al cubo

// Número aleatorio entre dos cotas (incluyéndolas)
int minimo = 1;
int maximo = 10;
int numeroAleatorioEntreUnoYDiezInclusive =  (int)(Math.random() * maximo) + minimo;
```

## String

Esta clase contiene métodos estáticos útiles y métodos posibles de utilizar con un objeto String

```java
String texto = String.join("-", "Java", "es", "cool"); // Devuelve "Java-es-cool". El guión es el caracter que se usará para unir las palabras

char caracter = texto.charAt(0); // Devuelve 'J'. Obtiene un caracter contenido en el String utilizando su posición. Las posiciones empiezan en 0 (cero)
texto = texto.concat("-Yeah"); // Devuelve "Java-es-cool-Yeah". Concatena al final del String, el String suministrado como parámetro
boolean contiene = texto.contains("Java"); // Devuelve verdadero. Verifica si el String contiene el String "Java"
boolean empiezaCon = texto.startsWith("Java"); // Devuelve verdadero. Verifica si el String empieza con el String "Java"
boolean terminaCon = texto.endsWith("Yeah"); // Devuelve verdadero. Verifica si el String termina con el String "Yeah"
boolean estaEnBlanco = texto.isBlank(); // Devuelve falso. Verifica si el String esta vacío o si solo contiene espacios
boolean estaVacio = texto.isEmpty(); // Devuelve falso. Verifica si el String esta vacío (length == 0)
int largo = texto.length(); // Devuelve 17, es la cantidad de caracteres que contiene el String
texto = texto.replace("-", " "); // Devuelve "Java es cool Yeah", reemplazando los guiones por espacios
String subCadena = texto.substring(4); // Devuelve " es cool Yeah". Genera otro String comenzando en el índice 4 hasta el final
String subCadenaInicioFin = texto.substring(0,4); // Devuelve "Java". Genera otro String comenzando en el índice 0 hasta el índice 4
String aMinuscula = texto.toLowerCase(); // Convierte todos los caracteres del String a minúscula
String aMayuscula = texto.toUpperCase(); // Convierte todos los caracteres del String a mayúscula
boolean igualExacto = texto.equals("Java"); // Devuelve falso. Compara el String con el String que se provee como parámetro
boolean igualIgnorandoMayusculasOMinusculas = texto.equals("Java"); // Devuelve falso. Compara el String con el String que se provee como parámetro sin considerar si los caracteres estan en mayúscula o minúscula
texto = "     Java      ";
texto = texto.trim(); // Devuelve "Java" sin espacios al inicio y el final del String
String[] palabras = texto.split(" "); // Devuelve un array de String con las palabras separadas donde se encuentra un espacio
```

[Volver](../)