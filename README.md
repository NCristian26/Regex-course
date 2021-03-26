<div align="center">
    <h1>CURSO DE REGEX</h1>
</div>

Este repositorio contiene apuntes del [Curso de Expresiones Regulares](https://platzi.com/clases/expresiones-regulares/) de PLATZI 💚. El curso está dirigido por [Alberto Alcocer](https://twitter.com/beco?s=20).

Creación del repositorio: 19/03/2021

Ultima actualización: 19/03/2021

att. C. Nicolas Villamil

<div align="center">
    <img src=images/regex_logo.png alt="Regex logo" width="350px" height="350px">
</div>

## TABLA DE CONTENIDOS
- [ EL LENGUAJE: CARACTERES, OPERADORES, Y CONSTRUCCIONES](#EL-LENGUAJE:-CARACTERES,-OPERADORES,-Y-CONSTRUCCIONES)
  - [Los delimitadores: +, *, ?](#Los-delimitadores:-+,-*,-?)
  - [Los contadores {1, 4}](#Los-contadores-{1,-4})



## EL LENGUAJE: CARACTERES, OPERADORES, Y CONSTRUCCIONES
### Los delimitadores: +, *, ? 
  > Los delimitadores en nuestras clases acotan los match que podemos obtener de la expresión.<br>
 - #### * --> Selecciona 0 o todo <br>
    > Este delimitador sirve para indicar que se debe incluir todo lo que haga o no match  dada una clase. Trae una seleccion completa agrupando los match.
 - #### + --> Selecciona 1 o más 
    >Este delimitador selecciona solamente lo que haga match una o más veces dada una clase. Trae una seleccion unica o completa.
 - #### ? --> Selecciona 0 o 1 
    >Este delimitador nos trae la misma seleccion que el operador * pero caracter por caracter.
### Los contadores {1, 4}
  >Los contadores en las expresiones regulares sirven para delimitar el numero de repeticiones que puede o debe tener una cadena de texto para que haga match. <br>
  La manera de escribir esta condiciòn es como sigue: <br>
  
    {a, b}
  >Siendo { } el par de signos utilizados para delimitar el contador. <br>
  a, el limite inferior del contador. <br>
  Y b, el limite suyperior.

  >Algunos lenguajes permiten el uso de un solo numero cuando estamos siendo estrictos en cuanto al contador.
