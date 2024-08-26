---
layout: default
---

[Volver](../)

# Introducción a Java

## ¿Qué es Java?

Java es un lenguaje de programación de alto nivel que permite el desarrollo de aplicaciones, ya sean básicas (de consola) o empresariales (web, mobile).
Tiene un propósito general, es fuertemente tipado, compilado y orientado a objetos.

Es un lenguaje multiplataforma y multidispositivo. Su paradigma es: "Write Once Run Anywhere" (WORA). Escibilo una vez, correlo en cualquier lugar.
De esta manera, podemos escribir el código necesario para nuestro programa Java y luego ejecutarlo en distintas platarformas como Windows, MacOS o Linux.

## ¿Cómo funciona?

Java funciona con ciertos ejes. Escribiremos nuestro código fuente (archivos de extensión .java), posibles de leer por nosotros. Luego los podremos compilar para generar el [bytecode](https://es.wikipedia.org/wiki/Bytecode_Java) (archivos con extensión .class, los cuales no son legibles a simple vista), y así poder ejecutar nuestro programa con la máquina virtual de Java (Java Virtual Machine - [JVM](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual_Java)).

El bytecode, contiene las instrucciones que la máquina virtual de Java deberá interpertar para ejecutar el programa.

Para desarrollar un programa en Java, debemos instalar alguna versión de java (se recomienda utilizar desde la versión 1.8 en adelante).
Dicha instalación nos proveerá de herramientas de desarrollo para la creación de programas en Java (Java Development Kit - [JDK](https://es.wikipedia.org/wiki/Java_Development_Kit)) y de la máquina virtual para el sistema operativo en el cual trabajemos para ejecutar nuestro programa (JVM).

La instalación de Java también nos provee de un entorno de ejecución de Java (Java Runtime Environment - [JRE](https://es.wikipedia.org/wiki/Java_Runtime_Environment)), quien nos permite ejercutar en definitiva nuestro programa y actúa como "intermediario" entre el sistema operativo y Java.

## Programación orientada a objetos ([POO](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos))

Es un paradigma que nos permite representar elementos de la realidad en un lenguaje de programación, dando lugar a entidades que poseen un estado (atributos) y un comportamiento (métodos).

### Pilares de la programación orientada a objetos

#### [Abstracción](https://es.wikipedia.org/wiki/Abstracci%C3%B3n_(inform%C3%A1tica))

Representación en código de elementos de la realidad.

#### [Encapsulamiento](https://es.wikipedia.org/wiki/Encapsulamiento_(inform%C3%A1tica))

Agrupación de datos, permiso o restricción de acceso a los mismos.

#### [Polimorfismo](https://es.wikipedia.org/wiki/Polimorfismo_(inform%C3%A1tica))

Posibilida de enviar mensajes sintácticamente iguales a objetos de tipos distintos.

#### [Herencia](https://es.wikipedia.org/wiki/Herencia_(inform%C3%A1tica))

Establece una jerarquía que nos permite centralizar características (atributos o datos) o comportamiento (métodos o acciones) en un sitio mas general, para luego extenderlos en elementos más específicos.

[Volver](../)