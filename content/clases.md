---
layout: default
---

[Volver](../)

# Clases

Las clases son el principal elemento para representar un elemento de la realidad en código ([abstracción](https://es.wikipedia.org/wiki/Abstracci%C3%B3n_(inform%C3%A1tica)) de POO). Definen las características (atributos) y el comportamiento (métodos) que poseerán todos los objetos creados a partir de la clase que definimos.

## Definición de clase personalizada

Para definir una clase debemos indicar un modificador de acceso (el más común es `public`), seguido de la palabra reservada `class` y un nombre de clase como `Perro`.

La nomenclatura de clases, por convención, es [PascalCase](https://es.wikipedia.org/wiki/Camel_case): la primera letra de cada palabra se escribe en mayúscula y no se usan separadores. Ejemplo: `AutoVolador`.

Las clases incluyen sus propias llaves de apertura y cierre, que son obligatorias.

Las clases no poseen paréntesis para recibir parámetros (como los métodos); esa tarea queda a cargo de los [constructores](#constructor).

```java
public class Perro {
    // Contenido de la clase
}
```

> **Importante:** una clase `public` debe estar en un archivo con exactamente su mismo nombre. La clase `Perro` va en el archivo `Perro.java`.

Las clases suelen organizarse en tres secciones, en este orden:

1. **Atributos y constantes**: las características de la clase.
2. **Constructores**: cómo se inicializan los objetos.
3. **Métodos**: el comportamiento de la clase.

## Modificadores de acceso

Un modificador de acceso establece si se permite el acceso (y con qué nivel) a una clase o a un elemento de una clase, como pueden ser atributos o métodos.

Java provee cuatro modificadores de acceso:

* **public**: el elemento es de acceso público. Aplicado sobre la definición de una clase, permite que la misma sea utilizada en todo el proyecto.
* **private**: generalmente utilizado sobre los atributos de una clase (también sobre algunos métodos), no permite el acceso a esos elementos desde afuera de la clase. Es el nivel de acceso más restrictivo.
* **protected**: más utilizado al implementar [herencia](#herencia), permite que los atributos o métodos de una superclase sean accedidos por las clases que hereden de ella.
* **default** (o "de paquete"): cuando no escribimos ninguno de los anteriores, se aplica este nivel de acceso. Permite el acceso desde todas las clases del mismo paquete (package). No existe una palabra reservada `default` para esto: simplemente no se escribe nada.

## Atributos

Al principio de la clase se escriben los atributos (variables) y constantes que pueda tener. Los atributos, en Java, deben tener el modificador de acceso `private` para cumplir con el concepto de [encapsulamiento](./introduccion-a-java.html#encapsulamiento). Los atributos estarán presentes en todos los objetos que se creen a partir de la clase.

Las constantes definidas en la clase pueden ser `private` o `public`, según sea necesario.

Los atributos de una clase raramente se inicializan al momento de declararlos: esa tarea se deja para cada constructor.

```java
public class Perro {

    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

}
```

Notar que el atributo `duenio` no es un tipo de dato primitivo ni un `String`: es de tipo `Persona`, otra clase que definimos nosotros. Una clase puede tener como atributo un objeto de otra clase.

```java
public class Persona {

    private String nombre;

    public Persona(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() {
        return this.nombre;
    }
}
```

> **Nota:** en general, el uso de caracteres especiales como la `ñ` puede traer inconvenientes. En su reemplazo se puede usar `n`, o bien `ni` (como en `duenio`).

## Constructor

Es una especie de método (aunque tiene su propia forma de definirse) que nos permite inicializar los objetos que se creen a partir de la clase. Podemos tener más de un constructor.

Un constructor posee un modificador de acceso (generalmente `public`), lleva **el mismo nombre que la clase** y no declara ningún tipo de dato de retorno (ni siquiera `void`). Se completa con dos llaves que delimitan las sentencias que se ejecutarán al utilizarlo.

```java
// Considerando que la clase se llama Perro, definimos un constructor sin parámetros

public Perro() {
    // Líneas de código del constructor
}
```

El constructor más común es el que no recibe parámetros. Si no escribimos **ningún** constructor, Java nos provee uno vacío de manera implícita. Pero en cuanto definimos al menos un constructor con parámetros, ese constructor implícito deja de existir: si además lo necesitamos, tenemos que escribirlo nosotros.

Al igual que con los métodos, es posible tener más de un constructor (sobrecarga de constructores). Como todos llevan el mismo nombre, deben diferenciarse en la cantidad de parámetros o en los tipos de dato de esos parámetros y su orden (los nombres de los parámetros no cuentan).

```java
// Constructor que recibe un parámetro
public Perro(String nombre) {
    // Líneas de código del constructor
}

// Constructor que recibe dos parámetros
public Perro(String nombre, int edad) {
    // Líneas de código del constructor
}

// Constructor que además recibe un parámetro de una clase personalizada
public Perro(String nombre, int edad, Persona duenio) {
    // Líneas de código del constructor
}
```

Es importante saber que, en la creación de un objeto, se utiliza **un solo** constructor.

### La palabra reservada this

Lo habitual es que los constructores reciban parámetros con el mismo nombre que los atributos de la clase. En ese caso, una asignación como la siguiente NO tiene efecto: el nombre `nombre` se refiere al parámetro, así que la línea le asigna el parámetro a sí mismo y el atributo queda sin tocar.

```java
public class Perro {

    private String nombre;
    private int edad;
    private Persona duenio;

    public Perro(String nombre, int edad, Persona duenio) {
        // Estas asignaciones no tienen efecto sobre los atributos
        nombre = nombre;
        edad = edad;
        duenio = duenio;
    }

}
```

Para resolver este escenario, Java nos provee la palabra reservada `this`, que dentro de una clase hace referencia al objeto actual, con la salvedad de que *no puede usarse para atributos ni métodos estáticos*.

La palabra reservada `this` debe ir seguida de un punto y luego el atributo o método al que nos queremos referir: `this.nombre` es el atributo, mientras que `nombre` a secas es el parámetro.

```java
public class Perro {

    private String nombre;
    private int edad;
    private Persona duenio;

    public Perro(String nombre, int edad, Persona duenio) {
        // Estas asignaciones sí modifican los atributos, por incluir la palabra reservada this
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

}
```

> **Recomendación:** conviene usar siempre `this.` para referirse a un elemento propio de la clase, aunque no haya ambigüedad. Deja explícito que estamos trabajando con un atributo y no con una variable local.

Con esto, los tres constructores de la clase quedan así:

```java
public class Perro {

    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro() {
        // Como no recibe parámetros, inicializamos los atributos con valores que nos sirvan
        this.nombre = "";
        this.edad = 0;
        this.duenio = null;
    }

    public Perro(String nombre, int edad) {
        // Si recibimos parámetros, lo habitual es utilizarlos para inicializar los atributos
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null; // Si no recibimos un parámetro para algún atributo, podemos asignarle algo que nos sirva
    }

    public Perro(String nombre, int edad, Persona duenio) {
        // Este constructor recibe como parámetros todos los atributos de la clase Perro
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

}
```

## Métodos

En tercer lugar se ubican los métodos que pueda incluir la clase. Estos métodos formarán el comportamiento (o las acciones) que podrá realizar cada objeto creado a partir de esta clase.

Los métodos deben incluir un modificador de acceso, que determinará si el método puede utilizarse solo dentro de la clase (`private`) o también desde afuera (`public`).

Los métodos definidos como `public` serán invocados por los objetos creados a partir de la clase, no por la clase en sí misma. Los métodos `private` solo pueden usarse dentro de la clase: lo más habitual es que se invoquen desde algún constructor o desde otros métodos de la misma clase.

```java
    // Método que incrementa en 1 la edad del perro
    public void cumplirAnios() {
        this.edad++;
    }
```

Dentro de una clase podemos definir tantos métodos como necesitemos. Una forma de ordenarlos es escribir los métodos públicos antes que los privados, para ver primero lo que la clase ofrece hacia afuera.

### Getters y Setters

Continuando con el concepto de [encapsulamiento](./introduccion-a-java.html#encapsulamiento): los atributos de una clase son privados, con lo cual solo se pueden usar desde adentro de la clase. Necesitamos entonces alguna forma de interactuar con ellos desde afuera (obtener su contenido actual o asignarles un nuevo valor). Esa tarea la realizamos mediante métodos públicos.

Para obtener el contenido de un atributo debemos generar un método que nos devuelva ese dato:

```java
    public String obtenerNombre() {
        return this.nombre;
    }
```

Definiendo un método no permitimos acceder directamente al atributo. Además, tenemos control absoluto sobre cómo se realiza la obtención: quien define el método puede agregar las líneas de código que hagan falta para devolver un dato apropiado.

Entonces, ¿de dónde viene el concepto de `Getter`? *Get* en inglés significa "obtener", y es habitual encontrarse con un método como:

```java
    public String getNombre() {
        return this.nombre;
    }
```

Conceptualmente este método y el anterior representan la misma operación; la única diferencia es su nomenclatura. La nomenclatura de un "Getter" es `getNombre`, donde "get" indica que vamos a obtener un dato y "Nombre" hace referencia al atributo del cual lo obtenemos.

Puntos a tener en cuenta sobre un "Getter":

* El tipo de dato que devuelve debe ser el mismo que el del atributo.
* Al declarar un tipo de dato de retorno (no `void`), siempre debe incluir la palabra reservada `return`.
* En Java, la responsabilidad de un "Getter" es únicamente devolver el dato del atributo en cuestión.
* En general tenemos tantos "Getters" como atributos. Si no queremos permitir que se obtenga el valor de un atributo, simplemente no escribimos su "Getter".

Por su contraparte, podemos permitir que se cambie el contenido de un atributo:

```java
    public void asignarNombre(String nombre) {
        this.nombre = nombre;
    }
```

El método anterior es un "Setter". La palabra *set* debe comprenderse como "asignar". La nomenclatura habitual es análoga a la del "Getter": definimos el nombre del método como `setNombre`, donde "set" indica que asignaremos algo y "Nombre" indica a cuál atributo.

```java
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
```

Debemos notar que los "Setters" no devuelven ningún dato (`void`), ya que su objetivo es asignar, y que reciben un parámetro (`String nombre` en el ejemplo) con el dato que deseamos asignar al atributo.

> **Importante:** un "Getter" empieza con `get` y un "Setter" con `set`. Usar `get` para un método que asigna, o al revés, compila igual pero vuelve el código imposible de leer.

La única sentencia de un "Setter" suele ser la asignación del parámetro al atributo, aunque es posible agregar las líneas que necesitemos para garantizar que el dato asignado sea válido para nuestra clase.

Si bien la validación de información suele ser previa a la invocación de un "Setter", pueden encontrarse ejemplos como este:

```java
    // Setter del atributo "edad", con una ligera validación
    public void setEdad(int edad) {

        if (edad > 0) {
            this.edad = edad;
        } else {
            this.edad = 0;
        }
    }
```

En el ejemplo anterior validamos que el dato que llega en el parámetro sea mayor a cero. Si no lo fuera, asignamos al atributo el literal cero. Repitiendo: esta práctica no es la más habitual, pero puede verse en algunos escenarios.

### Otros métodos

No todo método es un "Getter" o un "Setter". El método `cumplirAnios` que vimos antes también opera sobre un atributo (incrementa la edad en 1), pero no es un "Setter": forma parte del conjunto de métodos que definen el comportamiento de la clase.

Podemos agregar los métodos que necesitemos, devuelvan o no el valor de un atributo:

```java
    public String ladrar() {
        return "Guau!"; // No devuelve un atributo, sino un literal String
    }
```

Si, por ejemplo, necesitamos mostrar todos los datos del perro, podemos definir un método como el siguiente:

```java
    public String obtenerDatosDelPerro() {
        String datosDelPerro = "Nombre: " + this.nombre + ", Edad: " + this.edad;
        return datosDelPerro;
    }
```

Acá declaramos una variable local al método (`datosDelPerro`), que solo puede utilizarse dentro de sus llaves, y le asignamos literales String concatenados con los atributos, para luego devolverla con `return`.

Una forma abreviada, que evita declarar la variable local, es devolver la concatenación directamente:

```java
    public String obtenerDatosDelPerro() {
        return "Nombre: " + this.nombre + ", Edad: " + this.edad;
    }
```

### El método toString

"Devolver los datos del objeto como texto" es una necesidad tan común que Java ya tiene un nombre estándar para ese método: `toString()`. Todas las clases lo tienen, aunque no lo escribamos, porque toda clase [hereda](#herencia) de `Object`.

El problema es que la versión que viene por defecto no es útil. Si mostramos un objeto por pantalla sin haber escrito nuestro `toString()`, vemos algo así:

```java
    Perro miPerro = new Perro("Firulais", 3);
    System.out.println(miPerro); // Muestra algo como: Perro@1b6d3586
```

Ese texto es el nombre de la clase y un número que identifica al objeto en memoria: no nos dice nada sobre el perro.

La solución es escribir nuestro propio `toString()`. Es el mismo método que veníamos escribiendo como `obtenerDatosDelPerro`, solo que con el nombre que Java espera:

```java
    @Override
    public String toString() {
        return "Perro [nombre=" + this.nombre + ", edad=" + this.edad + "]";
    }
```

Con eso, la misma línea de antes ahora muestra los datos del perro:

```java
    Perro miPerro = new Perro("Firulais", 3);
    System.out.println(miPerro); // Muestra: Perro [nombre=Firulais, edad=3]
```

> **Nota:** el formato `Perro [nombre=..., edad=...]` es el que generan los IDE cuando les pedimos que escriban el `toString()` por nosotros (en Eclipse, con *Source > Generate toString()*). Conviene respetarlo: cualquiera que lea el código lo reconoce de inmediato.

Puntos a tener en cuenta:

* El método debe llamarse exactamente `toString`, ser `public`, no recibir parámetros y devolver un `String`. Si nos apartamos de esa firma, deja de ser el método que Java usa.
* `System.out.println(miPerro)` y `"" + miPerro` invocan a `toString()` automáticamente. No hace falta escribir `miPerro.toString()`, aunque también es válido.
* La anotación `@Override` no es obligatoria, pero conviene incluirla: le avisa al compilador que estamos reescribiendo un método que ya existe, y si nos equivocamos en el nombre o en los parámetros, nos marca el error. Se explica en [herencia](#herencia).

De acá en adelante usamos `toString()` en lugar de `obtenerDatosDelPerro`.

### La clase completa

Juntando todo lo visto hasta acá, la clase `Perro` queda así:

```java
public class Perro {

    // Atributos y constantes
    private String nombre;
    private int edad;
    private Persona duenio;

    // Constructores
    public Perro() {
        this.nombre = "";
        this.edad = 0;
        this.duenio = null;
    }

    public Perro(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = null;
    }

    public Perro(String nombre, int edad, Persona duenio) {
        this.nombre = nombre;
        this.edad = edad;
        this.duenio = duenio;
    }

    // Métodos

    // Getters
    public String getNombre() {
        return this.nombre;
    }

    public int getEdad() {
        return this.edad;
    }

    public Persona getDuenio() {
        return this.duenio;
    }

    // Setters
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }

    public void setDuenio(Persona duenio) {
        this.duenio = duenio;
    }

    // Comportamiento
    public void cumplirAnios() {
        this.edad++;
    }

    public String ladrar() {
        return "Guau!";
    }

    @Override
    public String toString() {
        return "Perro [nombre=" + this.nombre + ", edad=" + this.edad + "]";
    }

}
```

## Objetos

Entonces, ¿cuál es el objetivo de definir una clase personalizada?

Definir una clase nos permite generar objetos, que adoptarán los atributos y métodos declarados en ella. Un objeto no es más que una variable del tipo de la clase que definimos.

```java
    // Declaración de una variable que podrá contener un objeto de tipo Perro
    Perro miPerro;
```

En este punto tenemos una variable de tipo `Perro`, pero que todavía no tiene nada asignado. A estas variables no podemos asignarles un dato primitivo (ni un `String`), porque su tipo es `Perro`.

Para crear un objeto, o "instanciar" (considerado sinónimo), debemos utilizar la palabra reservada `new` seguida del nombre de la clase y de los paréntesis del constructor que queramos usar.

```java
    // Creación de un objeto o instancia de la clase Perro
    Perro miPerro = new Perro();
```

La asignación funciona igual que siempre, solo que en lugar de asignar un dato primitivo asignamos el objeto recién creado.

La palabra reservada `new` es la encargada de reservar un espacio en memoria para el objeto. Dicho espacio almacenará, por ejemplo, todos los atributos que la clase defina.

Podemos entonces instanciar más de un objeto:

```java
    Perro miPerro = new Perro();
    Perro miOtroPerro = new Perro();
```

De esta forma creamos dos perros con las mismas características y comportamiento definidos por la clase `Perro`, pero independientes entre sí.

Es importante notar que en `new Perro()` no hay datos entre los paréntesis: esta línea usa el constructor que no recibe parámetros. Los valores iniciales de los atributos de cada objeto serán entonces los que ese constructor asigna (`nombre` un String vacío, `edad` cero y `duenio` null).

Si usamos otro constructor, los objetos nacen con los datos que le pasemos:

```java
    Perro miPerro = new Perro("Firulais", 3);
    Perro miOtroPerro = new Perro("Cartucho", 5, new Persona("Ana"));
```

Podemos crear tantos objetos o instancias de la clase `Perro` como necesitemos.

¿Dónde debemos crear objetos? Siempre dentro de algún método.

### Usar los métodos de un objeto

¿Cómo obtenemos el nombre de un perro? Invocando al método "Getter" que definimos para tal fin. Para ello escribimos el nombre de la variable, seguido de un `.` (punto) y luego el nombre del método.

```java
    Perro miPerro = new Perro();
    String nombreDeMiPerro = miPerro.getNombre(); // Devuelve el dato actual del atributo nombre del objeto miPerro -> "" (vacío)

    Perro miOtroPerro = new Perro();
    String nombreDeMiOtroPerro = miOtroPerro.getNombre(); // Devuelve el dato actual del atributo nombre del objeto miOtroPerro -> "" (vacío)
```

¿Cómo cambiamos el nombre de un perro? Usando el "Setter", indicando entre los paréntesis el dato que deseamos asignar.

```java
    Perro miPerro = new Perro();
    miPerro.setNombre("Firulais"); // Asignación de un nombre para el objeto miPerro

    Perro miOtroPerro = new Perro();
    miOtroPerro.setNombre("Cartucho"); // Asignación de un nombre para el objeto miOtroPerro
```

Si ahora volvemos a obtener los nombres de cada objeto con su "Getter", cada uno devolverá el dato que le asignamos:

```java
    Perro miPerro = new Perro();
    String nombreDeMiPerro = miPerro.getNombre(); // El contenido es "" (vacío)
    miPerro.setNombre("Firulais");
    nombreDeMiPerro = miPerro.getNombre(); // El contenido ahora es "Firulais"

    Perro miOtroPerro = new Perro();
    String nombreDeMiOtroPerro = miOtroPerro.getNombre(); // El contenido es "" (vacío)
    miOtroPerro.setNombre("Cartucho");
    nombreDeMiOtroPerro = miOtroPerro.getNombre(); // El contenido ahora es "Cartucho"
```

> **Importante:** cada objeto o instancia posee las mismas características y el mismo comportamiento definidos en la clase `Perro`, pero **cada uno almacena sus propios datos**.

### Pasar objetos a un método

En [métodos](./metodos.html#qué-recibe-realmente-un-método) vimos que un método recibe una copia del valor, y que modificar un parámetro de tipo primitivo no afecta a la variable original.

Con los objetos la regla es la misma —se copia el valor de la variable— pero hay que tener presente qué contiene esa variable: **no el objeto, sino la referencia al objeto**. La copia apunta al mismo objeto, con lo cual el método sí puede modificarlo.

```java
public void cambiarNombre(Perro perro) {
    perro.setNombre("Cartucho"); // Modifica el objeto al que apunta la referencia
}
```

```java
Perro miPerro = new Perro("Firulais", 3);
cambiarNombre(miPerro);
System.out.println(miPerro.getNombre()); // Muestra "Cartucho": el objeto cambió
```

Ahora bien, si en lugar de modificar el objeto **reasignamos el parámetro**, solo estamos cambiando hacia dónde apunta la copia. La variable original sigue apuntando al objeto de siempre:

```java
public void intentarReemplazar(Perro perro) {
    perro = new Perro("Laika", 1); // Solo cambia a dónde apunta la copia
}
```

```java
Perro miPerro = new Perro("Firulais", 3);
intentarReemplazar(miPerro);
System.out.println(miPerro.getNombre()); // Muestra "Firulais": la variable original no cambió
```

Resumiendo: un método puede **modificar** el objeto que recibe, pero no puede **reemplazarlo** por otro. Si necesitamos que lo reemplace, el método debe devolver el objeto nuevo con `return`.

> **Nota:** un `String` es un objeto, pero al ser [inmutable](./clases-utiles.html#string) ningún método puede modificarlo. Por eso los String se comportan como si se pasaran por valor, igual que los tipos primitivos.

## Métodos y atributos estáticos

Vimos que en una clase podemos definir atributos y métodos que serán parte de los objetos creados a partir de ella. ¿Y si necesitamos que un atributo o método sea común a todos los objetos, es decir, que le pertenezca a la clase y no a cada instancia?

Java, así como otros lenguajes de programación, provee una palabra reservada para tal fin: `static`. Puede utilizarse con atributos, constantes o métodos.

Siendo que la palabra reservada `this` referencia al objeto actual, no debemos utilizarla para referirnos a un elemento estático: los elementos estáticos se usan directamente por su nombre, o anteponiendo el nombre de la clase.

```java
public class Perro {

    // Atributo estático, perteneciente a la clase y compartido por todos los objetos
    private static int proximoId = 0;

    // Atributos de cada objeto
    private int identificador;
    private String nombre;
    private int edad;
    private Persona duenio;

    public Perro() {
        this.identificador = ++proximoId; // Primero incrementa y después asigna: el primer perro queda con el 1
        this.nombre = "";
        this.edad = 0;
        this.duenio = null;
    }

    public int getIdentificador() {
        return this.identificador;
    }
}
```

Cada vez que se crea un objeto se le asigna un identificador correlativo: el primer perro tendrá el 1, el segundo el 2, el tercero el 3 y así sucesivamente.

La clave está en la diferencia entre los dos atributos. `proximoId` es **estático**: hay uno solo para toda la clase y su valor sobrevive de un objeto al siguiente. `identificador` no lo es: cada perro tiene el suyo. El [pre incremento](./operadores.html#operadores-unarios-y-ternarios) `++proximoId` incrementa primero y asigna después, y por eso el primer perro recibe el 1 y no el 0.

Notar también que no escribimos un `setIdentificador`: si existiera, cualquiera podría cambiar un identificador desde afuera y romper la correlatividad que la clase se encarga de garantizar.

Los métodos estáticos se invocan usando el nombre de la clase, sin necesidad de crear ningún objeto. Es exactamente lo que hacemos cuando escribimos `Math.abs(-1)` o `Integer.parseInt("5")`.

> **Importante:** un método estático no puede usar atributos ni métodos no estáticos de la clase, porque no está asociado a ningún objeto en particular. El caso más conocido es `main`, que es estático: por eso, para usar nuestras clases desde ahí, primero hay que crear objetos.

## Herencia

La [herencia](https://es.wikipedia.org/wiki/Herencia_(inform%C3%A1tica)) nos permite definir una clase general y, a partir de ella, clases más específicas que reutilizan sus atributos y métodos. La clase general se llama **superclase** (o clase padre) y la específica **subclase** (o clase hija).

Para indicar que una clase hereda de otra usamos la palabra reservada `extends`.

Supongamos que además de perros queremos representar gatos. Ambos son animales: tienen nombre y edad, y ambos cumplen años. Lo que cambia es cómo hacen ruido.

```java
public class Animal {

    // protected permite que las subclases accedan a estos atributos
    protected String nombre;
    protected int edad;

    public Animal(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public String getNombre() {
        return this.nombre;
    }

    public int getEdad() {
        return this.edad;
    }

    public void cumplirAnios() {
        this.edad++;
    }

    public String hacerRuido() {
        return "...";
    }
}
```

Ahora `Perro` y `Gato` pueden extender `Animal`:

```java
public class Perro extends Animal {

    public Perro(String nombre, int edad) {
        super(nombre, edad); // Invoca al constructor de la superclase
    }

    @Override
    public String hacerRuido() {
        return "Guau!";
    }
}
```

```java
public class Gato extends Animal {

    public Gato(String nombre, int edad) {
        super(nombre, edad);
    }

    @Override
    public String hacerRuido() {
        return "Miau!";
    }
}
```

Elementos nuevos en estos ejemplos:

* **`extends Animal`** indica que la clase hereda de `Animal`. `Perro` y `Gato` cuentan con `nombre`, `edad`, `getNombre()`, `getEdad()` y `cumplirAnios()` sin necesidad de volver a escribirlos.
* **`super(...)`** invoca al constructor de la superclase. Debe ser la primera sentencia del constructor de la subclase. También podemos usar `super.` para invocar un método de la superclase.
* **`@Override`** es una anotación que indica que estamos reescribiendo (sobrescribiendo) un método que ya existe en la superclase. No es obligatoria, pero es muy recomendable: si nos equivocamos al escribir la firma del método, el compilador nos avisa.

A esto de volver a definir en la subclase un método que ya existe en la superclase se lo llama **sobrescritura** (*override*). No hay que confundirlo con la [sobrecarga](./metodos.html#sobrecarga-de-métodosfunciones) (*overload*), que es tener varios métodos con el mismo nombre y distinta firma dentro de la misma clase.

> **Nota:** en Java una clase solo puede extender de **una** superclase. Si una clase no extiende explícitamente de ninguna, hereda de `Object`, la clase de la que descienden todas las demás.

## Polimorfismo

El [polimorfismo](https://es.wikipedia.org/wiki/Polimorfismo_(inform%C3%A1tica)) es la posibilidad de tratar a objetos de tipos distintos como si fueran del mismo tipo, y que cada uno responda a su manera.

Como `Perro` y `Gato` son `Animal`, una variable de tipo `Animal` puede contener cualquiera de los dos:

```java
    Animal unAnimal = new Perro("Firulais", 3);
    Animal otroAnimal = new Gato("Michi", 2);

    System.out.println(unAnimal.hacerRuido());  // Guau!
    System.out.println(otroAnimal.hacerRuido()); // Miau!
```

Aunque las dos variables son de tipo `Animal` y la línea que las invoca es idéntica, cada objeto ejecuta **su propia** versión de `hacerRuido()`. Java resuelve en tiempo de ejecución cuál corresponde según el objeto real que hay del otro lado.

Esto es especialmente útil cuando trabajamos con varios objetos a la vez, por ejemplo en un [array](./arrays.html):

```java
    Animal[] animales = new Animal[3];
    animales[0] = new Perro("Firulais", 3);
    animales[1] = new Gato("Michi", 2);
    animales[2] = new Perro("Cartucho", 5);

    // No necesitamos saber de qué tipo es cada uno: cada objeto responde como corresponde
    for (Animal animal : animales) {
        System.out.println(animal.getNombre() + ": " + animal.hacerRuido());
    }
```

Si en algún momento necesitamos saber de qué clase es realmente un objeto, podemos usar el operador [instanceof](./operadores.html#operador-instanceof):

```java
    for (Animal animal : animales) {
        if (animal instanceof Perro) {
            System.out.println(animal.getNombre() + " es un perro");
        }
    }
```

## Garbage collector

Como vimos en [conceptos básicos](./conceptos-basicos.html#dónde-viven-las-variables), para una variable de tipo primitivo se reserva una porción de memoria donde se almacena su valor, en un sector llamado `Stack` (pila). Con los objetos interviene además otro sector de memoria, conocido como `Heap` (montón).

Cuando creamos un objeto, ocurren dos cosas:

* En el **Heap** se reserva el espacio con el contenido del objeto: todos sus atributos (en la clase `Perro`: nombre, edad y duenio).
* En el **Stack** se guarda únicamente la **variable de referencia** (`miPerro`), que no contiene al objeto sino la dirección donde el objeto vive en el Heap.

Por eso, cuando asignamos un objeto a otra variable, no se copia el objeto: las dos variables terminan apuntando al mismo lugar del Heap.

```java
    Perro miPerro = new Perro("Firulais", 3);
    Perro elMismoPerro = miPerro; // No se crea un perro nuevo: ambas variables referencian al mismo objeto

    elMismoPerro.setNombre("Cartucho");
    System.out.println(miPerro.getNombre()); // Muestra "Cartucho": es el mismo objeto
```

Como vimos antes, el Stack se libera automáticamente cuando un método termina. Eso rompe las referencias, pero el Heap **no** libera por sí solo la memoria ocupada por los objetos.

La función del **Garbage collector** ("recolector de basura") es justamente esa: liberar los objetos alojados en el Heap que ya no tienen ninguna referencia que los apunte. Es automático, corre cuando la JVM lo considera necesario y no tenemos que hacer nada para activarlo.

Para más información pueden visitar: [Java Stack y Heap](https://www.baeldung.com/java-stack-heap).

## enum

Un enumerado o "enum" es una "clase especial" que define un conjunto **fijo y conocido** de valores posibles. No se instancia con `new`: cada opción declarada es la única instancia de sí misma. Se usa cuando una variable solo puede tomar valores de una lista cerrada: los días de la semana, los estados de un pedido, los colores disponibles.

Para definir un "enum" reemplazamos la palabra `class` por `enum`. El modificador de acceso suele ser `public` y el nombre sigue la misma convención [PascalCase](https://es.wikipedia.org/wiki/Camel_case) que las clases.

```java
public enum Colores {

}
```

Las opciones del enum se escriben como las constantes: en mayúscula, separando las palabras con guiones bajos.

Internamente, un enum asigna un número de orden a cada opción, comenzando por el cero.

```java
public enum Colores {
    ROJO, AZUL, AMARILLO, BLANCO, NEGRO, AZUL_OSCURO
    //0    1      2         3       4       5
}
```

Las opciones de un enum se usan de manera estática: escribimos el nombre del enum, un `.` (punto) y luego la opción deseada.

```java
    // Este código debe estar dentro de un método
    Colores colorElegido = Colores.AZUL;
```

Al ser un tipo de dato, el enum también puede usarse en un `switch`, y es uno de sus usos más habituales:

```java
    switch (colorElegido) {
        case ROJO:
            System.out.println("Elegiste rojo");
            break;
        case AZUL:
            System.out.println("Elegiste azul");
            break;
        default:
            System.out.println("Elegiste otro color");
    }
```

### Constructores y atributos de un enum

Es posible definirle constructores a un enum, con la salvedad de que deben ser privados, para no permitir que se creen objetos. Si intentamos declarar el constructor como `public`, obtendremos un error de compilación. No hace falta escribir `private`: el enum lo asume automáticamente.

```java
public enum Colores {
    ROJO, AZUL, AMARILLO, BLANCO, NEGRO, AZUL_OSCURO;

    // Constructor del enum
    Colores() {

    }
}
```

¿Por qué podríamos necesitar un constructor?

Un enum permite definir atributos, igual que una clase. Un atributo muy habitual es de tipo `String` y se usa para darle una descripción legible a cada opción, ya que si mostramos una opción por pantalla se muestra su nombre tal cual (por ejemplo, `AZUL_OSCURO`), lo cual no siempre es prolijo.

Podemos entonces agregar un parámetro de tipo `String` al constructor, que asignaremos a un atributo del enum.

```java
public enum Colores {
    // Opciones del enum que asignan en su construcción una descripción amigable
    ROJO("Rojo"), // orden 0
    AZUL("Azul"), // orden 1
    AMARILLO("Amarillo"), // orden 2
    BLANCO("Blanco"), // orden 3
    NEGRO("Negro"), // orden 4
    AZUL_OSCURO("Azul oscuro"); // orden 5. Se agrega ; (punto y coma) al final de la última opción

    // Atributo del enum
    private String descripcion;

    // Constructor del enum que recibe un parámetro y lo asigna al atributo
    Colores(String descripcion) {
        this.descripcion = descripcion;
    }
}
```

Es importante notar que al lado de cada opción se proporciona el dato que recibirá el constructor. Ese es el único lugar donde se puede usar el constructor, justamente porque es privado. También es necesario finalizar la lista de opciones con un `;` (punto y coma); caso contrario obtendremos un error.

El enum no provee una forma automática de obtener esa descripción, así que agregamos un "Getter":

```java
public enum Colores {
    ROJO("Rojo"),
    AZUL("Azul"),
    AMARILLO("Amarillo"),
    BLANCO("Blanco"),
    NEGRO("Negro"),
    AZUL_OSCURO("Azul oscuro");

    private String descripcion;

    Colores(String descripcion) {
        this.descripcion = descripcion;
    }

    public String getDescripcion() {
        return this.descripcion;
    }
}
```

### Métodos que provee un enum

Todo enum cuenta con algunos métodos por defecto. Los más usados son `values()` y `valueOf()`.

```java
    Colores[] todosLosColores = Colores.values(); // Devuelve todas las opciones del enum en un array (ver arrays)

    // El enum puede utilizarse como tipo de dato para declarar una variable
    Colores colorAzul = Colores.valueOf("AZUL"); // valueOf() devuelve la opción cuyo nombre coincide con el texto
    colorAzul = Colores.values()[1]; // También podemos obtener una opción por su número de orden

    int ordinalAzul = Colores.AZUL.ordinal(); // Devuelve 1: el número de orden de la opción
    String nombreAzul = Colores.AZUL.name();  // Devuelve "AZUL": el nombre de la opción como String

    // Obtención de la descripción, usando el Getter que definimos nosotros
    String descripcionAzulOscuro = Colores.AZUL_OSCURO.getDescripcion(); // Devuelve "Azul oscuro"
```

> **Nota:** `valueOf()` lanza un error en tiempo de ejecución si el texto no coincide exactamente con el nombre de ninguna opción (incluidas mayúsculas y minúsculas). Cuando conocemos la opción de antemano, es más seguro escribirla directamente: `Colores.AZUL`.

> **Nota:** escribiendo un punto luego de una opción del enum (`Colores.AZUL.`) el IDE nos muestra todos los métodos disponibles.

El atributo del enum no necesariamente debe ser un `String`: puede ser `int`, `double`, `float`, etc., respetando el tipo de dato en el constructor y en el valor que se le pasa al declarar cada opción.

Ejemplo con un tipo de dato primitivo `int`:

```java
public enum Numeros {
    UNO(1),
    DOS(2),
    TRES(3);

    // Atributo del enum
    private int valor;

    // Constructor del enum que recibe un parámetro y lo asigna al atributo
    Numeros(int valor) {
        this.valor = valor;
    }

    public int getValor() {
        return this.valor;
    }
}
```

[Volver](../)
