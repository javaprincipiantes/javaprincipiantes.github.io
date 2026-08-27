---
layout: default
---

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

## Date

`Date` representa un instante en el tiempo (fecha y hora). Pertenece al paquete `java.util`, con lo cual **debemos importarla** (ver [imports](./introduccion-a-java.html#imports)).

```java
import java.util.Date;

Date ahora = new Date(); // Crea un objeto con la fecha y hora actuales del sistema

System.out.println(ahora); // Muestra algo como: Tue Aug 25 19:30:00 ART 2026
```

Sus métodos más usados sirven para comparar dos fechas:

```java
Date ahora = new Date();
Date otraFecha = new Date(0L); // El parámetro son los milisegundos transcurridos desde el 1 de enero de 1970 (UTC)

long milisegundos = ahora.getTime(); // Devuelve los milisegundos transcurridos desde el 1 de enero de 1970

boolean esAnterior = otraFecha.before(ahora); // Devuelve true si otraFecha es anterior a ahora
boolean esPosterior = otraFecha.after(ahora); // Devuelve false si otraFecha no es posterior a ahora
boolean sonIguales = otraFecha.equals(ahora); // Devuelve false: representan instantes distintos
```

Para mostrar una fecha con un formato propio usamos la clase `SimpleDateFormat`, del paquete `java.text`:

```java
import java.text.SimpleDateFormat;
import java.util.Date;

Date ahora = new Date();

SimpleDateFormat formato = new SimpleDateFormat("dd/MM/yyyy");
String fechaComoTexto = formato.format(ahora); // Devuelve algo como "25/08/2026"

System.out.println(fechaComoTexto);
```

Las letras del patrón indican qué parte de la fecha se muestra: `dd` el día, `MM` el mes, `yyyy` el año, `HH` la hora, `mm` los minutos y `ss` los segundos. Notar que el mes va en mayúscula y los minutos en minúscula: `"dd/MM/yyyy HH:mm:ss"`.

> **Nota:** un `Date` guarda el instante en UTC, pero se muestra usando la zona horaria del sistema. Por eso `new Date(0L)`, que es el 1 de enero de 1970 a las 00:00 UTC, se ve como el 31 de diciembre de 1969 en Argentina.

> **Importante:** `Date` es una clase antigua. La mayoría de sus métodos para obtener el día, el mes o el año (`getYear()`, `getMonth()`, `getDate()`) están **deprecados**, es decir, marcados como obsoletos: siguen funcionando pero no deben usarse, y el IDE los muestra tachados. Vas a encontrarte con `Date` en código ya existente, pero **para código nuevo conviene usar `LocalDate`**, que se explica a continuación.

## LocalDate

Desde la versión 1.8, Java provee el paquete `java.time` con clases mucho más simples y seguras para trabajar con fechas. La principal es `LocalDate`, que representa una fecha (año, mes y día) sin hora.

```java
import java.time.LocalDate;

LocalDate hoy = LocalDate.now(); // La fecha actual del sistema
LocalDate unaFecha = LocalDate.of(2026, 8, 25); // Una fecha determinada: año, mes y día

System.out.println(hoy);      // Muestra la fecha en formato ISO, por ejemplo: 2026-08-25
System.out.println(unaFecha); // 2026-08-25
```

Notar que `LocalDate` no se instancia con `new`: se obtiene invocando a sus métodos estáticos `now()` y `of()`.

### Obtener las partes de una fecha

```java
LocalDate fecha = LocalDate.of(2026, 8, 25);

int anio = fecha.getYear();          // 2026
int mes = fecha.getMonthValue();     // 8. El mes como número, del 1 al 12
int dia = fecha.getDayOfMonth();     // 25
int diaDelAnio = fecha.getDayOfYear(); // 237

int diasDelMes = fecha.lengthOfMonth(); // 31: la cantidad de días que tiene ese mes
boolean esBisiesto = fecha.isLeapYear(); // false: indica si el año es bisiesto
```

Los métodos `getMonth()` y `getDayOfWeek()` devuelven un [enum](./clases.html#enum) en lugar de un número:

```java
LocalDate fecha = LocalDate.of(2026, 8, 25);

System.out.println(fecha.getMonth());     // AUGUST
System.out.println(fecha.getDayOfWeek()); // TUESDAY
```

### Sumar y restar tiempo

Al igual que `String`, **`LocalDate` es inmutable**: ningún método modifica la fecha original, todos devuelven una fecha **nueva**. Por eso hay que asignar el resultado.

```java
LocalDate fecha = LocalDate.of(2026, 8, 25);

fecha.plusDays(10); // Devuelve una fecha nueva, pero se descarta: fecha sigue siendo 2026-08-25

LocalDate enDiezDias = fecha.plusDays(10);    // 2026-09-04
LocalDate elMesQueViene = fecha.plusMonths(1); // 2026-09-25
LocalDate elAnioPasado = fecha.minusYears(1);  // 2025-08-25
LocalDate haceUnaSemana = fecha.minusWeeks(1); // 2026-08-18
```

### Comparar fechas

```java
LocalDate hoy = LocalDate.now();
LocalDate navidad = LocalDate.of(2026, 12, 25);

boolean esAnterior = hoy.isBefore(navidad);  // true si hoy es anterior a navidad
boolean esPosterior = hoy.isAfter(navidad);  // true si hoy es posterior a navidad
boolean esLaMismaFecha = hoy.isEqual(navidad); // true si son la misma fecha
```

Para saber cuánto tiempo hay entre dos fechas contamos con `ChronoUnit` y `Period`:

```java
import java.time.LocalDate;
import java.time.Period;
import java.time.temporal.ChronoUnit;

LocalDate nacimiento = LocalDate.of(2000, 5, 10);
LocalDate hoy = LocalDate.now();

long diasVividos = ChronoUnit.DAYS.between(nacimiento, hoy); // La cantidad de días entre las dos fechas
int edad = Period.between(nacimiento, hoy).getYears();       // La cantidad de años completos entre las dos fechas
```

### Convertir entre texto y fecha

`LocalDate.parse()` convierte un texto en una fecha, y `format()` convierte una fecha en texto. Por defecto se usa el formato ISO (`aaaa-MM-dd`):

```java
LocalDate fecha = LocalDate.parse("2026-08-25"); // Convierte el texto en una fecha
String texto = fecha.toString(); // "2026-08-25"
```

Si necesitamos otro formato, usamos `DateTimeFormatter`, del paquete `java.time.format`:

```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");

LocalDate fecha = LocalDate.of(2026, 8, 25);
String fechaComoTexto = fecha.format(formato); // "25/08/2026"

LocalDate otraFecha = LocalDate.parse("31/12/2026", formato); // Convierte el texto usando el mismo formato
```

> **Importante:** si el texto no coincide con el formato esperado, el programa se interrumpe con el error `DateTimeParseException`. Cuando la fecha la ingresa el usuario, conviene validarla.

### Otras clases del paquete java.time

`LocalDate` guarda solo la fecha. Si además necesitamos la hora, contamos con dos clases más, que se usan de la misma manera:

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

LocalDate soloLaFecha = LocalDate.now();         // Por ejemplo: 2026-08-25
LocalTime soloLaHora = LocalTime.now();          // Por ejemplo: 19:30:45.123
LocalDateTime fechaYHora = LocalDateTime.now();  // Por ejemplo: 2026-08-25T19:30:45.123

LocalDateTime unMomento = LocalDateTime.of(2026, 8, 25, 19, 30); // año, mes, día, hora y minutos
```
