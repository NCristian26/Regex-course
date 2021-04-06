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
  > Los contadores en las expresiones regulares sirven para delimitar el numero de repeticiones  que puede o debe tener una cadena de texto para que haga match.La manera de escribir esta condiciòn es como sigue:

    {a, b}
  > Siendo { } el par de signos utilizados para anotar el contador. <br>
  a, el limite inferior del contador. <br>
  Y b, el limite superior.

  >Algunos lenguajes permiten el uso de un solo numero cuando estamos siendo estrictos en cuanto al contador. 
  - Ejemplo 
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
    > En este caso, el delimitador (?) indica el caracter (-) puede o no estar en la cadena de texto para hacer match.

        0-53-- //Acá los matches son (0-) (5) y (3-)
        Entra el 5 porque el - lo hacemos opcional por el delimitador (?)
  - Cuando queremos traer matches por separado generados por otro delimitador.
    >
        .+?[,\n] //Va  junto a otro delimitador
    > El primer delimitador cumple su función normal que en este caso es indicar que debe hacer uno o más. De esta forma el delimitador (?) está indicando que cada match lo debe traer por separado en vez de juntar todos los matches en uno si es que se siguen. 

        csv1,csv2,csv3,csv4
        123,543,234,435,678
        234,765,567,879,231
        
        Acá los matches son cada una de las expresiones que tengan uno o mas caracteres seguido de una coma. Es decir (csv1,) (csv2,) (csv3,)...
        Sin el delimitador (?) el match sería la linea completa (csv1,csv2,csv3,csv4) (123,543,234,434,678,), lo cual no es util si la intención es trabajar con un csv.
  >En conclusión, la función de (?) como delimitador conociste justamente en delimitar a la menor cantidad posible de los matches.

### Not (^), su uso y sus peligros

>La negación en expresiones regulares se usa para indicar que debe traer todo lo que NO coincida con el patrón. <br>
>La negación en expresiones regulares se indica así: <br>
> - Para las clases predefinidas se escribe la letra en mayuscula.

    Para digitos \D //Trae cualquier cosa que No sea digito ej. (abc_D)
    Para caracteres \W //Trae cualquier cosa que NO sea caracter ej. (:/-\n)
    Para espacios \S //Trae cualquier cosa que No sea un salto de linea ej. (01fe/:)

> - Para las clases construidas se escribe el caracter (^) al inicio de la clase.

    [^0-5a-c] //Trae Todos los digitos que NO esten entre 0 y 5 y todos los caracteres que No esten entre a y c.

### El principio (^) y el final de linea ($)

>Cuando lo que se quiere es usar las expresiones regulares para evaluar una linea completa, debemos usar los caracteres (^) y ($). <br>


    El caracter (^) indica el inicio de linea.
    Por su parte el caracter ($) denota el final de linea.

    Ej. ^asi "ve" el editor de texto una linea con su inicio y su fin$

>Esto es importante en muchas aplicaciones de las expresiones regulares como cuando por ejemplo se quiere incluir solamente aquellas cadenas de texto que esten al inicio o al final de una linea.

    $\d+,

>Esta expresion regular solamente admite aquellas cadenas de caracteres que estén al inicio de una linea (^), tengan uno o mas digitos (\d+) y al final tengan una coma (,). <br>
>Sin el caracter (^) que denota el inicio de linea, no habria manera de indicar que lo que queremos debe estar al inicio de la linea. Lo mismo funciona para el final de linea ($).

>Cuando queremos validar que una linea completa haga o no match sin incluir resultados parciales utilizamos los dos caracteres (^) y ($).

    ^\d{3,5}$

>Esta expresion regular lo que nos traería sería solamente aquellas lineas que comiencen, tengan entre 3 y 5 digitos e inmetiatamente terminen sin dejar opcion a aquellas lineas que tengan algo más. <br>
>Esto nos sirve esencialmente cuando lo que queremos es evaluar lineas completas. Por ejemplo en un archivo csv donde nos interesa traer solamente las lineas que contegan determinada forma. 