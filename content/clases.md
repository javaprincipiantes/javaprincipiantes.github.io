---
layout: default
---

[Volver](../)

# Clases

Las clases son el principal elemento para representar un elemento de la realidad en código ([Abstracción](https://es.wikipedia.org/wiki/Abstracci%C3%B3n_(inform%C3%A1tica)) de POO). Definen las características (atributos) y comportamiento (métodos) que poseerán todos los objetos creados a partir de la clase que definimos.

## Modificadores de acceso

Un modificador de acceso establece si se permite el acceso (el nivel de acceso o si no está permitido) a una clase o elemento de una clase, como pueden ser atributos o métodos. 

Java provee de cuatro modificadores de acceso:
* public: el elemento es de acceso público. Aplicado sobre la definición de una clase, nos permite que la misma sea utilizada en todo el proyecto.
* private: generalmente utilizado sobre los atributos de una clase (también sobre algunos métodos), no permite el acceso directo a alguno de estos elementos de la clase, por fuera de la clase. Es el nivel de acceso mas restrictivo.
* protected: mas utilizado al implementar herencia, permite que los atributos o métodos de una superclase sean accedidos por una clase que herede de una superclase.
* default: cuando no se define algun modificador de acceso de los anteriores, se activa este modificador de acceeso. Permite el acceso a todas las clases dentro del mismo paquete (package).

## Constructor

Es una especie de método (aunque tiene su propia forma de definirse), que nos permite inicializar los objetos que se creen a partir de la clase que definimos. Podemos tener más de un constructor.

El constructor más comun es el constructor que no recibe parámetros. Este constructor está implícito, salvo que se defina un constructor que posea parámetros (al menos uno), en ese caso, debemos definir (escribir) el constructor vacío.

Un constructor posee un modificador de acceso (generalmente public) y lleva como nombre el mismo nombre de la clase. Posee además, dos llaves, una de apertura y otra de cierre que definen las sentencias que deben ejecutarse al ser utilizado dicho constructor.

```java
// Considerando que la clase se llama Perro, definimos un constructor sin parámetros

public Perro () {
    // Lineas de código del constructor
}
```

Como se dijo antes, es posible tener mas de un constructor (sobrecarga de constructor). En caso de definir un nuevo constructor, debe recibir al menos un parámetro (en comparación con el constructor que no recibe parámetros), para no obtener un error de compilación:

```java
// Considerando que la clase se llama Perro, definimos un constructor con un parámetro

public Perro (String nombre) {
    // Lineas de código del constructor
}
```

Si necesitamos definir otro constructor, y considerando que ya existe el constructor vacío y el que recibe un parámetro, el nuevo constructor debe recibir distintos parámetros (quizás más de uno), o bien, no en el mismo orden con respecto a los tipos de dato (los nombres de los parámetros son ignorados).

```java
// Considerando que la clase se llama Perro, definimos un constructor con mas de un parámetro

public Perro (String nombre, int edad) {
    // Lineas de código del constructor
}
```

Un constructor puede recibir como parámetro un tipo de dato personalizado (algún objeto creado a partir de una clase definida por nosotros):

```java
// Considerando que la clase se llama Perro, definimos un constructor con mas de un parámetro y recibiendo un parámetro de una clase personalizada

public Perro (String nombre, int edad, Persona duenio) {
    // Lineas de código del constructor
}
```

Es importante saber, que en la creación de un objeto (explicado mas abajo), solo se utiliza un constructor.

## Definición de clase personalizada

Para definir una clase, debemos indicar un modificador de acceso (el más común es `public`), seguido de la palabra reservada `class` y un nombre de clase como `Perro`.

La nomenclatura de clases, por convención, es [PascalCase](https://es.wikipedia.org/wiki/Camel_case) donde la primera letra de la palabra se escribe en mayúscula y las siguientes en minúscula. Si existe una segunda palabra, esta debe comenzar en mayúscula y el resto de las letras en minúscula: `AutoVolador`.
Las clases incluyen sus propias llaves de apertura y cierre, las cuales son obligatorias.

Las clases no poseen paréntesis para recibir parámetros (como los métodos), esta tarea (recibir parámetros) es relegada a los constructores.

```java
public class Perro {
    // Contenido de la clase
}
```
Las clases suelen (quizás por convención) tener al menos tres secciones, donde escribiremos los elementos que contiene.

Al principio de la clase, se suelen escribir los atributos (variables) y constantes que pueda tener la clase. Los atributos, en Java, deben tener un modificador de acceso `private` para cumplir con el concepto de [encapsulamiento](./introduccion-a-java.html). Los atributos y constantes estarán presentes en todos los objetos que se creen a partir de la clase que definimos.

Las constantes definidas en la clase, pueden ser `private` o `public`, según sea necesario.

Los atributos de una clase, raramente son inicializados al momento de su definición, esta tarea de "inicialización", se deja para cada constructor.

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

}
```

Siguiendo con el orden de los elementos en una clase, como segundo se suelen escibir los constructores.

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombreDelPerro, int edadDelPerro) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        nombre = nombreDelPerro;
        edad = edadDelPerro;
        duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombreDelPerro, int edadDelPerro, Persona duenioDelPerro) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        nombre = nombreDelPerro;
        edad = edadDelPerro;
        duenio = duenioDelPerro;
    }

}
```

> **Nota:** es importante notar que los parámetros tienen un nombre distinto al nombre de los atributos.

Es común que los constructores reciban parámetros con el mismo nombre que los atributos de la clase. En este caso una asignación como la siguiente NO tiene efecto, ya que,  representan a la misma variable (intenta asignar el contenido a si misma).

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro (String nombre, int edad, Persona duenio) {
        // Estas asignaciones no tiene efecto
        nombre = nombre;
        edad = edad;
        duenio = duenio;
    }

}
```

En el ejemplo anterior, no se puede determinar qué se asigna a quién. Para solventar este escenario, se nos provee de la palabra reservada `this`, la cual solo puede utizarse dentro de las clases para hacer referencia a un atributo o método propio de la clase, con la salvedad de que _el atributo o método no debe ser estático_.

La palabra reservada `this` debe estar seguida de un punto `this.` y luego el atributo o método al cual nos queremos referir.

> **Nota:** Es recomendable siempre usar `this.` para referirse a un elemento propio de la clase, no hay quien pierde...

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro (String nombre, int edad, Persona duenio) {
        // Estas asignaciones son válidas por incluir la palabra reservada this
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

}
```

Para completar las "secciones de una clase", en tercer lugar de ubicación se suelen colocar los métodos que pueda incluir la clase. Estos métodos formarán el comportamiento (o acciones) posibles de realizar por cada objeto creado a partir de esta clase.

Los métodos deben incluir un modificador de acceso, el cual determinará si el método puede utilizarse solo dentro de la clase (`private`) o se permite utilizar por fuera de la clase (`public`). 

Cabe destacar que los métodos definidos como `public`, serán invocados por los objetos creados a partir de la clase, no por la clase en si misma. Mientras que los métodos definidos como `private`, podrán utilizarse dentro de la clase. Lo más habitual es que se invoquen desde algún constructor, o bien, desde otros métodos existentes en la clase.

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos
    public void cumplirAnios() {
        this.edad++;
    }

}
```
> **Nota:** En general el uso de caracteres especiales como la `ñ` puede traer inconvenientes. En su reemplazo, se puede usar la `n`, o bien, `ni`.

Dentro de una clase podemos definir tantos métodos como necesitemos. Una forma de ordenarlos es escribir los métodos públicos antes que los privados. Esto nos permite ver, dentro de la clase, primero los métodos que pueden utilizarse de manera pública, y si necesitamos ver alguno privado, simplemente bajamos hasta la sección de métodos privados.

* Getters y Setters

Continuando con el concepto de [encapsulamiento](./conceptos-basicos.html#Encapsulamiento) y considerando que los atributos de una clase (variables de caracter privado) a los cuales solo las podemos "utilizar" de la clase, debemos contar con una forma de interactuar (obtener el contenido actual o asignar un nuevo valor) con dichos atributos. Esta tarea la realizaremos mediante métodos públicos.

Para obtener el contenido de una variable asignado por ejemplo en su construcción, deberemos entonces generar un método que nos facilite el objetivo.

```java
    public String obtenerNombre () {
        return this.nombre;
    }
```

Esta tarea tiene un fin determinado. Definiendo un método no permitimos acceder directamente al contenido del atributo de clase. Además, tenemos el control absoluto dee cómo se realizará la obtención, esto quiere decir, que quien define el método, puede (o no) agregar líneas de código que permita la correcta obtención del dato, o bien, devolver un dato apropiado.

Entonces ¿De donde viene el concepto de `Getter`? Get en inglés significa "obtener" y es habitual encontrarse con un método como:

```java
    public String getNombre () {
        return this.nombre;
    }
```

Conceptualmente, este método y el anterior, representan la misma operación. La única diferencia es su nomenclatura.

En Java, se relega la responsabilidad de un método "Getter" a solo devolver el dato del atributo en cuestión. La nomenclatura de un método "Getter" suele ser `getNombre` donde "get" nos indica que vamos a obtener un dato y "Nombre" hace referencia al atributo del cual queremos obtener el dato o valor.

Cabe destacar que el tipo de dato que devuelve el método "Getter", debe ser el mismo que posee el atributo en su definición.

Un "Getter", al definir un tipo de dato de retorno (no void), debe poseer siempre la palabra reservada `return` acompañada del atributo necesario para satisfacer la operación. En este caso `this.nombre` (atributo de la clase).

En general, tenemos tantos "Getters" como atributos de clase. No obstante, si no queremos permitir que alguien pueda obtener el dato o valor de un atributo de clase, simplemente no escribimos el método "Getter" correspondiente.

Completamos el ejemplo:

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos

    // Getter del atributo de clase "nombre"
    public String getNombre () {
        return this.nombre;
    }

    // Getter del atributo de clase "edad"
    public int getEdad () {
        return this.edad;
    }

    // Getter del atributo de clase "duenio"
    public Persona getDuenio () {
        return this.duenio;
    }

    public void cumplirAnios() {
        this.edad++;
    }

}
```
Por su contraparte, podemos permitir (mediante un método) cambiar o asignar el contenido de un atributo de clase:

```java
    public void asignarNombre (String nombre) {
        this.nombre = nombre;
    }
```

El método anterior es un "Setter". La palabra Set deberá comprenderse como "asignar". Permitiendo entonces (en caso de escribir el método) cambiar el contenido (dato o valor) de un atributo de clase, para mantener el concepto de [encapsulamiento](./conceptos-basicos.html#Encapsulamiento).

La mayoría de las veces encontraremos que la nomenclatura de un "Setter", es similar a la del "Getter", donde definimos el nombre del método como `setNombre`. La palabra "set" nos indica que asignaremos algo al atributo de clase, mientras que la palabra "Nombre", nos indica a cuál atributo le asignamos algo.

```java
    public void setNombre (String nombre) {
        this.nombre = nombre;
    }
```

Debemos notar que los "Setters" no devuelven un dato o valor (void), ya que, su objetivo es asignar. Dicho esto encontraremos que los métodos tienen la palabra reservada `void` en el lugar donde ponemos el tipo de dato que devolverá en caso de ser un "Getter" y reciben un parámetro (String nombre en el ejemplo). Este parámetro deberá contener el dato o valor que deseamos asignar al atributo de clase.

Completamos el ejemplo:

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos
    
    // Getter del atributo de clase "nombre"
    public String getNombre () {
        return this.nombre;
    }

    // Getter del atributo de clase "edad"
    public int getEdad () {
        return this.edad;
    }

    // Getter del atributo de clase "duenio"
    public Persona getDuenio () {
        return this.duenio;
    }

    // Setter del atributo de clase "nombre"
    public void getNombre (String nombre) {
        this.nombre = nombre;
    }

    // Setter del atributo de clase "edad"
    public void getEdad (int edad) {
        this.edad = edad;
    }

    // Setter del atributo de clase "duenio"
    public void getDuenio (Persona duenio) {
        this.duenio = duenio;
    }

    public void cumplirAnios() {
        this.edad++;
    }

}
```

En el ejemplo antes definido, notamos que la única sentencia de código, en un "Setter", es una asignación del dato o valor que llega en el parámetro, hacia el atributo de clase. Esta suele ser la única sentencia incluida en un "Setter", aunque es posible agregar las líneas de código que necesitemos para garantizar que el dato asignado al atributo de clase sea "correcto" para nuestra clase.

Si bien la validación de información suele ser previa a la invocación de un "Setter", pueden encontrarse algunos ejemplos que agreguen líneas de código en un "Setter":

```java
    // Setter del atributo de clase "edad", con una ligera validación
    public void getEdad (int edad) {

        if(edad > 0) {
            this.edad = edad;
        } else {
            this.edad = 0;
        }
    }
```

En el ejemplo anterior, validamos que el dato o valor que llega en el parámetro sea mayor a cero. Si no fuera el caso (el dato es menor a cero), entonces asignamos al atributo de clase el literal cero.

Repitiendo, esta práctica no es la mas habitual, pero puede verse en algunos escenarios.

Hasta este punto, definimos una clase propia, con sus atributos (características), sus "Getters" y "Setters" para los atributos y un método llamado `cumplirAnios`.
Este método también realiza una operación sobre un atributo de la clase (incrementa en 1 el dato o valor del atributo edad). Este método no es considerado un "Setter", si no que, forma parte del conjunto de métodos que definen el "comportamiento" de la clase.

Agregamos otro método que agrega "comportamiento":

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos

    // Getter del atributo de clase "nombre"
    public String getNombre () {
        return this.nombre;
    }

    // Getter del atributo de clase "edad"
    public int getEdad () {
        return this.edad;
    }

    // Getter del atributo de clase "duenio"
    public Persona getDuenio () {
        return this.duenio;
    }

    // Setter del atributo de clase "nombre"
    public void getNombre (String nombre) {
        this.nombre = nombre;
    }

    // Setter del atributo de clase "edad"
    public void getEdad (int edad) {
        this.edad = edad;
    }

    // Setter del atributo de clase "duenio"
    public void getDuenio (Persona duenio) {
        this.duenio = duenio;
    }

    
    public void cumplirAnios() {
        this.edad++;
    }

    // Nuevo método agregado
    public String ladrar () {
        return "Guau!";
    }

}
```

En el ejemplo anterior notamos que el método "ladrar" no devuelve el dato o valor de un atributo de clase. En su lugar devuelve un literal String.

Esto nos indica que podemos agregar los métodos que obtengan o asignen datos según necesitemos, por fuera de los "Getters" y "Setters".

Si, por ejemplo, necesitamos mostrar todos los datos asignados a los atributos de la clase, podemos definir un método como el siguiente:

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }

    public Perro (String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // si no recibimos un parámetro para algún atributo (como en este caso), podemos asignar algo que nos sirva
    }

    public Perro (String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros, todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos

    // Getter del atributo de clase "nombre"
    public String getNombre () {
        return this.nombre;
    }

    // Getter del atributo de clase "edad"
    public int getEdad () {
        return this.edad;
    }

    // Getter del atributo de clase "duenio"
    public Persona getDuenio () {
        return this.duenio;
    }

    // Setter del atributo de clase "nombre"
    public void getNombre (String nombre) {
        this.nombre = nombre;
    }

    // Setter del atributo de clase "edad"
    public void getEdad (int edad) {
        this.edad = edad;
    }

    // Setter del atributo de clase "duenio"
    public void getDuenio (Persona duenio) {
        this.duenio = duenio;
    }

    
    public void cumplirAnios() {
        this.edad++;
    }

    public String ladrar () {
        return "Guau!";
    }

    // Nuevo método agregado
    public String obtenerDatosDelPerro () {
        String datosDelPerro = "Nombre: " + this.nombre + ", Edad: " + this.edad;
        return datosDelPerro;
    }

}
```

Notamos entonces que podemos utilizar los atributos de la clase para forma un texto que nos indica el nombre y la edad del perro.
En el método `obtenerDatosDelPerro`, definimos una variable local al método (datosDelPerro) la cual sólo puede ser utilizada dentro del método (dentro de sus llaves) y a la cual se asignan literales String concatenados con los datos correspondientes, para luego devolverlos con `return`.

Una forma abreviada puede ser la siguiente:

```java
    // Nuevo método agregado de manera abreviada
    public String obtenerDatosDelPerro () {
        return datosDelPerro = "Nombre: " + this.nombre + ", Edad: " + this.edad;
    }
```

Donde simplemente devolvemos la concateniación de los lietarles String y los atributos de clase, evitando definir una variable local al método.

## Objetos

Entonces, ¿Cuál es el objetivo de definir una clase personalizada?

La definición de una clase personalizada nos permite generar objetos los cuales adoptarán los atributos y métodos que definimos en la clase.

Un objeto no es mas que una variable del tipo de la clase que definimos.

```java
    // Definición de una variable la cual será un objeto de tipo Perro.
    Perro miPerro;
```

En este punto tenemos una variable de tipo "Perro", pero que aún no tiene nada asignado. Estas variables, cuando las definimos, no las podremos asignar con un dato o valor primitivo (o de tipo String), porque su tipo es "Perro".

Para crear un objeto o "instanciar" (considerado como sinónimo), debemos entonces utilizar la palabra reservada `new` seguida del nombre de la clase `Perro` (en este ejemplo), y luego utilizar paréntesis de apertura y cierre.

```java
    // Creación de un objeto o instancia de la clase Perro.
    Perro miPerro = new Perro ();
```

En el ejemplo anterior notamos que luego del caracter `=`, el cual utilizamos para asignar, tenemos algo diferente a lo antes visto. La asignación funciona de la misma manera, pero en lugar de asignar un dato de tipo primitiro (o String), asignamos el objeto o instancia de tipo Perro.

La palabra reservada `new` es la encargada de reservar un espacio en la memoria del sistema operativo (propia para el programa cuando se ejecute) y colocar el objeto o instancia que estamos creando. Dicho espacio en memoria podrá almacenar, por ejemplo, todos los atributos que la clase defina.

Podemos entonces instanciar más de un objeto:

```java
    // Creación de un objeto o instancia de la clase Perro.
    Perro miPerro = new Perro ();

    // Creación de un objeto o instancia que representa a otro perro
    Perro miOtroPerro = new Perro ();
```

De esta forma podemos crear otro objeto perro con las mismas características y comportamiento que define la clase Perro.

¿Dónde está lo divertido?

Es importante notar que en la creación de los objetos, entre los paréntesis no hay datos `new Perro ()`. Esta línea de código hace uso del constructor, definido en la clase "Perro", que no recibe parámetros.

```java
public class Perro {
    
    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructor utilizado en la creación de los objetos "miPerro" y "miOtroPerro" en el ejemplo anterior
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        nombre = "";
        edad = 0;
        duenio = null;
    }
}
```

Siendo que, cuando el constructor vacío no recibe parámetros, los valores iniciales de los atributos de cada objeto o instancia, serán los que se asignaron en el constructor vacío (nombre es un literal String sin contenido, la edad es un literal cero y el duenio null). Estos valores representan al dato o valor que poseen los atributos de clase.

Podemos crear tantos objetos o instancias de la clase Perro que necesitemos.

¿Dónde debemos crear objetos o instancias? Siempre dentro de algún método.

¿Cómo obtenemos el nombre de un perro? Debemos invocar al método "Getter" que definimos para tal fin.

Para ello, debemos escibir el nombre de la variable (miPerro), seguido de un `.` (punto) y luego el nombre del método que deseamos invocar (o llamar).

```java
    // Creación de un objeto o instancia de la clase Perro.
    Perro miPerro = new Perro ();
    String nombreDeMiPerro = miPerro.getNombre(); // invocación al método getNombre() el cual devolverá el dato actual (en el atributo nombre) del objeto "miPerro"

    // Creación de un objeto o instancia que representa a otro perro
    Perro miOtroPerro = new Perro ();
    String nombreDeMiOtroPerro = miPerro.getNombre(); // invocación al método getNombre() el cual devolverá el dato actual (en el atributo nombre) del objeto "miOtroPerro"
```

En el ejemplo recien mostrado, se asigna a la variable `nombreDeMiPerro` de tipo String, el dato que posee el objeto "miPerro", en el atributo "nombre". Se asignará entonces el dato o valor `""` (String con contenido vacío).

Por su parte, en la variable `nombreDeMiOtroPerro` de tipo String, se asigna el dato que posee el objeto "miOtroPerro", en el atributo "nombre". Se asignará entonces el dato o valor `""` (String con contenido vacío).

¿Cómo cambiamos el nombre de un perro? Siendo que definimos un método "Setter" que permite asignar el atributo nombre, podemos hacer uso del "Setter".

Para ello, debemos escibir el nombre de la variable (miPerro), seguido de un `.` (punto), luego el nombre del método que deseamos invocar (o llamar), debiendo indicar entre los paréntesis del método, el dato o valor que deseamos asignar.

```java
    // Creación de un objeto o instancia de la clase Perro.
    Perro miPerro = new Perro ();
    String nombreDeMiPerro = miPerro.getNombre(); // El contenido de nombreDeMiPerro es "" (vacio)
    miPerro.setNombre("Firulais"); // Asignación de un nombre para mi objeto "miPerro"

    // Creación de un objeto o instancia que representa a otro perro
    Perro miOtroPerro = new Perro ();
    String nombreDeMiOtroPerro = miPerro.getNombre(); // El contenido de nombreDeMiOtroPerro es "" (vacio)
    miOtroPerro.setNombre("Cartucho"); // Asignación de un nombre para mi objeto "miOtroPerro"
```

Estas asignaciones colocarán los datos "Firulais" y "Cartucho" en los atributos "nombre" de cada objeto.

Si ahora los volvemos obtener los nombres dew cada objeto utilizando el "Getter" correspondiente, y asignamos a las variables definidas, cada objeto en su atributo "nombre" contendrá "Firulais" y "Cartucho" respectivamente.

```java
    // Creación de un objeto o instancia de la clase Perro.
    Perro miPerro = new Perro ();
    String nombreDeMiPerro = miPerro.getNombre(); // El contenido de nombreDeMiPerro es "" (vacio)
    miPerro.setNombre("Firulais"); // Asignación de un nombre para mi objeto "miPerro"
    nombreDeMiPerro = miPerro.getNombre(); // El contenido de nombreDeMiPerro es "Firulais"

    // Creación de un objeto o instancia que representa a otro perro
    Perro miOtroPerro = new Perro ();
    String nombreDeMiOtroPerro = miPerro.getNombre(); // El contenido de nombreDeMiOtroPerro es "" (vacio)
    miOtroPerro.setNombre("Cartucho"); // Asignación de un nombre para mi objeto "miOtroPerro"
    nombreDeMiOtroPerro = miOtroPerro.getNombre(); // El contenido de nombreDeMiOtroPerro es "Cartucho"
```

> **Importante:** Esto nos deja ver que cada objeto o instancia posee las mismas características o comportamiento definidos en la clase "Perro", pero cada objeto o instancia, almacena datos distintos.

## Garbage collector

Como vimos en [Conceptos básicos](./conceptos-basicos.html#Variables), para la creación de una variable de tipo de dato primitivo, se reserva una porción de memoria donde se almacenará el dato o valor asignado a la variable. En el caso de objetos, esto funciona de manera similar, pero con un sector de memoria agregado, conocido como `Heap` (o montón).

Cuando creamos un objeto entonces, se reserva una porción de memoria en el `Stack` (o pila de memoria) para almacenar el dato o valor de cada atributo del objeto. En la clase "Perro" serán: nombre, edad y duenio. Así como también la variable de referencia "miPerro" (nombre de la variable que contiene al objeto).

Es importante recordar que en la pila de memoria `Stack` se almacenan tipos de dato primitivos

En el `Heap` entonces, se almacenará el contenido de los objetos, pero de una manera particular. El `Heap` trabaja con un gran String (conocido como String pool) que posee los datos del objeto. Entonces existe una relación o referencia entre la variable del objeto "miPerro" almacenada en el "Stack" y los datos del objetos, almacenados en el "Heap".

Como vimos antes, la pila de memoria o Stack se libera cuando un método termina de utilizar las variables o bien, se finaliza la ejecución del programa. Esto genera que la pila de memoria se libere, rompiendo las referencias, pero la memoria "Heap", no libera la memoria ocupada por los datos del objeto de manera automática.

La función del "Garbage collector" es liberar los objetos alojados en el "Heap" que no tengan una referencia en el "Stack".

Para más información pueden visitar: [Java Stack y Heap](https://www.baeldung.com/java-stack-heap).

## Métodos y atributos estáticos

Vimos que en una clase podemos definir atributos y métodos que serán parte de los objetos creados o instanciados a partir de dicha clase.

Y que haríamos si necesitamos que un atributo o método sea común a todas los objetos creados, es decir, le pertenezca estrictamente a la clase.

Java, así como otros lenguajes de programación, provee de una palabra reservada para tal fin: `static`. Esta palabra reservada puede ser utilizada con atributos, constantes o métodos.

Siendo que la palabra reservada `this` es utilizada para referenciar a un atributo o método no estático de la clase, no debemos utilizarla para referirnos a un atributo o método estático. Si lo hacemos obtendremos una advertencia (warning) que nos indicará que, debemos utilizar dicho elemento de manera estática. Esa forma es utilizar el atributo o clase directamente sin anteponer `this.`.

```java
public class Perro {
    
    // Definición de una variable estática, perteneciente a la clase
    private static int identificador = 1; // Para este ejemplo, le asignamos un literal entero para inicializar la variable estática

    // Atributos y constantes
    private int id;
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructor utilizado en la creación de los objetos "miPerro" y "miOtroPerro" en el ejemplo anterior
    public Perro () {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        this.id = obtenerSiguienteIdentificador(); // Asignamos el siguiente identificador
        this.nombre = "";
        this.edad = 0;
        this.duenio = null;
    }

    // Método estático perteneciente solo a la clase (no a los objetos creados)
    private static int obtenerSiguienteIdentificador () {
        return identificador++;
    }
}
```

En el ejemplo anterior, cada vez que se cree un objeto utilizando el constructor vacío, se asignará un identificador. Dicho identificador será un número correlativo (se incrementa de 1 en 1). Entonces el primer objeto creado tendrá id 1, el segundo id 2, el tercero id 3 y así sucesivamente. 

## enum

Un enumerado o "enum", es una "clase especial" que limita básicamente, la creación de objetos. Solo se permite crear uno (en cierto modo) y será explícitamente la implementación del enum. Esto quiere decir, que el contenido del enum será "una única instancia".

Para definir un "enum", debemos reemplazar la palabra `class` por `enum`, el modificador de acceso deberá se `public`, el nombre del enum deberá comenzar con la primera letra en mayúscula, con las siguientes en minúscula. Si existe otra palabra en el nombre del enum, debe comenzar con mayúscula: `MiEnum`.

```java
public enum Colores {

}
```

Los enums suelen declarar un contenido considerados "opciones", los cuales deben escribirse como las constantes, en letra mayúscula y separados por guiones bajos si existiera mas de una palabra.

Internamente, un enum asigna un número de orden para cada opción, comenzando por el cero. Este número de orden, nos permite acceder a la opción (por ejemplo).

```java
public enum Colores {
    ROJO, AZUL, AMARILLO, BLANCO, NEGRO, AZUL_OSCURO
    //0    1      2         3       4       5
}
```

Dichas opciones o valores del enum, se usan de manera estática, es decir, cuando necesitemos usar alguna de las opciones, debemos escribir el nombre del enum, seguido de un `.` (punto) y luego la opción deseada.

```java
    // Este código debe estar en un método por ejemplo
    Colores.AZUL;
```

Las opciones de un enum (ROJO, AZUL, etc) suelen contener algunos métodos de la clase String, como el método `equals()`.

Es posible definirle constructores a un enum, con la salvedad de que deben ser privados (y así no permitir que se creen objetos). No obstante, si intentamos asignar un modificador de acceso `public` a un constructor, obtendremos un error.

```java
public enum Colores {
    ROJO, AZUL, AMARILLO, BLANCO, NEGRO, AZUL_OSCURO

    // Constructor del enum
    Colores () {

    }
}
```

Al no definir un modificador de acceso privado, el enum lo asume automáticamente (private es opcional).

¿Por qué podriamos necesitar un constructor?

Un enum permite definir atributos (como en una clase) y utilizarlos dentro del enum. Un atributo muy habitual es de tipo String y se suele utilizar para darle alguna descripción a una opción del enum, ya que, si mostramos por pantalla una opción del enum, se muestra el nombre de la opción (Ejemplo: AZUL_OSCURO). Esto puede no ser muy estético cuando mostramos una opción.

Podemos entonces agregar un parámetro de tipo String que permita dar el valor de descripción que deseamos a cada opción del enum. Sin olvidar que este parámetro debe asignarse a algún atributo del enum.

```java
public enum Colores {
    // Opcines del enum que asignan en su construccción una descripción amigable.
    ROJO("Rojo"), // orden 0
    AZUL("Azul"), // orden 1
    AMARILLO("Amarillo"), // orden 2
    BLANCO("Blanco"), // orden 3
    NEGRO("Negro"), // orden 4
    AZUL_OSCURO("Azul oscuro"); // orden 5. Se agrega ; (punto y coma) al final de la última opción del enum con constructor

    // Atributo del enum
    private String descripcion;

    // Constructor del enum que recibe un parámetro y lo asigna al atributo
    Colores (String descripcion) {
        this.descripcion = descripcion;
    }
}
```

Es importante notar que al lado de cada opción del enum se proporciona el dato literal que formará parte de la opción del enum. Siendo ese lugar, el único donde se podrá usar el constructor, ya que, es privado. También es necesario finalizar las opciones con un `;` (punto y coma), caso contrario obtendremos un error.

Si bien definimos un atributo con una descripción amigable, el enum no provee estrictamente de una forma de obtener dicha descripción. Podemos entonces crear un método para tal fin (un getter).

```java
public enum Colores {
    // Opcines del enum que asignan en su construccción una descripción amigable.
    ROJO("Rojo"), 
    AZUL("Azul"), 
    AMARILLO("Amarillo"), 
    BLANCO("Blanco"), 
    NEGRO("Negro"), 
    AZUL_OSCURO("Azul oscuro"); // Se agrega ; (punto y coma) al final de la última opción del enum con constructor

    // Atributo del enum
    private String descripcion;

    // Constructor del enum que recibe un parámetro y lo asigna al atributo
    Colores (String descripcion) {
        this.descripcion = descripcion;
    }

    public String getDescripcion () {
        return this.descripcion;
    }
}
```

Si necesitamos mostrar por pantalla la descripcion de una opción del enum podemos usar el Getter.

Antes de mostrar como se obtiene la descripción, es importante conocer los métodos que provee el enum por defecto (en general usamos `values()` y `valueOf()`).

```java
    // Métodos de un enum
    Colores.values(); // Obtiene las opciones de un enum en un array (ver arrays)

    // El enum puede utilizarse como tipo de dato para definiar una variable del tipo del enum
    Colores colorAzul = Colores.valueOf("AZUL"); // El método valueOf() permite obtener una opción del enum (de tipo enum), utilizando el nombre de la opción
    colorAzul = Colores.values()[1]; // Es posible obtener una opción del enum por su número de orden (ver arrays).

    // Obtención de la descrpción de una opción del enum Colores
    String descripcionColorAzulOscuro = Colores.valueOf("AZUL_OSCURO").getDescripcion(); // A la variable "descripcionColorAzulOscuro" se le asigna "Azul oscuro"

    int ordinalAzul = Colores.valueOf("AZUL").ordinal(); // Obtiene el número de orden de la opción AZUL del enum
    String nombreAzul = Colores.valueOf("AZUL").name(); // Obtiene el nombre de la opción AZUL del enum como String
```

> **Nota:** Escribiendo un punto luego del valor de un enum `Colores.valueOf("AZUL").` podemos ver todos los métodos posibles de utilizar.

El atributo de clase que en el ejemplo es de tipo String, no necesariamente debe ser String, puede ser int, double, float, etc, respetando el tipo de dato en el constructor y el valor que se pasa al constructor en el momento de crear la opción del enum. Es recomendable que sea de un tipo de dato primitivo o String.

Ejemplo con un tipo de dato primitivo int:

```java
public enum Numeros {
    UNO(1), 
    DOS(2), 
    TRES(3); 

    // Atributo del enum
    private int valor;

    // Constructor del enum que recibe un parámetro y lo asigna al atributo
    Numeros (int valor) {
        this.valor = valor;
    }

    public int getValor () {
        return this.valor;
    }
}
```

[Volver](../)