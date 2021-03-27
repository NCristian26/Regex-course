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
  Y b, el limite superior.

  >Algunos lenguajes permiten el uso de un solo numero cuando estamos siendo estrictos en cuanto al contador.
  - Ejemplo <br>
  > 
    \d{2, 8}
  
  > Esta expresión regular requiere de maxímo 8 digitos y minimo 2 seguidos para hacer match. 

    1234567890
    - Primer match: 12345678
    - Segundo match: 90
  > El contador primero hace match con  la mayor cantidad de repeticiones que encuentre y luego la menor cantidad. Es decir, en el orden de hacer match tiene prioridad el limite superior que el inferior.
  
  >Además, si omitimos uno de los limites, podemos indicar en el caso del limite inferior que no hay un minimo de repeticiones y en el de el superior que no hay un maximo.

    {,5} //No hay un minimo de repeticiones
    {3,} //No hay un maximo de repeticiones  

### (?) como delimitador de matches
  > El delimitador (?) se emplea en dos situaciones: 
  - Cuando necesitamos delimitar el match de una clase ya sea predefinida o construida.
    > 
        \d[-]?
    > En este caso, el delimitador (?) indica que lo indicado en la clase puede o no entrar en el match .

        0-53-- //Acá los matches son (0-) (5) y (3-)
        Entra el 5 porque el - lo hacemos opcional por el delimitador (?)
  - Cuando queremos traer matches por separado generados por otro delimitador.
    >
        \d[,]
