## Ejercicio 2

> ¿Cuál es la importancia de la sintaxis para un lenguaje? ¿Cuáles son sus elementos?

La sintaxis sirve para establecer un conjunto de reglas formales para la computadora, es un convenio con el usuario donde ambos se entienden y sirve como el primer chequeo de que una instruccion esta bien.

Los elementos que la componen son **alfabeto**, el cual es el conjunto de caracteres permitidos, los **identificadores** los cuales son los nombres de variables, funciones, etc. que define el programador, los **operadores**, simbolos como +, -, /, ., etc. Las **palabras clave** como if, else while y los **comentarios y espacios en blanco**. 

## Ejercicio 3

>Explique a qué se denomina regla lexicográfica y regla sintáctica

**Sintaxis:** Gramatica del programa, fundamental para la traduccion, verificabilidad y legibilidad.

**Reglas sintacticas:** Conjunto de reglas que define como se combinan y estructuran plaabras para armar **expresiones y sentencias**.

## Ejercicio 4

> ¿En la definición de un lenguaje, a qué se llama palabra reservadas? ¿A qué son equivalentes en la definición de una gramática? De un ejemplo de palabra reservada en el lenguaje que más conoce. (Ada,C,Ruby,Python,..).

Una palabra clave es una palabra que tiene un significado predefinido en el contexto particular y no puede ser usada como identificador por el programador. Ejemplos de esto son int, char, break y for

## Ejercicio 5

> Ejercicio de Gramática BNF
> Dada la siguiente gramática escrita en BNF:
> 
> ```text
> G = (N, T, S, P)
> 
> N = { <numero_entero>, <digito> }
> T = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 }
> S = <numero_entero>
> P = { 
>     <numero_entero> ::= <numero_entero> | <numero_entero><digito> | <digito>
>     <digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 
> }
> ```
> 
> a- Identifique las componentes de la misma.
> b- Indique por qué es ambigua y corríjala.

Es ambigua porque tiene dos recursiones iguales

## Ejercicio 6

>Defina en BNF (Gramática de contexto libre desarrollada por Backus- Naur) la gramática para la definición de una palabra cualquiera.

```text
G = (N, T, S, P)

N = { <letra>, <palabra> }

T = { A, B, C, … , X, Y, Z, Á, É, Í, Ó, Ú, a, b, … , y, z, á, …}

S = { <palabra> }

P = {

<palabra> ::= <letra> | <letra><palabra>

<letra> ::= A | B | … | Y | Z | Á | É | Í | Ó | Ú | a | b | … | y | z | á | …

}
```

## Ejercicio 7

> Defina en EBNF la gramática para la definición de números reales. Inténtelo desarrollar para BNF y explique las diferencias con la utilización de la gramática EBNF.

```text
G = (N, T, S, P)

N = { <numero_real>, <entero>, <digito> }

T = { 0, 1, … , 8, 9, +, -, . }

S = { <numero_real> }

P _(EBNF)_= {

<numero_real> ::= [ (+ | - ) ]<entero>[ **.**<entero> ]

<entero> ::= { <digito> }+

<digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

}

P _(BNF)_= {

<numero_real> ::= +<entero> | -<entero> |+<entero>**.**<entero> | -<entero>**.**<entero>

<entero> ::= <digito> | <digito><entero>

<digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

}
```

## Ejercicio 8

>Utilizando la gramática que desarrolló en los puntos 6 y 7, escriba el árbol sintáctico de: 
>a. Conceptos 
>b. Programación 
>c. 1255869 
>d. 854,26 
>e. Conceptos de lenguajes

```
 - Conceptos -
<palabra> 
├── <letra> ── C
└── <palabra>
 ├── <letra> ── O 
 └── <palabra>
  ├── <letra> ── N 
  └── <palabra> 
   ├── <letra> ── C 
   └── <palabra> 
    ├── <letra> ── E 
    └── <palabra> 
     ├── <letra> ── P 
     └── <palabra> 
      ├── <letra> ── T 
      └── <palabra> 
       ├── <letra> ── O 
       └── <palabra> 
        └── <letra> ── S  
```

```
 - 1255869 -
<numero_real> 
└── <entero> 
├── <digito> ── 1 
└── <entero> 
 ├── <digito> ── 2 
 └── <entero> 
  ├── <digito> ── 5 
  └── <entero> 
   ├── <digito> ── 5 
   └── <entero> 
    ├── <digito> ── 8 
    └── <entero> 
     ├── <digito> ── 6 
     └── <entero> 
      └── <digito> ── 9
```

```
 - 854,26 -
<numero_real> 
├── <entero> 
│ 
├── <digito> ── 8 
│ └── <entero> 
│ ├── <digito> ── 5 
│ └── <entero> 
│ └── <digito> ── 4 
├── . 
└── <entero> 
 ├── <digito> ── 2 
 └── <entero> 
  └── <digito> ── 6
```

```
 - Conceptos de lenguajes -
No se puede definir con lo que tenemos actualmente ya que la plabara no contempla espacios, deberiamos definir <oracion>
```

## Ejercicio 9

> Defina utilizando diagramas sintácticos la gramática para la definición de un identificador de un lenguaje de programación. Tenga presente como regla que un identificador no puede comenzar con números.

```
BNF

<id> ::= <letra> | <letra><caracter>

<caracter> ::= <letra> | <digito> | <letra><caracter | <digito><caracter>

<digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<letra> ::= A | B | … | Y | Z | a | b | … | y | z

EBNF

<id> ::= <letra>[ {<caracter>}* ]

<caracter> ::= (<digito> | <letra>)

<digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<letra> ::= A | B | … | Y | Z | a | b | … | y | z
```

## Ejercicio 10

>a) Defina con EBNF la gramática para una expresión numérica, dónde intervienen variables y números. Considerar los operadores +, -, * y / sin orden de prioridad. No considerar el uso de paréntesis. 
>b) A la gramática definida en el ejercicio anterior agregarle prioridad de operadores. 
>c) Describa con sus palabras los pasos y decisiones que tomó para agregarle prioridad de operadores al ejercicio anterior.

```
a). G = (N, T, P, S)

N = { <expr>, <operando>, <operador>, <id>, <numero_real>, <entero>, <digito>, <letra>, <caracter> }

T = { 0 | 1 | … | 8 | 9 | + | - | * | / | . }

S = { <expr> }

P = {

<expr> ::= <operando>{<operador><operando>}*

<operando> ::= (<numero_real> | <id>)

<operador> ::= (+ | - | * | / )

<numero_real>, <id>, <entero>, <digito>, <letra>, <caracter> ::= (ya definidos antes)

}

b).

P = {

<expr> ::= <termino> { <operador_sr><termino> }*

<termino> ::= <operando> { <operador_md><operando> }*

<operando> ::= ( <id> | <numero_real> )

<operando_sr> ::= ( + | - )

<operando_md> ::= ( * | / )

}

c). Pensamos las operaciones como sumas o restas de terminos, se sumaria o restaria el resultado de esa multiplicacion o division, haciendo que tenga prioridad
```

## Ejercicio 12

>Realice en EBNF la gramática para la definición un tag div en html 5. (Puede ayudarse con el siguiente enlace (https://developer.mozilla.org/es/docs/Web/HTML/Elemento/div)

```
N = { <sentencia>, <apertura>, <atributo>, <palabra> }

P = {

<sentencia> ::= <apertura><bloque_codigo>”</div>”

<apertura> ::= “<div “{ <atributos> }*”>”

<bloque_codigo> ::= (<texto> | <sentencia> | <otra_etiqueta>)

<texto> ::= { <palabras> }+

<otra_etiqueta> ::= … (me ahorro el quilombo)

}
```

## Ejercicio 13

> Ejercicio 13: Defina en EBNF una gramática para la construcción de números primos.¿Qué debería agregar a la gramática para completar el ejercicio?

No tiene sentido el enunciado ya que un numero primo es un numero como cualquier otro, no hay manera de poner condicionales en la definicion sintactica

## Ejercicio 14

>Sobre un lenguaje de su preferencia escriba en EBNF la gramática para la definición de funciones o métodos o procedimientos (considere los parámetros en caso de ser necesario)

```
N = { <funcion>, <privacidad>, <tipo>, <nombre>, <parametro>, <bloque_codigo>, <valor>, <linea> }

P = {

<funcion> ::= <privacidad> <tipo> <nombre> ( { <parametro> [,] }* ) “{” <bloque_codigo> [ return <valor> ] “}”

<privacidad> ::= (public | internal | protected | private)

<tipo> ::= (int | boolean | string | char | double | void)

<nombre> ::= <letra>{ <caracter_valido> }*

<parametro> ::= <tipo> <etiqueta>

<bloque_codigo> ::= { <linea> ; }*

<linea> ::= { (<palabra> | <caracter>)

<valor> ::= (<etiqueta> | <numero> | <palabra>)
```

