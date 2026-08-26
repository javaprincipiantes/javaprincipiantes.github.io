---
layout: default
---

[Volver](../)

# Un programa completo

Hasta acá vimos cada tema por separado. En esta sección armamos un programa de consola que los usa todos juntos: una veterinaria que permite registrar perros, modificarlos, filtrarlos y ver un resumen.

El programa usa [clases](./clases.html), [objetos](./clases.html#objetos), [atributos estáticos](./clases.html#métodos-y-atributos-estáticos), [enum](./clases.html#enum), [arrays](./arrays.html), [métodos](./metodos.html), [estructuras de decisión e iteración](./estructuras.html), [Scanner](./entrada-y-salida-por-consola.html#entrada-por-consola-scanner) y [String.format](./entrada-y-salida-por-consola.html#dar-formato-a-la-salida).

Así se ve funcionando:

```
 < Menu Principal >

1. Agregar perro
2. Modificar la edad de un perro
3. Mostrar perros por tamanio
4. Mostrar el perro de mayor edad
5. Mostrar resumen
6. Salir
Ingrese una opcion:
1

Ingrese el nombre:
Firulais

Ingrese la edad:
-3
La edad no puede ser negativa.

Ingrese la edad:
3

Ingrese: PEQUENIO o MEDIANO o GRANDE
GRANDE

Perro agregado!
```

## Cómo se organiza el proyecto

Un programa de consola no se escribe todo en un archivo. Los archivos se agrupan en [paquetes](./conceptos-basicos.html#introducción) según su responsabilidad, y la división más habitual separa dos cosas:

* **El dominio**: las clases que representan los elementos de la realidad y la lógica que opera sobre ellos. No sabe nada de la consola: no muestra mensajes ni lee lo que escribe el usuario.
* **La interfaz**: todo lo que tiene que ver con la consola. Muestra el menú, lee lo que el usuario escribe y le pide al dominio que haga el trabajo.

```
src/
└── com/javaprincipiantes/
    ├── dominio/
    │   ├── Perro.java
    │   ├── AdministradorDePerros.java
    │   └── enums/
    │       └── Tamanio.java
    └── interfaz/
        ├── Interfaz.java
        └── enums/
            └── MenuPrincipal.java
```

La ventaja de esta separación es concreta: si mañana quisiéramos que el programa dejara de ser de consola, el paquete `dominio` no habría que tocarlo.

> **Nota:** cada archivo empieza declarando a qué paquete pertenece, con la palabra reservada `package`, y debe estar en una carpeta con ese mismo nombre. Si una clase necesita usar otra de un paquete distinto, la importa con `import`.

## Paso 1: el enum Tamanio

Un perro puede ser pequeño, mediano o grande, y no hay más opciones. Cuando los valores posibles son una lista cerrada y conocida, lo que corresponde es un [enum](./clases.html#enum) y no un `String`: así el compilador nos impide escribir un tamaño que no existe.

```java
package com.javaprincipiantes.dominio.enums;

public enum Tamanio {
	PEQUENIO,
	MEDIANO,
	GRANDE
}
```

## Paso 2: la clase Perro

Es la entidad del dominio: representa un perro con sus características.

```java
package com.javaprincipiantes.dominio;

import com.javaprincipiantes.dominio.enums.Tamanio;

public class Perro {

	private int identificador;
	private String nombre;
	private int edad;
	private Tamanio tamanio;
	private static int proximoId = 0;

	public Perro(String nombre, int edad, Tamanio tamanio) {
		this.identificador = ++proximoId;
		this.nombre = nombre;
		this.edad = edad;
		this.tamanio = tamanio;
	}

	public int getIdentificador() {
		return this.identificador;
	}

	public String getNombre() {
		return this.nombre;
	}

	public void setNombre(String nombre) {
		this.nombre = nombre;
	}

	public int getEdad() {
		return this.edad;
	}

	public void setEdad(int edad) {
		this.edad = edad;
	}

	public Tamanio getTamanio() {
		return this.tamanio;
	}

	public void setTamanio(Tamanio tamanio) {
		this.tamanio = tamanio;
	}

	public void cumplirAnios() {
		this.edad++;
	}

	@Override
	public String toString() {
		return "Perro [identificador=" + this.identificador + ", nombre=" + this.nombre + ", edad=" + this.edad
				+ ", tamanio=" + this.tamanio + "]";
	}
}
```

Tres cosas para mirar:

* **El identificador es automático.** El atributo `proximoId` es [estático](./clases.html#métodos-y-atributos-estáticos): hay uno solo para toda la clase, compartido por todos los perros. Cada vez que se construye un perro, `++proximoId` lo incrementa **antes** de usarlo, así el primer perro queda con el identificador 1, el segundo con el 2, y así. Es la razón por la que el identificador no se recibe como parámetro: lo genera la propia clase.
* **Los atributos son privados** y se acceden con [getters y setters](./clases.html#getters-y-setters). No hay setter para `identificador`, justamente porque no queremos que nadie lo cambie desde afuera.
* **El `toString()`** devuelve el perro como texto. Es el que se usa cada vez que mostramos un perro por pantalla (ver [el método toString](./clases.html#el-método-tostring)).

## Paso 3: el AdministradorDePerros

Esta clase guarda los perros y resuelve toda la lógica. Es la que tiene el array.

```java
package com.javaprincipiantes.dominio;

import com.javaprincipiantes.dominio.enums.Tamanio;

public class AdministradorDePerros {

	private final int CANTIDAD_MAXIMA_DE_PERROS = 100;
	private final int EDAD_MAXIMA = 25;

	private String nombreDeLaVeterinaria;
	private Perro[] perros;

	public AdministradorDePerros(String nombreDeLaVeterinaria) {
		this.nombreDeLaVeterinaria = nombreDeLaVeterinaria;
		this.perros = new Perro[CANTIDAD_MAXIMA_DE_PERROS];
	}

	public boolean agregarPerro(String nombre, int edad, Tamanio tamanio) {
		int indice = 0;
		boolean agregado = false;

		while (indice < this.perros.length && !agregado) {
			if (this.perros[indice] == null) {
				this.perros[indice] = new Perro(nombre, edad, tamanio);
				agregado = true;
			}
			indice++;
		}
		return agregado;
	}

	public int modificarEdad(int identificador, int nuevaEdad) {
		Perro perro = this.buscarPerroPorIdentificador(identificador);

		if (perro == null) {
			return 1;
		}

		if (nuevaEdad < 0 || nuevaEdad > EDAD_MAXIMA) {
			return 2;
		}

		perro.setEdad(nuevaEdad);

		return 3;
	}

	private Perro buscarPerroPorIdentificador(int identificador) {
		int indice = 0;
		Perro perro = null;

		while (indice < this.perros.length && perro == null) {
			if (this.perros[indice] != null && this.perros[indice].getIdentificador() == identificador) {
				perro = this.perros[indice];
			}
			indice++;
		}
		return perro;
	}

	public Perro[] obtenerPerrosPorTamanio(Tamanio tamanio) {
		Perro[] perrosFiltrados = new Perro[this.perros.length];
		int posicion = 0;

		for (int indice = 0; indice < this.perros.length; indice++) {
			if (this.perros[indice] != null && this.perros[indice].getTamanio().equals(tamanio)) {
				perrosFiltrados[posicion++] = this.perros[indice];
			}
		}
		return perrosFiltrados;
	}

	public Perro obtenerPerroDeMayorEdad() {
		Perro perroDeMayorEdad = null;

		for (int indice = 0; indice < this.perros.length; indice++) {
			if (this.perros[indice] != null
					&& (perroDeMayorEdad == null || this.perros[indice].getEdad() > perroDeMayorEdad.getEdad())) {
				perroDeMayorEdad = this.perros[indice];
			}
		}
		return perroDeMayorEdad;
	}

	public double obtenerPromedioDeEdad() {
		double acumulador = 0;
		int cantidad = 0;

		for (int indice = 0; indice < this.perros.length; indice++) {
			if (this.perros[indice] != null) {
				acumulador += this.perros[indice].getEdad();
				cantidad++;
			}
		}

		if (cantidad == 0) {
			return 0;
		}

		return acumulador / cantidad;
	}

	public String obtenerResumen() {
		String resumen = "\nVeterinaria: " + this.nombreDeLaVeterinaria + "\n";
		resumen += "\nPerros pequenios: " + this.contarPerrosPorTamanio(Tamanio.PEQUENIO);
		resumen += "\nPerros medianos: " + this.contarPerrosPorTamanio(Tamanio.MEDIANO);
		resumen += "\nPerros grandes: " + this.contarPerrosPorTamanio(Tamanio.GRANDE);
		resumen += "\nPromedio de edad: " + String.format("%.2f", this.obtenerPromedioDeEdad());
		return resumen;
	}

	private int contarPerrosPorTamanio(Tamanio tamanio) {
		int contador = 0;

		for (int indice = 0; indice < this.perros.length; indice++) {
			if (this.perros[indice] != null && this.perros[indice].getTamanio().equals(tamanio)) {
				contador++;
			}
		}
		return contador;
	}
}
```

### El array y las posiciones libres

El array se crea con un tamaño fijo (`CANTIDAD_MAXIMA_DE_PERROS`), pero eso no significa que haya 100 perros: **las posiciones que todavía no cargamos valen `null`**. Ese `null` es la marca de "acá no hay nada".

De ahí salen dos reglas que se repiten en toda la clase:

1. Para **agregar**, buscamos la primera posición que valga `null`.
2. Para **recorrer**, salteamos las posiciones que valgan `null`, porque invocar un método sobre `null` interrumpe el programa con `NullPointerException`.

### Buscar con una bandera

Fijate en `agregarPerro` y en `buscarPerroPorIdentificador`: los dos recorren el array con un `while` cuya condición tiene **dos partes**.

```java
	while (indice < this.perros.length && perro == null) {
			if (this.perros[indice] != null && this.perros[indice].getIdentificador() == identificador) {
				perro = this.perros[indice];
			}
			indice++;
		}
```

La condición dice dos cosas a la vez: "seguí mientras queden posiciones **y** mientras no lo hayas encontrado". Cuando la bandera cambia, el bucle termina solo.

Es la alternativa a cortar el recorrido con `break`, y suele preferirse porque toda la información sobre cuándo termina el bucle está en un único lugar, la condición del `while`, en lugar de estar repartida entre la condición y una salida en el medio del bloque.

### Máximo, contador y acumulador

Los últimos métodos son los patrones que ya vimos en [operaciones con arrays](./arrays.html#operaciones-con-arrays), adaptados a un array de objetos:

* `obtenerPerroDeMayorEdad` es el patrón del **máximo**. Arranca en `null` y no en cero, y la condición `perroDeMayorEdad == null || ...` hace que el primer perro que encuentre sea el máximo provisorio. Devolver `null` cuando no hay perros es la forma de avisar que no hay respuesta posible.
* `contarPerrosPorTamanio` es un **contador**.
* `obtenerPromedioDeEdad` usa un **acumulador** más un contador. La verificación `if (cantidad == 0)` evita una división por cero.

## Paso 4: el enum MenuPrincipal

El menú también es una lista cerrada de opciones, así que también es un enum. Además de las opciones, guarda la descripción que se muestra por pantalla y resuelve dos tareas.

```java
package com.javaprincipiantes.interfaz.enums;

public enum MenuPrincipal {
	AGREGAR_PERRO("Agregar perro"),
	MODIFICAR_EDAD("Modificar la edad de un perro"),
	MOSTRAR_PERROS_POR_TAMANIO("Mostrar perros por tamanio"),
	MOSTRAR_EL_PERRO_DE_MAYOR_EDAD("Mostrar el perro de mayor edad"),
	MOSTRAR_RESUMEN("Mostrar resumen"),
	SALIR("Salir");

	private String descripcion;

	MenuPrincipal(String descripcion) {
		this.descripcion = descripcion;
	}

	public String obtenerDescripcion() {
		return this.descripcion;
	}

	public static String obtenerMenuPrincipal() {
		MenuPrincipal[] opciones = MenuPrincipal.values();
		String menuPrincipal = "\n < Menu Principal >\n";
		for (int indice = 0; indice < opciones.length; indice++) {
			menuPrincipal += String.format("\n%d. %s", (indice + 1), opciones[indice].obtenerDescripcion());
		}
		return menuPrincipal;
	}

	public static MenuPrincipal obtenerOpcionDeMenuPrincipal(int opcion) {
		MenuPrincipal[] opciones = MenuPrincipal.values();
		return opcion >= 1 && opcion <= opciones.length ? opciones[opcion - 1] : null;
	}
}
```

* **`obtenerMenuPrincipal()`** arma el texto del menú recorriendo las opciones con `values()`. Como el array empieza en 0 pero al usuario le mostramos desde 1, el número que se imprime es `i + 1`.
* **`obtenerOpcionDeMenuPrincipal(int)`** hace el camino inverso: convierte el número que ingresó el usuario en la opción correspondiente. Si el número está fuera de rango devuelve `null`, y de eso se encarga la interfaz.

La ventaja de tener el menú acá es que **las opciones se definen en un solo lugar**. Si agregamos una opción nueva al enum, el texto del menú se actualiza solo.

## Paso 5: la Interfaz

Es la clase que se ejecuta. Todo lo que tenga que ver con la consola vive acá.

```java
package com.javaprincipiantes.interfaz;

import java.util.Scanner;

import com.javaprincipiantes.dominio.AdministradorDePerros;
import com.javaprincipiantes.dominio.Perro;
import com.javaprincipiantes.dominio.enums.Tamanio;
import com.javaprincipiantes.interfaz.enums.MenuPrincipal;

public class Interfaz {

	private static Scanner scanner = new Scanner(System.in);

	public static void main(String[] args) {

		MenuPrincipal opcionIngresada = null;
		String nombreDeLaVeterinaria = ingresarString("\nIngrese el nombre de la veterinaria:");
		AdministradorDePerros administradorDePerros = new AdministradorDePerros(nombreDeLaVeterinaria);

		do {
			mostrarMensajePorConsola(MenuPrincipal.obtenerMenuPrincipal());
			opcionIngresada = ingresarOpcionDeMenuPrincipal();

			if (opcionIngresada == null) {
				mostrarMensajePorConsola("\nOpcion invalida.");
			} else {
				switch (opcionIngresada) {
				case AGREGAR_PERRO:
					agregarPerro(administradorDePerros);
					break;
				case MODIFICAR_EDAD:
					modificarEdad(administradorDePerros);
					break;
				case MOSTRAR_PERROS_POR_TAMANIO:
					mostrarPerrosPorTamanio(administradorDePerros);
					break;
				case MOSTRAR_EL_PERRO_DE_MAYOR_EDAD:
					mostrarElPerroDeMayorEdad(administradorDePerros);
					break;
				case MOSTRAR_RESUMEN:
					mostrarResumen(administradorDePerros);
					break;
				case SALIR:
					mostrarMensajePorConsola("\nHasta luego!");
					break;
				}
			}

		} while (!MenuPrincipal.SALIR.equals(opcionIngresada));

		scanner.close();
	}

	private static void agregarPerro(AdministradorDePerros administradorDePerros) {
		String nombre = ingresarString("\nIngrese el nombre: ");
		int edad = ingresarEdad();
		Tamanio tamanio = ingresarTamanio();

		boolean agregado = administradorDePerros.agregarPerro(nombre, edad, tamanio);

		if (agregado) {
			mostrarMensajePorConsola("\nPerro agregado!");
		} else {
			mostrarMensajePorConsola("\nPerro NO agregado.");
		}
	}

	private static void modificarEdad(AdministradorDePerros administradorDePerros) {
		int identificador = ingresarNumeroEntero("\nIngrese el identificador: ");
		int nuevaEdad = ingresarNumeroEntero("\nIngrese la nueva edad: ");

		int resultado = administradorDePerros.modificarEdad(identificador, nuevaEdad);

		switch (resultado) {
		case 1:
			mostrarMensajePorConsola("\nIdentificador no encontrado");
			break;
		case 2:
			mostrarMensajePorConsola("\nLa edad ingresada no es valida");
			break;
		case 3:
			mostrarMensajePorConsola("\nEdad modificada!");
			break;
		}
	}

	private static void mostrarPerrosPorTamanio(AdministradorDePerros administradorDePerros) {
		Tamanio tamanio = ingresarTamanio();
		Perro[] perros = administradorDePerros.obtenerPerrosPorTamanio(tamanio);
		mostrarPerros(perros);
	}

	private static void mostrarElPerroDeMayorEdad(AdministradorDePerros administradorDePerros) {
		Perro perro = administradorDePerros.obtenerPerroDeMayorEdad();

		if (perro != null) {
			mostrarMensajePorConsola("\n" + perro.toString());
		} else {
			mostrarMensajePorConsola("\nNo hay perros");
		}
	}

	private static void mostrarResumen(AdministradorDePerros administradorDePerros) {
		mostrarMensajePorConsola(administradorDePerros.obtenerResumen());
	}

	private static void mostrarPerros(Perro[] perros) {
		for (int indice = 0; indice < perros.length; indice++) {
			if (perros[indice] != null) {
				mostrarMensajePorConsola(perros[indice].toString());
			}
		}
	}

	private static int ingresarEdad() {
		int edad;

		do {
			edad = ingresarNumeroEntero("\nIngrese la edad: ");

			if (edad < 0) {
				mostrarMensajePorConsola("La edad no puede ser negativa.");
			}
		} while (edad < 0);

		return edad;
	}

	private static int ingresarNumeroEntero(String mensaje) {
		mostrarMensajePorConsola(mensaje);
		return scanner.nextInt();
	}

	private static String ingresarString(String mensaje) {
		mostrarMensajePorConsola(mensaje);
		return scanner.next();
	}

	private static Tamanio ingresarTamanio() {
		return Tamanio.valueOf(ingresarString("\nIngrese: PEQUENIO o MEDIANO o GRANDE").trim().toUpperCase());
	}

	private static MenuPrincipal ingresarOpcionDeMenuPrincipal() {
		int opcion = ingresarNumeroEntero("Ingrese una opcion:");
		return MenuPrincipal.obtenerOpcionDeMenuPrincipal(opcion);
	}

	private static void mostrarMensajePorConsola(String mensaje) {
		System.out.println(mensaje);
	}
}
```

### El bucle principal

El menú es un [do-while](./estructuras.html#do-while) con un [switch](./estructuras.html#switch) adentro: se muestra al menos una vez y se repite hasta que el usuario elige salir.

```java
		do {
			mostrarMensajePorConsola(MenuPrincipal.obtenerMenuPrincipal());
			opcionIngresada = ingresarOpcionDeMenuPrincipal();

			if (opcionIngresada == null) {
				mostrarMensajePorConsola("\nOpcion invalida.");
			} else {
				switch (opcionIngresada) {
				case AGREGAR_PERRO:
					agregarPerro(administradorDePerros);
					break;
				case MODIFICAR_EDAD:
					modificarEdad(administradorDePerros);
					break;
				case MOSTRAR_PERROS_POR_TAMANIO:
					mostrarPerrosPorTamanio(administradorDePerros);
					break;
				case MOSTRAR_EL_PERRO_DE_MAYOR_EDAD:
					mostrarElPerroDeMayorEdad(administradorDePerros);
					break;
				case MOSTRAR_RESUMEN:
					mostrarResumen(administradorDePerros);
					break;
				case SALIR:
					mostrarMensajePorConsola("\nHasta luego!");
					break;
				}
			}

		} while (!MenuPrincipal.SALIR.equals(opcionIngresada));
```

Dos detalles importantes:

* **La verificación de `null`.** Si el usuario ingresa un número que no corresponde a ninguna opción, `obtenerOpcionDeMenuPrincipal` devuelve `null`. Hacer `switch` sobre `null` interrumpe el programa con `NullPointerException`, así que hay que verificarlo antes.
* **`MenuPrincipal.SALIR.equals(opcionIngresada)`.** La condición se escribe con la constante a la izquierda a propósito: si `opcionIngresada` fuera `null`, escribirlo al revés daría error. Así, la comparación es segura.

### Los métodos de ingreso

Todo lo que lee el usuario pasa por un método chico y con un solo objetivo: `ingresarString`, `ingresarNumeroEntero`, `ingresarTamanio`. Eso evita repetir `System.out.println` y `scanner.next()` en cada lugar donde hace falta un dato.

La validación de la edad es el único caso que necesita repetir el pedido, y para eso usamos un `do-while`: la edad hay que pedirla al menos una vez antes de poder evaluarla.

```java
	private static int ingresarEdad() {
		int edad;

		do {
			edad = ingresarNumeroEntero("\nIngrese la edad: ");

			if (edad < 0) {
				mostrarMensajePorConsola("La edad no puede ser negativa.");
			}
		} while (edad < 0);

		return edad;
	}
```

## Compilar y ejecutar

Desde un [IDE](https://es.wikipedia.org/wiki/Entorno_de_desarrollo_integrado), se ejecuta la clase `Interfaz`, que es la que tiene el `main`.

Desde una terminal, parados en la carpeta que contiene `src`:

```bash
# Compila todo el código fuente y deja los .class en la carpeta bin
javac -d bin $(find src -name "*.java")

# Ejecuta indicando el paquete completo de la clase que tiene el main
java -cp bin com.javaprincipiantes.interfaz.Interfaz
```

## Para seguir practicando

Sobre este mismo programa se pueden agregar opciones al menú. Cada una es un método nuevo en `AdministradorDePerros` y un `case` nuevo en el enum y en el `switch`:

* Una opción para que un perro cumpla años. El método `cumplirAnios` ya está en la clase `Perro` y no lo usamos: hay que buscar el perro por identificador e invocarlo.
* Una opción que muestre el perro más joven, con la lógica del mínimo.
* Una opción que muestre los perros ordenados por edad. Requiere recorrer el array comparando de a pares e intercambiar posiciones con una variable auxiliar.
* Una opción para eliminar un perro. Es la más interesante: hay que decidir qué hacer con el `null` que queda en el medio del array.

[Volver](../)
