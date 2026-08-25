---
layout: default
---

[Volver](../)

# Introducción a Java

## ¿Qué es Java?

Java es un lenguaje de programación de alto nivel que permite el desarrollo de aplicaciones, ya sean básicas (de consola) o empresariales (web, mobile).
Tiene un propósito general, es fuertemente tipado, compilado y orientado a objetos.

Es un lenguaje multiplataforma y multidispositivo. Su paradigma es: "Write Once Run Anywhere" (WORA). Escribilo una vez, correlo en cualquier lugar.
De esta manera, podemos escribir el código necesario para nuestro programa Java y luego ejecutarlo en distintas plataformas como Windows, MacOS o Linux.

## ¿Cómo funciona?

Java funciona con ciertos ejes. Escribiremos nuestro código fuente (archivos de extensión .java), posibles de leer por nosotros. Luego los podremos compilar para generar el [bytecode](https://es.wikipedia.org/wiki/Bytecode_Java) (archivos con extensión .class, los cuales no son legibles a simple vista), y así poder ejecutar nuestro programa con la máquina virtual de Java (Java Virtual Machine - [JVM](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual_Java)).

El bytecode contiene las instrucciones que la máquina virtual de Java deberá interpretar para ejecutar el programa.

Para desarrollar un programa en Java, debemos instalar alguna versión de Java (se recomienda utilizar desde la versión 1.8 en adelante).
Dicha instalación nos proveerá de herramientas de desarrollo para la creación de programas en Java (Java Development Kit - [JDK](https://es.wikipedia.org/wiki/Java_Development_Kit)) y de la máquina virtual para el sistema operativo en el cual trabajemos para ejecutar nuestro programa (JVM).

La instalación de Java también nos provee de un entorno de ejecución de Java (Java Runtime Environment - [JRE](https://es.wikipedia.org/wiki/Java_Runtime_Environment)), que nos permite ejecutar en definitiva nuestro programa y actúa como "intermediario" entre el sistema operativo y Java.

## Tu primer programa

Todo el código Java vive dentro de una [clase](./clases.html), y todo código que se ejecuta vive dentro de un [método](./metodos.html). Por eso, ningún ejemplo de esta guía puede correr por sí solo: siempre hay que ubicarlo dentro de un programa como el que sigue.

```java
public class MiPrimerPrograma {

    public static void main(String[] args) {
        System.out.println("Hola mundo!");
    }
}
```

Repasemos cada parte:

* `public class MiPrimerPrograma` define la clase. **El nombre de la clase debe coincidir con el nombre del archivo**: este código va en un archivo llamado `MiPrimerPrograma.java`.
* `public static void main(String[] args)` es el método `main`, el punto de entrada del programa. Es el método que la JVM busca y ejecuta cuando corremos nuestro programa. Su firma es siempre exactamente esa; si cambiamos alguna palabra, la JVM no lo encuentra.
* `System.out.println("Hola mundo!")` muestra un texto por consola (ver [entrada y salida por consola](./entrada-y-salida-por-consola.html)).

Cada vez que en esta guía veas un fragmento suelto, como:

```java
int numero = 10;
System.out.println(numero);
```

entendé que en un programa real va dentro del `main` (o dentro de otro método invocado desde el `main`):

```java
public class MiPrimerPrograma {

    public static void main(String[] args) {
        int numero = 10;
        System.out.println(numero);
    }
}
```

### Compilar y ejecutar

Si usamos un [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado), alcanza con el botón de "Run". Desde una terminal, son dos pasos:

```bash
# Compila MiPrimerPrograma.java y genera MiPrimerPrograma.class (el bytecode)
javac MiPrimerPrograma.java

# Ejecuta el programa con la JVM (se indica el nombre de la clase, sin la extensión)
java MiPrimerPrograma
```

### Imports

Algunas clases que usaremos (como `Scanner` o `Random`) no están disponibles automáticamente: hay que importarlas al principio del archivo, antes de la definición de la clase.

```java
import java.util.Scanner;

public class MiPrimerPrograma {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese su nombre:");
        String nombre = scanner.nextLine();
        System.out.println("Hola " + nombre + "!");
        scanner.close();
    }
}
```

> **Nota:** las clases del paquete `java.lang` (como `String`, `Math`, `Integer` o `System`) no necesitan import, están siempre disponibles. Los IDE suelen agregar los imports que faltan de manera automática.

## Programación orientada a objetos ([POO](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos))

Es un paradigma que nos permite representar elementos de la realidad en un lenguaje de programación, dando lugar a entidades que poseen un estado (atributos) y un comportamiento (métodos).

### Pilares de la programación orientada a objetos

#### [Abstracción](https://es.wikipedia.org/wiki/Abstracci%C3%B3n_(inform%C3%A1tica))

Representación en código de elementos de la realidad.

#### [Encapsulamiento](https://es.wikipedia.org/wiki/Encapsulamiento_(inform%C3%A1tica))

Agrupación de datos, permiso o restricción de acceso a los mismos.

#### [Polimorfismo](https://es.wikipedia.org/wiki/Polimorfismo_(inform%C3%A1tica))

Posibilidad de enviar mensajes sintácticamente iguales a objetos de tipos distintos.

#### [Herencia](https://es.wikipedia.org/wiki/Herencia_(inform%C3%A1tica))

Establece una jerarquía que nos permite centralizar características (atributos o datos) o comportamiento (métodos o acciones) en un sitio más general, para luego extenderlos en elementos más específicos.

> **Nota:** los cuatro pilares se ponen en práctica en la sección de [clases](./clases.html).

[Volver](../)
