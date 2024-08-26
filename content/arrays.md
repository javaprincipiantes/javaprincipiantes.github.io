---
layout: default
---

[Volver](../)

## Arrays

Un array es una estructura que permite almacenar o contener varios elementos del mismo tipo de dato, ya sea primitivo o de alguna clase. Cuando trabajamos con arrays, debemos definir el tamaño del mismo, esto se refiere a la cantidad de elementos que puede contener (como máximo). Este tamaño no se puede cambiar en Java durante la ejecución.

Para declarar un array, debemos indicar el tipo de dato de los elementos que puede contener, seguido, dos corchetes `[]` los cuales indicarán que estamos definiendo un array (en comparación de una variable común) y luego el nombre del array. El nombre de la variable, suele ser escrito en plural.

```java
    // Ejemplo de declaración de un array unidimensional
    tipoDeDato[] elementos;

    // En Java se admite poner los corchetes luego del nombre de la variable
    tipoDeDato elementos[];
```

Luego de definir un array, el mismo debe ser instanciado, como con los objetos, utilizando la palabra reservada `new` seguido del tipo de dato de los elementos que puede contener el array y agregando en el final dos corchetes con el número de elementos que el array podrá contener `new tipoDeDato[10]`.

```java
    // Ejemplo de declaración de un array unidimensional que puede contener hasta 10 elementos
    tipoDeDato[] nombreDelArray = new tipoDeDato[10];

    // En Java se admite poner los corchetes luego del nombre de la variable
    tipoDeDato nombreDelArray[] = new tipoDeDato[10];
```

Los arrays pueden ser de una única dimensión (unidimensionales) o de más de una dimensión (multidimensionales). Cuando instanciamos un array, internamente se manejan con un número de posición o índice. Dicho índice comienza desde 0 (cero).

<img src="/assets/images/examples/arrays/array-unidimensional.jpeg" alt="Ejemplo de array unidimensional">

Cuando instanciamos un array, se reservan espacios de memoria contiguos (uno al lado del otro), respetando la cantidad de elementos que se especificó al momento de ser instanciado (en el ejemplo, 10).

### Arrays de una dimensión (unidimensional)

Para definir un array unidimensional, debemos utilizar solo un par de corchetes (`[]`). Esta definición puede tener su analogía con una única fila con la cantidad de columnas que se defina como cantidad máxima de elementos que puede contener.

```java
    // Ejemplo de declaración de un array unidimensional que puede contener hasta 10 números enteros
    int[] numerosEnteros = new int[10];
```

Si necesitamos que el array pueda contener objetos, simplemente debemos especificar la clase en el tipo de dato.

```java
    // Ejemplo de declaración de un array unidimensional que puede contener hasta 10 objetos de la clase Perro
    Perro[] perros = new Perro[10];
```

### Arrays de mas de una dimensión (multidimensional)

Los arrays de más de una dimensión, deben definirse indicando más de un conjunto de corchetes luego del tipo de dato de los elementos que contendrá el array. Cuando dicho array es instanciado, en el primer par de corchetes, con un número, se definirá la cantiad de filas que va a poseer el array muldimensional, mientras que el segundo par de corchetes, con el número definido, se indicará cuantas columnas tendrá el array en cada fila.

Considerando que el array unidimensional utiliza un índice para indicar las columnas, en el caso de arrays mulidimensionales tendremos dos índices, uno para indicar la fila y otro para indicar la columna.

Un ejemplo muy común es la representación de matrices.

```java
    // Ejemplo de declaración de un array multidimensional que puede contener números enteros.
    // En este caso, representaremos una matriz simétrica
    int[][] matrizDeNumerosEnteros = new int[5][5];
```

De esta manera podemos representar una matriz simétrica de 5 filas y 5 columnas.

<img src="/assets/images/examples/arrays/matriz-simetrica.jpeg" alt="Ejemplo de matriz simétrica">

Es posible también representar matrices asimétricas. Simplemente indicamos un número distinto de filas o columnas, según sea necesario.


Para el siguiente ejemplo, definimos una matriz asimétrica de 5 filas y 10 columnas.

```java
    // Ejemplo de declaración de un array multidimensional que puede contener números enteros.
    // En este caso, representaremos una matriz asimétrica
    int[][] matrizDeNumerosEnteros = new int[5][10];
```

<img src="/assets/images/examples/arrays/matriz-asimetrica-5-10.jpeg" alt="Ejemplo de matriz asimétrica de 5 filas y 10 columnas">

En este ejemplo definimos una matriz asimétrica de 3 filas y 2 columnas.

```java
    // Ejemplo de declaración de un array multidimensional que puede contener números enteros.
    // En este caso, representaremos una matriz asimétrica
    int[][] otraMatrizDeNumerosEnteros = new int[3][2];
```

<img src="/assets/images/examples/arrays/matriz-asimetrica-3-2.jpeg" alt="Ejemplo de matriz asimétrica de 3 filas y 2 columnas">


### Operaciones con arrays

#### Arrays unidimensionales

Usaremos como ejemplo el array de números enteros antes mostrado.

```java
    // Ejemplo de declaración de un array unidimensional que puede contener hasta 10 números enteros
    int[] numerosEnteros = new int[10];
```

Cuando instanciamos un array unidimensional de números enteros, por defecto cada posisión del array tendrá como contenido el número cero.

<img src="/assets/images/examples/arrays/array-unidimensional-con-ceros.jpeg" alt="Ejemplo de array unidimensional con ceros como contenido">

Si necesitamos asignar un nuevo número, una posición del array, debemos indicar entre los corchetes el índice (o posición) donde deseamos realizar esta tarea.

```java
    int[] numerosEnteros = new int[10];
    numerosEnteros[0] = 1;
    numerosEnteros[1] = 2;
    numerosEnteros[2] = 3;
    numerosEnteros[3] = 4;
    numerosEnteros[4] = 5;
```

En el ejemplo anterior, se asigna el número 1 a la primera posición del array de números enteros, el número 2 en la segunda posición y así sucesivamente. El resto del array quedará con los ceros que se asignan por defecto.

<img src="/assets/images/examples/arrays/array-unidimensional-con-numeros-asignados.jpeg" alt="Ejemplo de array unidimensional con números asignados">

En caso de querer asignar todas las posiciones del array, podemos realizarlo de manera manual (como el ejemplo anterior), o bien, utilizar una estructura de iteración como `for`, para hacerlo de manera dinámica.

```java
    int[] numerosEnteros = new int[10];
    // Iteramos sobre el array hasta que el índice sea menor que la cantidad, ya que, no existe la posición 10 (el índice empieza en cero)
    for(int indice = 0; indice < numerosEnteros.length; indice++) {
        numerosEnteros[indice] = indice + 1; // Sumamos 1 al índice para comenzar desde el número 1
    }
```

> **Nota:** numerosEnteros.length nos permite saber la cantidad de elementos que puede contener el array. La cantidad que nos muestra es la misma que indicamos al instanciar el array.

* Acumulador

Para poder conocer el valor total de la suma de todos los números contenidos en cada posición del array, debemos utilizar una variable extra en la cual iremos acumulando la sumatoria.

```java
    int[] numerosEnteros = new int[10];
    // Cargamos el array de números con los números del 1 al 10
    for(int indice = 0; indice < numerosEnteros.length; indice++) {
        numerosEnteros[indice] = indice + 1;
    }

    // Declaramos una variable donde acumularemos la suma de los números en el array. La inicializamos con cero, ya que, no afecta a la suma.
    int acumulador = 0;

    // Iteramos el array acumulando en la variable declarada el número contenido en cada posición 
    for(int indice = 0; indice < numerosEnteros.length; indice++) {
        acumulador += numerosEnteros[indice];
    }

    // Mostramos por pantalla el valor acumulado
    System.out.println("El valor acumulado es: " + acumulador);
```

> **Nota:** De la misma manera podemos realizar otras operaciones aritméticas.

* Contador

En caso de necesitar saber por ejemplo cuantos números contenidos en el array son distintos de cero, podemos utilizar una variable para contar.

```java
    int[] numerosEnteros = new int[10];
    // Colocamos algunos números en el array
    numerosEnteros[0] = 1;
    numerosEnteros[3] = 5;
    numerosEnteros[5] = 3;
    numerosEnteros[7] = 8;

    // Declaramos una variable donde almacenaremos la cuenta de los números en el array distintos de cero. 
    int contador = 0;

    // Iteramos el array acumulando en la variable declarada el número contenido en cada posición 
    for(int indice = 0; indice < numerosEnteros.length; indice++) {
       
       if(numerosEnteros[indice] != 0) {
            contador++;
       }
    }

    // Mostramos por pantalla
    System.out.println("La cantidad de números distintos de cero es: " + contador);
```

* Máximo

Podemos averiguar cuál es el número más grande contenido en el array.

```java
    int[] numerosEnteros = new int[10];
    // Colocamos algunos números en el array
    numerosEnteros[0] = 1;
    numerosEnteros[1] = 7;
    numerosEnteros[2] = 3;
    numerosEnteros[3] = 5;
    numerosEnteros[4] = 2;
    numerosEnteros[5] = 20;
    numerosEnteros[6] = 10;
    numerosEnteros[7] = 7;
    numerosEnteros[7] = 4;
    numerosEnteros[9] = 9;

    // Declaramos una variable donde almacenaremos la cuenta de los números en el array distintos de cero. 
    int maximo = 0;

    for(int indice = 0; indice < numerosEnteros.length; indice++) {
       
       // Verificamos si el número en la posición actual es mayor al número contenido en la variable maximo
       if(numerosEnteros[indice] > maximo) {
            // Es mayor, nos guardamos el número
            maximo = numerosEnteros[indice];
       }
    }

    // Mostramos por pantalla
    System.out.println("El número mas grande es: " + maximo);
```

* Mínimo

Es posible averiguar el número más chico contenido en alguna posición del array.

```java
    int[] numerosEnteros = new int[10];
    // Colocamos algunos números en el array
    numerosEnteros[0] = 30;
    numerosEnteros[1] = 7;
    numerosEnteros[2] = 3;
    numerosEnteros[3] = 5;
    numerosEnteros[4] = 2;
    numerosEnteros[5] = 20;
    numerosEnteros[6] = 10;
    numerosEnteros[7] = 7;
    numerosEnteros[7] = 4;
    numerosEnteros[9] = 9;

    // Declaramos una variable donde almacenaremos la cuenta de los números en el array distintos de cero. 
    int minimo = 0;

    for(int indice = 0; indice < numerosEnteros.length; indice++) {
       
       // Tomamos al primer numero del array como el menor. En las siguientes iteraciones nos fijamos si el numero que esta en la posicion actual del array es menor al almacenado
       if(indice == 0 || numerosEnteros[indice] < minimo ) {
            minimo = numerosEnteros[indice];
       }
    }

    // Mostramos por pantalla
    System.out.println("El número mas chico es: " + minimo);
```

Como desafío, se puede probar qué sucede con los demás tipos de datos primitivos al instanciar un array!

#### Arrays unidimensionales con objetos



[Volver](../)