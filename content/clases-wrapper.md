---
layout: default
---

[Volver](../)

# Clases Wrapper (Envoltorio)

Para cada tipo de dato primitivo existe una clase Wrapper (o envoltorio) que nos provee de comportamiento (métodos) de uso común, los cuales nos ayudan con los temas conocidos a resolver. Cabe destacar que los Wrappers son clases, razón por la cual, podemos aprovechar el uso de los tipos de datos primitivos como objetos.

En Java, existen 8 tipos de dato primitivos, por ende, contaremos con 8 clases Wrapper.

| Tipo de dato primitivo | Clase Wrapper
|:-----------------------|:------------------|
| byte                   | Byte              |
| short                  | Short             |
| int                    | Integer           |
| long                   | Long              |
| float                  | Float             |
| double                 | Double            |
| char                   | Character         |
| boolean                | Boolean           |

Es posible convertir cada tipo de dato primitivo en su correspondiente Wrapper (Autoboxing), o bien, convertir un tipo de dato Wrapper en un tipo de dato primitivo (Unboxing).

Si definimos una variable con tipo de dato clase Wrapper, provee métodos de utlidad. Además, cada clase Wrapper provee de métodos estáticos útiles. 

## Byte

Es la clase Wrapper del tipo de dato primitivo `byte`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
byte numeroByte = 1; // Tipo de dato primitivo
Byte numeroByteWrapper = 1; // Clase Wrapper
```
Utilizando la clase `Byte` para definir una variable podemos contar con herramientas como las siguientes:

```java
Byte numeroByteWrapper = 1; // Variable con tipo de dato Byte
		
byte numeroByte = numeroByteWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Byte como byte (primitivo)
short numeroShort = numeroByteWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Byte como short (primitivo)
int numeroInt = numeroByteWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Byte como int (primitivo)
long numeroLong = numeroByteWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Byte como long (primitivo)
float numeroFloat = numeroByteWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Byte como float (primitivo)
double numeroDouble = numeroByteWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Byte como double (primitivo)
String numeroComoString = numeroByteWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Byte como String
boolean sonIguales = numeroByteWrapper.equals(numeroByte); // Permite conocer si el contenido de la variable es igual al de otra variable byte

// Constantes estáticas de utilidad
byte maximoValor = Byte.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Byte
byte minimoValor = Byte.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Byte

// Métodos estáticos de utilidad
byte numeroConvertidoDesdeString = Byte.parseByte(numeroComoString); // Devuelve el contenido de la variable String en el argumento como byte (primitivo)
numeroComoString = Byte.toString(numeroByte); // Devuelve el contenido de la variable en el argumento byte como un nuevo objeto String
numeroByteWrapper = Byte.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Byte
```

## Short

Es la clase Wrapper del tipo de dato primitivo `short`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
short numeroShort = 1; // Tipo de dato primitivo
Short numeroShortWrapper = 1; // Clase Wrapper
```
Utilizando la clase `Short` para definir una variable podemos contar con herramientas como las siguientes:

```java
Short numeroShortWrapper = 1; // Variable con tipo de dato Short
		
byte numeroByte = numeroShortWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Short como byte (primitivo)
short numeroShort = numeroShortWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Short como short (primitivo)
int numeroInt = numeroShortWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Short como int (primitivo)
long numeroLong = numeroShortWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Short como long (primitivo)
float numeroFloat = numeroShortWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Short como float (primitivo)
double numeroDouble = numeroShortWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Short como double (primitivo)
String numeroComoString = numeroShortWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Short como String
boolean sonIguales = numeroShortWrapper.equals(numeroShort); // Permite conocer si el contenido de la variable es igual al de otra variable short

// Constantes estáticas de utilidad
short maximoValor = Short.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Short
short minimoValor = Short.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Short

// Métodos estáticos de utilidad
short numeroConvertidoDesdeString = Short.parseShort(numeroComoString); // Devuelve el contenido de la variable String en el argumento como short (primitivo)
numeroComoString = Short.toString(numeroShort); // Devuelve el contenido de la variable en el argumento short como un nuevo objeto String
numeroShortWrapper = Short.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Short
```

## Integer

Es la clase Wrapper del tipo de dato primitivo `int`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
int numeroInt = 1; // Tipo de dato primitivo
Integer numeroIntegerWrapper = 1; // Clase Wrapper
```
Utilizando la clase `Integer` para definir una variable podemos contar con herramientas como las siguientes:

```java
Integer numeroIntegerWrapper = 1; // Variable con tipo de dato Integer
		
byte numeroByte = numeroIntegerWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Integer como byte (primitivo)
short numeroShort = numeroIntegerWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Integer como short (primitivo)
int numeroInt = numeroIntegerWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Integer como int (primitivo)
long numeroLong = numeroIntegerWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Integer como long (primitivo)
float numeroFloat = numeroIntegerWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Integer como float (primitivo)
double numeroDouble = numeroIntegerWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Integer como double (primitivo)
String numeroComoString = numeroIntegerWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Integer como String
boolean sonIguales = numeroIntegerWrapper.equals(numeroInt); // Permite conocer si el contenido de la variable es igual al de otra variable int

// Constantes estáticas de utilidad
int maximoValor = Integer.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Integer
int minimoValor = Integer.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Integer

// Métodos estáticos de utilidad
int numeroConvertidoDesdeString = Integer.parseInt(numeroComoString); // Devuelve el contenido de la variable String en el argumento como int (primitivo)
numeroComoString = Integer.toString(numeroInt); // Devuelve el contenido de la variable en el argumento int como un nuevo objeto String
numeroIntegerWrapper = Integer.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Integer
```

## Long

Es la clase Wrapper del tipo de dato primitivo `long`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
long numeroLong = 1; // Tipo de dato primitivo
Long numeroLongWrapper = 1; // Clase Wrapper
```
Utilizando la clase `Long` para definir una variable podemos contar con herramientas como las siguientes:

```java
Long numeroLongWrapper = 1L; // Variable con tipo de dato Long
		
byte numeroByte = numeroLongWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Long como byte (primitivo)
short numeroShort = numeroLongWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Long como short (primitivo)
int numeroInt = numeroLongWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Long como int (primitivo)
long numeroLong = numeroLongWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Long como long (primitivo)
float numeroFloat = numeroLongWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Long como float (primitivo)
double numeroDouble = numeroLongWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Long como double (primitivo)
String numeroComoString = numeroLongWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Long como String
boolean sonIguales = numeroLongWrapper.equals(numeroLong); // Permite conocer si el contenido de la variable es igual al de otra variable long

// Constantes estáticas de utilidad
long maximoValor = Long.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Long
long minimoValor = Long.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Long

// Métodos estáticos de utilidad
long numeroConvertidoDesdeString = Long.parseLong(numeroComoString); // Devuelve el contenido de la variable String en el argumento como long (primitivo)
numeroComoString = Long.toString(numeroLong); // Devuelve el contenido de la variable en el argumento long como un nuevo objeto String
numeroLongWrapper = Long.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Long
```

## Float

Es la clase Wrapper del tipo de dato primitivo `float`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
float numeroLong = 1; // Tipo de dato primitivo
Float numeroLongWrapper = 1f; // Clase Wrapper
```
Utilizando la clase `Float` para definir una variable podemos contar con herramientas como las siguientes:

```java
Float numeroFloatWrapper = 1f; // Variable con tipo de dato Float
		
byte numeroByte = numeroFloatWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Float como byte (primitivo)
short numeroShort = numeroFloatWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Float como short (primitivo)
int numeroInt = numeroFloatWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Float como int (primitivo)
long numeroLong = numeroFloatWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Float como long (primitivo)
float numeroFloat = numeroFloatWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Float como float (primitivo)
double numeroDouble = numeroFloatWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Float como double (primitivo)
String numeroComoString = numeroFloatWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Float como String
boolean sonIguales = numeroFloatWrapper.equals(numeroFloat); // Permite conocer si el contenido de la variable es igual al de otra variable float

// Constantes estáticas de utilidad
float maximoValor = Float.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Float
float minimoValor = Float.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Float

// Métodos estáticos de utilidad
float numeroConvertidoDesdeString = Float.parseFloat(numeroComoString); // Devuelve el contenido de la variable String en el argumento como float (primitivo)
numeroComoString = Float.toString(numeroFloat); // Devuelve el contenido de la variable en el argumento float como un nuevo objeto String
numeroFloatWrapper = Float.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Float
```

## Double

Es la clase Wrapper del tipo de dato primitivo `double`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
double numeroLong = 1; // Tipo de dato primitivo
Double numeroLongWrapper = 1D; // Clase Wrapper
```
Utilizando la clase `Float` para definir una variable podemos contar con herramientas como las siguientes:

```java
Double numeroDoubleWrapper = 1D; // Variable con tipo de dato Double
		
byte numeroByte = numeroDoubleWrapper.byteValue(); // Devuelve el contenido de la variable de tipo de dato Double como byte (primitivo)
short numeroShort = numeroDoubleWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Double como short (primitivo)
int numeroInt = numeroDoubleWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Double como int (primitivo)
long numeroLong = numeroDoubleWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Double como long (primitivo)
float numeroFloat = numeroDoubleWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Double como float (primitivo)
double numeroDouble = numeroDoubleWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Double como double (primitivo)
String numeroComoString = numeroDoubleWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Double como String
boolean sonIguales = numeroDoubleWrapper.equals(numeroDouble); // Permite conocer si el contenido de la variable es igual al de otra variable double

// Constantes estáticas de utilidad
double maximoValor = Double.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Float
double minimoValor = Double.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Float

// Métodos estáticos de utilidad
double numeroConvertidoDesdeString = Double.parseDouble(numeroComoString); // Devuelve el contenido de la variable String en el argumento como float (primitivo)
numeroComoString = Double.toString(numeroDouble); // Devuelve el contenido de la variable en el argumento double como un nuevo objeto String
numeroDoubleWrapper = Double.valueOf(numeroComoString); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Double
```

## Character

Es la clase Wrapper del tipo de dato primitivo `char`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
char caracter = 'a'; // Tipo de dato primitivo
Character caracterCharacterWrapper = 'a'; // Clase Wrapper
```
Utilizando la clase `Float` para definir una variable podemos contar con herramientas como las siguientes:

```java
Character caracterCharacterWrapper = 'a'; // Variable con tipo de dato Character
char caracter = caracterCharacterWrapper.charValue(); // Devuelve el contenido de la variable de tipo de dato Character como char (primitivo)
String caracterComoString = caracterCharacterWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Character como String
boolean sonIguales = caracterCharacterWrapper.equals(caracter); // Permite conocer si el contenido de la variable es igual al de otra variable char

// Constantes estáticas de utilidad
char maximoValor = Character.MAX_VALUE; // Esta constante estática posee el máximo valor para el tipo de dato Character
double minimoValor = Character.MIN_VALUE;// Esta constante estática posee el mínimo valor para el tipo de dato Character

// Métodos estáticos de utilidad
caracterComoString = Character.toString(caracter); // Devuelve el contenido de la variable en el argumento double como un nuevo objeto String
caracterCharacterWrapper = Character.valueOf(caracter); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Double
boolean esUnaLetraDelAlfabeto = Character.isAlphabetic(caracter); // Devuelve verdadero si es una letra mayúscula, minúscula.
boolean esUnNumero = Character.isDigit(caracter); // Devuelve verdadero si es un número
boolean esUnaLetraOUnNumero = Character.isLetterOrDigit(caracter); // Devuelve verdadero si es una letra o un número.
```

## Boolean

Es la clase Wrapper del tipo de dato primitivo `boolean`. En el siguiente ejemplo veremos cómo definir una variable con el tipo de dato primitivo y con la clase Wrapper.

```java
boolean existe = true; // Tipo de dato primitivo
Boolean existeBoolearWrapper = true; // Clase Wrapper
```
Utilizando la clase `Boolean` para definir una variable podemos contar con herramientas como las siguientes:

```java
Boolean existeBoolearWrapper = true; // Variable con tipo de dato Boolean
boolean existe = existeBoolearWrapper.booleanValue(); // Devuelve el contenido de la variable de tipo de dato Boolean como boolean (primitivo)
String existeComoString = existeBoolearWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Boolean como String
boolean sonIguales = existeBoolearWrapper.equals(existe); // Permite conocer si el contenido de la variable es igual al de otra variable boolean

// Constantes estáticas de utilidad
boolean verdadero = Boolean.TRUE; // Esta constante estática posee el valor de verdad true
boolean falso = Boolean.FALSE;// Esta constante estática posee el valor de verdad false

// Métodos estáticos de utilidad
existeComoString = Boolean.toString(existe); // Devuelve el contenido de la variable en el argumento boolean como un nuevo objeto String
existeBoolearWrapper = Boolean.valueOf(existe); // Devuelve el contenido de la variable en el argumento como un nuevo objeto Boolean
existe = Boolean.getBoolean(existeComoString); // Devuelve el contenido de la variable en el argumento como un boolean
existe = Boolean.parseBoolean(existeComoString); // Devuelve el contenido de la variable en el argumento como un boolean
```

[Volver](../)