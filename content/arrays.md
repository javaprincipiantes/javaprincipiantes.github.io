---
layout: default
---

# Arrays

Un array es una estructura que permite almacenar varios elementos del mismo tipo de dato, ya sea primitivo o de alguna clase. Cuando trabajamos con arrays debemos definir su tamaño, es decir, la cantidad de elementos que puede contener. **En Java ese tamaño no se puede cambiar durante la ejecución.**

Para declarar un array debemos indicar el tipo de dato de los elementos que puede contener, seguido de dos corchetes `[]`, que indican que estamos declarando un array (en comparación con una variable común), y luego el nombre del array. El nombre suele escribirse en plural.

```java
// Ejemplo de declaración de un array unidimensional
tipoDeDato[] elementos;

// En Java se admite poner los corchetes luego del nombre de la variable
tipoDeDato elementos[];
```

Luego de declarar un array, el mismo debe ser instanciado, como con los objetos, utilizando la palabra reservada `new` seguida del tipo de dato de los elementos y, entre corchetes, el número de elementos que el array podrá contener: `new tipoDeDato[10]`.

```java
// Ejemplo de un array unidimensional que puede contener hasta 10 elementos
tipoDeDato[] nombreDelArray = new tipoDeDato[10];

// En Java se admite poner los corchetes luego del nombre de la variable
tipoDeDato nombreDelArray[] = new tipoDeDato[10];
```

Los arrays pueden ser de una única dimensión (unidimensionales) o de más de una dimensión (multidimensionales). Para acceder a cada elemento se utiliza un número de posición o índice. **Dicho índice comienza desde 0 (cero)**, con lo cual, en un array de 10 elementos, los índices válidos van del 0 al 9.

<img src="/assets/images/examples/arrays/array-unidimensional.jpeg" alt="Ejemplo de array unidimensional">

Cuando instanciamos un array, se reservan espacios de memoria contiguos (uno al lado del otro), respetando la cantidad de elementos que se especificó al momento de instanciarlo (en el ejemplo, 10).

> **Importante:** si intentamos usar un índice que no existe (por ejemplo, la posición 10 en un array de 10 elementos), el programa no falla al compilar, pero se interrumpe al ejecutarse con el error `ArrayIndexOutOfBoundsException`.

## Arrays de una dimensión (unidimensional)

Para definir un array unidimensional debemos utilizar solo un par de corchetes (`[]`). Podemos pensarlo como una única fila, con tantas columnas como elementos pueda contener.

```java
// Array unidimensional que puede contener hasta 10 números enteros
int[] numerosEnteros = new int[10];
```

Si necesitamos que el array pueda contener objetos, simplemente indicamos la clase como tipo de dato.

```java
// Array unidimensional que puede contener hasta 10 objetos de la clase Perro
Perro[] perros = new Perro[10];
```

También podemos crear un array y cargarlo con valores en la misma línea. En ese caso no hace falta indicar el tamaño: lo determina la cantidad de valores que escribimos.

```java
// Array de 5 elementos, ya inicializado
int[] numerosEnteros = {1, 2, 3, 4, 5};
```

## Arrays de más de una dimensión (multidimensional)

Los arrays de más de una dimensión deben declararse indicando más de un par de corchetes luego del tipo de dato. Cuando el array es instanciado, el número del primer par de corchetes define la cantidad de **filas**, mientras que el del segundo par define cuántas **columnas** tendrá cada fila.

Considerando que el array unidimensional utiliza un índice para indicar la posición, en los arrays multidimensionales tendremos dos índices: uno para la fila y otro para la columna.

Un ejemplo muy común es la representación de matrices.

```java
// Array multidimensional que puede contener números enteros.
// En este caso representamos una matriz cuadrada
int[][] matrizDeNumerosEnteros = new int[5][5];
```

De esta manera podemos representar una matriz cuadrada de 5 filas y 5 columnas.

<img src="/assets/images/examples/arrays/matriz-simetrica.jpeg" alt="Ejemplo de matriz cuadrada de 5 filas y 5 columnas">

También es posible representar matrices rectangulares. Simplemente indicamos un número distinto de filas y de columnas, según sea necesario.

Para el siguiente ejemplo definimos una matriz rectangular de 5 filas y 10 columnas.

```java
// Matriz rectangular de 5 filas y 10 columnas
int[][] matrizDeNumerosEnteros = new int[5][10];
```

<img src="/assets/images/examples/arrays/matriz-asimetrica-5-10.jpeg" alt="Ejemplo de matriz rectangular de 5 filas y 10 columnas">

En este otro ejemplo definimos una matriz rectangular de 3 filas y 2 columnas.

```java
// Matriz rectangular de 3 filas y 2 columnas
int[][] otraMatrizDeNumerosEnteros = new int[3][2];
```

<img src="/assets/images/examples/arrays/matriz-asimetrica-3-2.jpeg" alt="Ejemplo de matriz rectangular de 3 filas y 2 columnas">

> **Nota:** en matemática, una matriz **cuadrada** es la que tiene la misma cantidad de filas y columnas. No hay que confundirla con una matriz *simétrica*, que es un concepto distinto (una matriz cuadrada que coincide con su transpuesta).

## Operaciones con arrays

### Arrays unidimensionales

Usaremos como ejemplo el array de números enteros antes mostrado.

```java
int[] numerosEnteros = new int[10];
```

Cuando instanciamos un array de números enteros, cada posición del array queda con el número cero como contenido. Ese es el valor por defecto de los tipos numéricos; para `boolean` es `false` y para las clases (por ejemplo `String`) es `null`.

<img src="/assets/images/examples/arrays/array-unidimensional-con-ceros.jpeg" alt="Ejemplo de array unidimensional con ceros como contenido">

Si necesitamos asignar un número a una posición del array, debemos indicar entre corchetes el índice (o posición) donde queremos hacerlo.

```java
int[] numerosEnteros = new int[10];
numerosEnteros[0] = 1;
numerosEnteros[1] = 2;
numerosEnteros[2] = 3;
numerosEnteros[3] = 4;
numerosEnteros[4] = 5;
```

En el ejemplo anterior se asigna el número 1 a la primera posición del array, el número 2 a la segunda y así sucesivamente. El resto del array queda con los ceros asignados por defecto.

<img src="/assets/images/examples/arrays/array-unidimensional-con-numeros-asignados.jpeg" alt="Ejemplo de array unidimensional con números asignados">

En caso de querer asignar todas las posiciones del array, podemos hacerlo de manera manual (como en el ejemplo anterior) o bien utilizar una estructura de iteración como `for`.

```java
int[] numerosEnteros = new int[10];
// Iteramos mientras el índice sea menor que la cantidad de elementos, ya que no existe la posición 10 (el índice empieza en cero)
for (int indice = 0; indice < numerosEnteros.length; indice++) {
    numerosEnteros[indice] = indice + 1; // Sumamos 1 al índice para que los números empiecen en 1
}
```

> **Nota:** `numerosEnteros.length` nos permite saber la cantidad de elementos que puede contener el array. Es la misma cantidad que indicamos al instanciarlo. Notar que `length` no lleva paréntesis: es un atributo, no un método.

Para recorrer un array de principio a fin sin necesitar el índice, existe además una variante del `for` conocida como *for each*:

```java
int[] numerosEnteros = {1, 2, 3, 4, 5};

// En cada vuelta, la variable numero contiene un elemento del array
for (int numero : numerosEnteros) {
    System.out.println(numero);
}
```

* Acumulador

Para conocer la suma de todos los números contenidos en el array, debemos utilizar una variable extra en la cual iremos acumulando la sumatoria (ver [acumulador](./conceptos-basicos.html#acumulador)).

```java
int[] numerosEnteros = new int[10];
// Cargamos el array con los números del 1 al 10
for (int indice = 0; indice < numerosEnteros.length; indice++) {
    numerosEnteros[indice] = indice + 1;
}

// Declaramos la variable donde acumularemos la suma. La inicializamos en cero, ya que no afecta a la suma
int acumulador = 0;

// Iteramos el array acumulando el número contenido en cada posición
for (int indice = 0; indice < numerosEnteros.length; indice++) {
    acumulador += numerosEnteros[indice];
}

// Mostramos por pantalla el valor acumulado
System.out.println("El valor acumulado es: " + acumulador); // 55
```

> **Nota:** de la misma manera podemos realizar otras operaciones aritméticas.

* Contador

En caso de necesitar saber, por ejemplo, cuántos números contenidos en el array son distintos de cero, podemos utilizar una variable para contar (ver [contador](./conceptos-basicos.html#contador)).

```java
int[] numerosEnteros = new int[10];
// Colocamos algunos números en el array. El resto de las posiciones queda en cero
numerosEnteros[0] = 1;
numerosEnteros[3] = 5;
numerosEnteros[5] = 3;
numerosEnteros[7] = 8;

// Declaramos la variable donde llevaremos la cuenta de los números distintos de cero
int contador = 0;

// Iteramos el array e incrementamos el contador cada vez que se cumple la condición
for (int indice = 0; indice < numerosEnteros.length; indice++) {

    if (numerosEnteros[indice] != 0) {
        contador++;
    }
}

// Mostramos por pantalla
System.out.println("La cantidad de números distintos de cero es: " + contador); // 4
```

* Máximo

Podemos averiguar cuál es el número más grande contenido en el array.

Para eso tomamos el primer elemento como máximo provisorio y, en cada vuelta, lo reemplazamos si encontramos uno mayor. Es importante **no** inicializar la variable en cero: si todos los números del array fueran negativos, el resultado sería incorrectamente cero.

```java
int[] numerosEnteros = {1, 7, 3, 5, 2, 20, 10, 7, 4, 9};

// Tomamos el primer número del array como máximo provisorio
int maximo = numerosEnteros[0];

for (int indice = 1; indice < numerosEnteros.length; indice++) {

    // Verificamos si el número en la posición actual es mayor al que tenemos guardado
    if (numerosEnteros[indice] > maximo) {
        // Es mayor: nos guardamos el número
        maximo = numerosEnteros[indice];
    }
}

// Mostramos por pantalla
System.out.println("El número más grande es: " + maximo); // 20
```

* Mínimo

Con la misma idea podemos averiguar el número más chico contenido en el array; solo cambia la comparación.

```java
int[] numerosEnteros = {30, 7, 3, 5, 2, 20, 10, 7, 4, 9};

// Tomamos el primer número del array como mínimo provisorio
int minimo = numerosEnteros[0];

for (int indice = 1; indice < numerosEnteros.length; indice++) {

    // Verificamos si el número en la posición actual es menor al que tenemos guardado
    if (numerosEnteros[indice] < minimo) {
        minimo = numerosEnteros[indice];
    }
}

// Mostramos por pantalla
System.out.println("El número más chico es: " + minimo); // 2
```

Como desafío, se puede probar qué sucede con los demás tipos de datos primitivos al instanciar un array.

### Arrays unidimensionales con objetos

Un array también puede contener objetos (ver [clases](./clases.html)). La diferencia importante es que, al instanciar el array, **no se crean los objetos**: cada posición queda en `null`, es decir, sin ningún objeto asignado.

```java
// Se crea el array con 3 posiciones, pero todavía no hay ningún perro
Perro[] perros = new Perro[3];

// Cada posición del array vale null
System.out.println(perros[0]); // null
```

Debemos entonces crear cada objeto y asignarlo a una posición:

```java
Perro[] perros = new Perro[3];

perros[0] = new Perro("Firulais", 3);
perros[1] = new Perro("Cartucho", 5);
perros[2] = new Perro("Laika", 1);
```

Una vez cargado el array, podemos recorrerlo e invocar los métodos de cada objeto:

```java
for (int indice = 0; indice < perros.length; indice++) {
    System.out.println(perros[indice].getNombre());
}

// O con la variante for each
for (Perro perro : perros) {
    System.out.println(perro.getNombre());
}
```

> **Importante:** si una posición quedó en `null` e intentamos invocar un método sobre ella, el programa se interrumpe con el error `NullPointerException`. Por eso, cuando no estamos seguros de haber cargado todas las posiciones, conviene verificarlo antes.

```java
for (Perro perro : perros) {
    if (perro != null) {
        System.out.println(perro.getNombre());
    }
}
```

### Arrays multidimensionales

Para recorrer una matriz necesitamos dos índices, uno por dimensión, con lo cual usaremos un `for` dentro de otro `for`. El `for` externo recorre las filas y el interno las columnas de esa fila.

```java
int[][] matriz = new int[3][2]; // 3 filas, 2 columnas

// Cargamos la matriz
for (int fila = 0; fila < matriz.length; fila++) {           // matriz.length -> cantidad de filas
    for (int columna = 0; columna < matriz[fila].length; columna++) { // matriz[fila].length -> cantidad de columnas
        matriz[fila][columna] = fila + columna;
    }
}
```

Para mostrar el contenido de la matriz respetando su forma, aprovechamos que `print` no agrega un salto de línea y que `println` sí lo hace:

```java
for (int fila = 0; fila < matriz.length; fila++) {
    for (int columna = 0; columna < matriz[fila].length; columna++) {
        System.out.print(matriz[fila][columna] + " ");
    }
    System.out.println(); // Salto de línea al terminar cada fila
}
```

El acumulador, el contador, el máximo y el mínimo funcionan igual que en un array unidimensional: solo cambia que la variable se declara antes de los dos `for` y la comparación ocurre dentro del `for` interno.

```java
int acumulador = 0;

for (int fila = 0; fila < matriz.length; fila++) {
    for (int columna = 0; columna < matriz[fila].length; columna++) {
        acumulador += matriz[fila][columna];
    }
}

System.out.println("La suma de todos los elementos es: " + acumulador);
```
