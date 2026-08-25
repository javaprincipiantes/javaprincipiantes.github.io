---
layout: default
---

[Volver](../)

# Entrada y salida por consola

Cuando desarrollamos programas de consola, es posible mostrar información y permitir el ingreso de datos desde la consola provista por el [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado) (entorno de desarrollo integrado), o bien desde el programa ejecutado en el sistema operativo (en Windows [CMD](https://es.wikipedia.org/wiki/S%C3%ADmbolo_del_sistema_de_Windows), en Linux [Shell de Unix](https://es.wikipedia.org/wiki/Shell_de_Unix)).

## Salida por consola (println)

Para mostrar texto en la consola, Java nos provee del método `System.out.println`:

```java
System.out.println("Mi primer mensaje por consola!");
```

Con este método podemos, por ejemplo, indicarle al usuario que ingrese información, o mostrar el contenido de una variable:

```java
int edad = 21;
System.out.println("La edad es: " + edad); // Muestra: La edad es: 21
```

`println` agrega un salto de línea al final. Si no queremos ese salto, podemos usar `print`:

```java
System.out.print("Hola ");
System.out.print("mundo!"); // Los dos mensajes se muestran en la misma línea: Hola mundo!
```

Cuando nos interese mostrar un mensaje de error, podemos usar el siguiente código:

```java
System.err.println("Mensaje de error.");
```

> **Nota:** `System.out` y `System.err` pertenecen al paquete `java.lang`, así que no necesitan ningún `import`.

## Entrada por consola (Scanner)

Para el ingreso de información en programas de consola utilizaremos la clase `Scanner`. Al no pertenecer al paquete `java.lang`, **es obligatorio importarla** al principio del archivo (ver [imports](./introduccion-a-java.html#imports)).

```java
import java.util.Scanner;

public class MiPrograma {

    public static void main(String[] args) {
        // Declaración y creación de un objeto de tipo Scanner
        Scanner scanner = new Scanner(System.in);

        System.out.println("Ingrese su nombre:");
        String nombre = scanner.nextLine();

        System.out.println("Hola " + nombre + "!");

        scanner.close(); // Cerramos el Scanner cuando ya no lo necesitamos
    }
}
```

En los ejemplos que siguen se muestra solo el fragmento relevante, pero todos necesitan el `import` y estar dentro de un método, tal como en el programa anterior.

Un objeto de tipo Scanner posee varios métodos, uno por cada tipo de dato que queramos leer.

* Para solicitar el ingreso de una palabra (String, sin espacios):

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese una palabra:"); // Mensaje que le indica al usuario qué debe ingresar
String palabra = scanner.next();
```

* Para solicitar el ingreso de texto (String, más de una palabra con espacios por ejemplo):

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese texto:");
String texto = scanner.nextLine();
```

* Para solicitar el ingreso de un número entero de tipo byte:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número entero (byte):");
byte numero = scanner.nextByte();
```

* Para solicitar el ingreso de un número entero de tipo short:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número entero (short):");
short numero = scanner.nextShort();
```

* Para solicitar el ingreso de un número entero de tipo int:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número entero (int):");
int numero = scanner.nextInt();
```

* Para solicitar el ingreso de un número entero de tipo long:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número entero (long):");
long numero = scanner.nextLong();
```

* Para solicitar el ingreso de un número con decimales de tipo float:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número con decimales (float):");
float numero = scanner.nextFloat();
```

* Para solicitar el ingreso de un número con decimales de tipo double:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un número con decimales (double):");
double numero = scanner.nextDouble();
```

* Para solicitar el ingreso de un caracter:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un caracter:");
// La clase Scanner no provee un método para leer un solo caracter. Por eso leemos una palabra
// e invocamos al método charAt(0), donde 0 (cero) es la posición inicial. El resto de los
// caracteres de la palabra ingresada se ignora.
char caracter = scanner.next().charAt(0);
```

* Para solicitar el ingreso de un valor de verdad (true o false):

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese true o false:");
boolean valorDeVerdad = scanner.nextBoolean(); // Se debe ingresar la palabra completa
```

> **Importante:** cuando el usuario ingresa un dato, además del dato queda pendiente el caracter de fin de línea (`'\n'`) que genera la tecla Enter. Los métodos como `nextInt()` o `nextDouble()` leen el número pero **no** consumen ese fin de línea. Si a continuación invocamos a `nextLine()`, este devuelve una cadena vacía sin darle oportunidad al usuario de escribir nada. La solución es agregar un `scanner.nextLine()` extra después de `nextInt()` para descartar el fin de línea pendiente. Ver este [enlace](https://stackoverflow.com/questions/23450524/java-scanner-doesnt-wait-for-user-input).

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese su edad:");
int edad = scanner.nextInt();
scanner.nextLine(); // Descarta el fin de línea que dejó pendiente nextInt()

System.out.println("Ingrese su nombre completo:");
String nombre = scanner.nextLine(); // Ahora sí espera el ingreso del usuario
```

## Coloreando los mensajes en la consola

Para cambiar el color del texto en la consola, el fondo, o mostrar texto en negrita o subrayado, debemos anteponer un código de color al texto deseado.

Luego, para devolver el estilo original del texto, es necesario hacer un reset de dicho código.

```java
String textoAzul = "\033[0;34m";
String reset = "\033[0m";
System.out.println(textoAzul + "Mi primer mensaje por consola!" + reset); // Muestra el texto en azul y luego devuelve el color original
```

> **Nota:** en caso de no realizar el reset, la consola continúa mostrando los mensajes con el último formato establecido.

> **Nota:** no todas las consolas interpretan estos códigos. Si en lugar del color aparecen caracteres extraños, la consola en uso no los soporta.

A continuación tenemos algunos de los códigos de colores y para qué se utilizan.

```java
String reset = "\033[0m";  // Reset al color original

// Colores de texto comunes
String negro = "\033[0;30m";
String rojo = "\033[0;31m";
String verde = "\033[0;32m";
String amarillo = "\033[0;33m";
String azul = "\033[0;34m";
String violeta = "\033[0;35m";
String cyan = "\033[0;36m";
String blanco = "\033[0;37m";

// Colores de texto en negrita (bold)
String negroBold = "\033[1;30m";
String rojoBold = "\033[1;31m";
String verdeBold = "\033[1;32m";
String amarilloBold = "\033[1;33m";
String azulBold = "\033[1;34m";
String violetaBold = "\033[1;35m";
String cyanBold = "\033[1;36m";
String blancoBold = "\033[1;37m";

// Colores subrayados
String negroSubrayado = "\033[4;30m";
String rojoSubrayado = "\033[4;31m";
String verdeSubrayado = "\033[4;32m";
String amarilloSubrayado = "\033[4;33m";
String azulSubrayado = "\033[4;34m";
String violetaSubrayado = "\033[4;35m";
String cyanSubrayado = "\033[4;36m";
String blancoSubrayado = "\033[4;37m";

// Colores de fondo
String fondoNegro = "\033[40m";
String fondoRojo = "\033[41m";
String fondoVerde = "\033[42m";
String fondoAmarillo = "\033[43m";
String fondoAzul = "\033[44m";
String fondoVioleta = "\033[45m";
String fondoCyan = "\033[46m";
String fondoBlanco = "\033[47m";

// Colores de texto de alta intensidad
String negroAltaIntensidad = "\033[0;90m";
String rojoAltaIntensidad = "\033[0;91m";
String verdeAltaIntensidad = "\033[0;92m";
String amarilloAltaIntensidad = "\033[0;93m";
String azulAltaIntensidad = "\033[0;94m";
String violetaAltaIntensidad = "\033[0;95m";
String cyanAltaIntensidad = "\033[0;96m";
String blancoAltaIntensidad = "\033[0;97m";

// Colores en negrita de alta intensidad
String negroBoldAltaIntensidad = "\033[1;90m";
String rojoBoldAltaIntensidad = "\033[1;91m";
String verdeBoldAltaIntensidad = "\033[1;92m";
String amarilloBoldAltaIntensidad = "\033[1;93m";
String azulBoldAltaIntensidad = "\033[1;94m";
String violetaBoldAltaIntensidad = "\033[1;95m";
String cyanBoldAltaIntensidad = "\033[1;96m";
String blancoBoldAltaIntensidad = "\033[1;97m";

// Fondos de alta intensidad
String fondoAltaIntensidadNegro = "\033[0;100m";
String fondoAltaIntensidadRojo = "\033[0;101m";
String fondoAltaIntensidadVerde = "\033[0;102m";
String fondoAltaIntensidadAmarillo = "\033[0;103m";
String fondoAltaIntensidadAzul = "\033[0;104m";
String fondoAltaIntensidadVioleta = "\033[0;105m";
String fondoAltaIntensidadCyan = "\033[0;106m";
String fondoAltaIntensidadBlanco = "\033[0;107m";
```

> **Nota:** estas sentencias de código deben estar incluidas dentro de un método.

[Volver](../)
