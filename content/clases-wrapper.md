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
float numeroFloat = numeroByteWrapper.floatValue(); // Devuelve el contenido de la variable de tipo de dato Byte como float (primitivo)
double numeroDouble = numeroByteWrapper.doubleValue(); // Devuelve el contenido de la variable de tipo de dato Byte como double (primitivo)
short numeroShort = numeroByteWrapper.shortValue(); // Devuelve el contenido de la variable de tipo de dato Byte como short (primitivo)
int numeroInt = numeroByteWrapper.intValue(); // Devuelve el contenido de la variable de tipo de dato Byte como int (primitivo)
long numeroLong = numeroByteWrapper.longValue(); // Devuelve el contenido de la variable de tipo de dato Byte como long (primitivo)
String numeroComoString = numeroByteWrapper.toString(); // Devuelve el contenido de la variable de tipo de dato Byte como String
boolean sonIguales = numeroByteWrapper.equals(numeroByte); // Permite conocer si el contenido de la variable es igual al de otra variable byte

// Constantes estáticas de utilidad
byte maximoValor = Byte.MAX_VALUE;
byte minimoValor = Byte.MIN_VALUE;

// Métodos estáticos de utilidad
byte numeroConvertidoDesdeString = Byte.parseByte(numeroComoString);
numeroComoString = Byte.toString(numeroByte);
numeroByteWrapper = Byte.valueOf(numeroComoString);
```

[Volver](../)