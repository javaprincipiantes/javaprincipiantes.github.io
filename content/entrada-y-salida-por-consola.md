---
layout: default
---

[Volver](../)

# Entrada y salida por consola

Cuando desarrollamos programas de consola, es posible permitir el ingreso de datos desde la consola provista por el [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado) (entorno de desarrollo integrado), o bien, desde el programa ejecutado desde el sistema operativo (en Windows [CMD](https://es.wikipedia.org/wiki/S%C3%ADmbolo_del_sistema_de_Windows), en Linux [Shell de Unix](https://es.wikipedia.org/wiki/Shell_de_Unix)).

Para mostrar texto en la consola del IDE (por ejemplo), Java nos provee de un método:

```java
System.out.println("Mi primer mensaje por consola!");
```

Con este método podemos, por ejemplo, indicarle al usuario que ingrese información.

Cuando nos interese mostrar un mensaje de error, podemos usar el siguiente código:

```java
System.err.println("Mensaje de error.");
```

### Coloreando los mensajes en la consola

Para cambiar el color del texto en la consola, el fondo, mostrar texto en negrita o subrayado, debemos anteponer un código de color, antes del texto deseado.

Luego, para devolver el estilo original del texto, es necesario hacer un reset de dicho código.

```java
String textoAzul = "\033[0;34m";
String reset = "\033[0m";
System.out.println(textoAzul + "Mi primer mensaje por consola!" + reset); // Mostrará el texto en azul para luego devolver el color original
```

> **Nota**: En caso de no realizar el reset, la consola continua mostrando los mensajes con el último formato establecido. 

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

// Colors de texto Bold (en negrita)
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

// Colores Bold (en negrita) de alta intensidad
String negroBoldAltaIntensidad = "\033[1;90m"; 
String rojoBoldAltaIntensidad = "\033[1;91m";   
String verdeBoldAltaIntensidad = "\033[1;92m"; 
String yellowBoldAltaIntensidad = "\033[1;93m";
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
> **Nota:** Estas sentencias de código debe estar incluidas dentro de un método.

Para el ingreso de información, en programas de consola, utilizaremos la clase `Scanner`.

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);
```

Un objeto de tipo Scanner, posee varios métodos específicos que nos permiten ingresar valores de distintos tipos de dato (específicos).

* Para solicitar el ingreso de una palabra (String):

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese una palabra:"); // Mensaje que sugiere el ingreso de información
String palabra = scanner.next(); 
```

* Para solicitar el ingreso de texto (String, mas de una palabra con espacios por ejemplo):

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese texto:"); // Mensaje que sugiere el ingreso de información
String texto = scanner.nextLine(); 
```

* Para solicitar el ingreso de un número entero de tipo short:

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero (short):"); // Mensaje que sugiere el ingreso de información
short numero = scanner.nextShort(); 
```

* Para solicitar el ingreso de un número entero de tipo byte:

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero (byte):"); // Mensaje que sugiere el ingreso de información
byte numero = scanner.nextByte();
```

* Para solicitar el ingreso de un número entero de tipo int:

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero (int):"); // Mensaje que sugiere el ingreso de información
int numero = scanner.nextInt();
```

* Para solicitar el ingreso de un número entero de tipo long:

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero (long):"); // Mensaje que sugiere el ingreso de información
long numero = scanner.nextLong();
```

* Para solicitar el ingreso de un número entero con decimales (float):

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero con decimales (float):"); // Mensaje que sugiere el ingreso de información
float numero = scanner.nextFloat();
```

* Para solicitar el ingreso de un número entero con decimales (float):

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero con decimales (double):"); // Mensaje que sugiere el ingreso de información
double numero = scanner.nextDouble();
```

* Para solicitar el ingreso de un caracter:

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese un numero entero con decimales (double):"); // Mensaje que sugiere el ingreso de información
char caracter = scanner.next().charAt(0); // La clase Scanner no provee de un método para ingresar un caracter, por este motivo, podemos invocar al método charAt(0), donde 0 (cero) es la posición inicial de la palabra ingresada. El resto de los caracteres en la palabra es ignorado. 
```

* Para solicitar el ingreso de un valor de verdad (true o false):

```java
// Definición y creación de un objeto de tipo Scanner
Scanner scanner = new Scanner(System.in);

System.out.println("Ingrese true o false:"); // Mensaje que sugiere el ingreso de información
boolean valorDeVerdad = scanner.nextBoolean(); // Se debe ingresar la palabra completa
```

> **Importante:** Luego de cada ingreso de información, en caso de los ingresos de tipo String, se incluye el caracter de fin de línea: `'\n'`.
Cuando invocamos a un método que no sea para ingresar un String, como scanner.nextInt(), no se incluye el caracter de fin de línea, con lo cual es necesario invocar al método scanner.nextLine() luego de scanner.nextInt() (como ejemplo), para no tener un error de ingreso de información (si luego se necesita ingresar un String). Esto no genera ningún efecto negativo sobre el funcionamiento. Ver este [enlace](https://stackoverflow.com/questions/23450524/java-scanner-doesnt-wait-for-user-input).

[Volver](../)