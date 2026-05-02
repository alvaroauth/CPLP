## Ejercicio 1

> a. Tome una de las variables de la línea 3 del siguiente código e indique y defina cuales son sus atributos: 
> b.Compare los atributos de la variable del punto a) con los atributos de la variable de la línea 4. Que dato contiene esta variable?
```pascal
Procedure Practica4();
var
	a, i: integer;
	p: puntero;
Begin
	a := 0;
	new(p);
	p := ^i;
	for i := 1 to 9 do
		a := 0;
	end;
	// ...
	p := a;
	// ...
	dispose(p);
end;
```


| Ident. | L-Value    | R-Value | Alcance | T.V    |
| ------ | ---------- | ------- | ------- | ------ |
| a      | automatico | indef   | 4 - 16  | 1 - 16 |
| p      | automatico | nil     | 5 - 16  | 1 - 16 |
| p^     | dinamico   | indef   | 5 - 16  | 7 - 15 |

## Ejercicio 2

> a. Indique cuales son las diferentes formas de inicializar una variable en el momento de la declaración de la misma
> b. Analice en los lenguajes: Java, C, Phyton y Ruby las diferentes formas de inicialización de variables que poseen. Realice un cuadro comparativo de esta característica.

a. 
1. **Inicializacion explicita:** El lenguaje permite al programador especificar el valor exacto directamente en la instruccion donde se define la variable
2. **Inicializacion implicita:** El lenguaje le asigna un valor automatico si el programador no lo hace dependiendo el tipo de variable
3. **Ninguna de las dos:** El sistema no limpia la memoria por lo que la variable asume de manera implicita la cadena de bits residual que se encontraba almacenada antes
b.

| Lenguaje   | Tipo de Ligadura (Variable-Tipo) | ¿Requiere declaración previa explícita? | Estrategia de Inicialización Principal                | Comportamiento si no se inicializa explícitamente                                 |
| ---------- | -------------------------------- | --------------------------------------- | ----------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Java**   | Estática (Tiempo de compilación) | Sí                                      | Explícita en declaración o instanciación de objetos,. | Error de compilación (variables locales) / Inicialización a `null` (referencias). |
| **C**      | Estática (Tiempo de compilación) | Sí                                      | Explícita en la declaración (ej. `int i = 0;`).       | Puede tomar "basura" de la memoria, o inicializarse en `0` por defecto.           |
| **Python** | Dinámica (Tiempo de ejecución)   | No                                      | Automática durante la primera asignación de valor,.   | No es posible usar una variable sin haberle asignado un valor previamente.        |
| **Ruby**   | Dinámica (Tiempo de ejecución)   | No                                      | Automática durante la primera asignación de valor,.   | No aplicable (la variable nace en la asignación).                                 |
## Ejercicio 3

> Explique los siguientes conceptos asociados al atributo l-valor de una:

**a) Variable estática.**
Su *L-Value* se aloca en tiempo de compilacion. Se reserva en una zona fija de datos y su vida perdura hasta el final de la ejecucion del programa
	**Ejemplo:** Las variables definidas como static en C

**b) Variable automática.**
Su *L-Value* se asigna de manera automatica durante la ejecucion, cuando el flujo del programa alcanza donde esta declarada la variable. Se gestiona usando la pila la cual crea un registro de activacion al entrar a la rutina o bloque y se destruye al salir de ella
	**Ejemplo:** Las variables locales comunes de Pascal o C

**c) Variable dinámica.**
Su *L-Value* se aloca en ejecucion pero por pedido explicito del programador mediante instrucciones de creacion como `new()`  o constructores. Estas variables se almacenan en la heap
	**Ejemplo:** Las variables instanciadas a traves de punteros usando new en c++ (`node* n = new node;`)

**d) Variable semidinámica.**
Su *L-Value* se aloca en la pila durante la ejecucion, pero no se conoce el tamaño durante la compilacion. El espacio exacto se calcula en ejecucion  y una vez alocada en memoria queda fija
	**Ejemplo:** Los arreglos dinamicos de ADA, en este lenguaje se pueden crear arreglos de tamaño irrestricto (`type VECTOR is array (INTEGER range <>)`) y asignarle limites como 0..N al momento de instanciar la variable

## Ejercicio 4

> **a.** ¿A qué se denomina variable local y a qué se denomina variable global?

Una **variable local** es aquella que se declara internamente dentro de un bloque o subprograma. EL uso se limita solo a esa parte por lo que ninguna otra parte del programa puede verla ni modificarla

Una **variable global** se declara fuera de cualquier modulo y es visible y accesible desde cualquier parte del codigo 

> **b.** ¿Una variable local puede ser estática respecto de su l-valor? En caso afirmativo dé un ejemplo

Si, una variable local puede ser estatica
Esto pasa cuando una variable tiene un alcance estrictamente local, limitado al subprograma donde fue declarada, pero su *L-Value* se reserva en la zona de datos antes que comience la ejecucion y perdura activa durante todo el ciclo del programa.
Esto genera que la variable no se destruya al salir de una rutina y conserva su valor entre diferentes llamadas
**Ejemplo:** 
```C
int contador_llamadas() {
    static int contador = 0; /* Alcance local, pero l-valor y tiempo de vida estáticos */
    contador = contador + 1;
    return contador;
}
```
En este ejemplo, la variable `contador` solo puede ser leída o modificada desde el interior de la función `contador_llamadas` porque su alcance es local. Sin embargo, al tener un l-valor estático, la variable conserva su estado en la memoria y recordará el número incrementado cada vez que la función vuelva a ser invocada a lo largo del programa.

> **c.** Una variable global ¿siempre es estática? Justifique la respuesta.

Si, en cuanto a *L-Value* y tiempo de vida
Dado que las variables globales se declaran en un entorno principal y deben ser accesibles para conservar y compartir su valor a lo largo de toda la ejecucion del programa, su espacio de memoria es estatico

> **d.**  Indique qué diferencia hay entre una variable estática respecto de su l-valor y una constante

**Variable estatica:** Su direccion de meoria se reserva antes de ejecucion y se mantiene vivo durante todo el programa. Su *R-Value* puede cambiar a lo largo de la ejecucion

**Constante:** Su *R-Value* no se puede modificar durante ejecucion. Tambien una constante no suele tener un *L-Value* asignado en memoria, se usa como un nombre simbolico para un valor

## Ejercicio 5

> **a.** En Ada hay dos tipos de constantes, las numéricas y las comunes. Indique a que se debe dicha clasificación.

**Constantes comunes:** Tienen un tipo de dato explicito y su valor se liga en tiempo de ejecucion, osea que se pueden usar otras variables o constantes para darle valor inicial

**Constantes numericas:** Su valor se liga y congela en tiempo de compilacion, requieren el uso de expresiones estaticas o valores fijos, toamn un tupo universal que las hace compatibles con cualquier numero

>**b.** En base a lo respondido en el punto a), determine el momento de ligadura de las constantes del siguiente código: 
```
H: constant Float:= 3,5;
I: constant:= 2; 
K: constant float:= H*I;
```

1. `H: constant Float:= 3,5;` : Al definirle explicitamente el tipo de dato float, se trata como constante comun, con momento de ligadura dinamico y establecido en tiempo de ejecucion
2. `I: constant:= 2; ` : Al no especificar un tipo de dato se trata de una constante numerica. Tiene momento de ligadura estatico y se establece en tiempo de compilacion
3. `K: constant float:= H*I;` : Se pone un tipo de dato explicito asi que es una constante comun, como `H` e `I` ya tienen un valor, no hay ningun drama

## Ejercicio 6
> Sea el siguiente archivo con funciones de C:
```C
Archivo.c 
{ 
	int x=1; (1) 
	int func1();{ 
		int i; 
		for (i:=0; i < 4; i++) x=x+1; 
	} 
	int func2();{ 
		int i, j; /*sentencias que contienen declaraciones y sentencias que 
					no contienen declaraciones*/ 
		...... 
		for (i:=0; i < 3; i++) j=func1 + 1; 
	} 
}
```

> Analice si llegaría a tener el mismo comportamiento en cuanto a alocación de memoria, sacar la declaración (1) y colocar dentro de func1() la declaración static int x =1;

En ambos casos x se asigna en el segmento de datos y su tiempo de vida es esattico (toda la ejecucion del programa). La alocacion de memoria es la misma si hablamos de donde y como se guarda x
En cuanto al alcance en el original x es global, con la modificacion x es local a func1()

## Ejercicio 7

> Ejercicio 7: Sea el siguiente segmento de código escrito en Java, indique para los identificadores si son globales o locales.

```java
Clase Persona { 
	public long id 
	public string nombreApellido 
	public Domicilio domicilio 
	private string dni; 
	public string fechaNac; 
	public static int cantTotalPersonas;
	
	//Se tienen los getter y setter de cada una de las variables 
	
	//Este método calcula la edad de la persona a partir de la fecha de nacimiento
	public int getEdad(){ 
		public int edad=0; 
		public string fN = this.getFechaNac(); 
		... 
		... 
		return edad; 
	} 
} 
Clase Domicilio { 
	public long id; 
	public static int nro 
	public string calle 
	public Localidad loc; 
	
	//Se tienen los getter y setter de cada una de las variables }
```

| Identificadores Locales      | Identificadores Globales             |
| ---------------------------- | ------------------------------------ |
| public long id (Persona)     | public static int cantTotalPersonas; |
| public string nombreApellido | public static int nro                |
| public Domicilio domicilio   |                                      |
| private string dni           |                                      |
| public string fechaNac       |                                      |
| public long id (Domicilio)   |                                      |
| public string calle          |                                      |
| public Localidad loc         |                                      |

## Ejercicio 8

> Sea el siguiente ejercicio escrito en Pascal

```pascal
Program Uno;
type tpuntero = ^integer;
var mipuntero: tpuntero;
var i: integer;
var h: integer;
Begin
  i := 3;
  mipuntero := nil;
  new(mipuntero);
  mipuntero^ := i;
  h := mipuntero^ + i;
  dispose(mipuntero);
  write(h);
  i := h - mipuntero;
End.
```

> **a)** Indique el rango de instrucciones que representa el tiempo de vida de las variables i, h y mipuntero

| Identificador | Tiempo de Vida           |
| ------------- | ------------------------ |
| i             | 1 - 15                   |
| h             | 1- 15                    |
| miPuntero     | 1 - 15                   |
| miPuntero^    | 9 - 12 (river es locura) |
> **b)** Indique el rango de instrucciones que representa el alcance de las variables i, h y mipuntero.

| Identificador | Alcance |
| ------------- | ------- |
| i             | 5 - 15  |
| h             | 6- 15   |
| miPuntero     | 4 - 15  |
| miPuntero^    | 4 - 15  |
> **c)** Indique si el programa anterior presenta un error al intentar escribir el valor de h. Justifique

No, el programa no presenta error ya que si bien uso el valor de `miPuntero^`, fue antes del dipose y al ser de tipo entero solo uso el valor que el puntero contenia al momento del llamado.

> **d)** Indique si el programa anterior presenta un error al intentar asignar a i la resta de h con mipuntero. Justifique

Si, el error esta en que miPuntero tiene el valor `nil` despues del dispose, y no es una operacion valida hacer entero - nil.

> **e)** Determine si existe otra entidad que necesite ligar los atributos de alcance y tiempo de vida para justificar las respuestas anteriores. En ese caso indique cuál es la entidad y especifique su tiempo de vida y alcance.

Existe otra entidad, el programa principal, que su tiempo de vida y alcance van desde la linea 1 a la 15

> **f)** Especifique el tipo de variable de acuerdo a la ligadura con el l-valor de las variables que encontró en el ejercicio.

| Identificador | Tipo    | L-Value    |
| ------------- | ------- | ---------- |
| i             | Integer | automatico |
| h             | Integer | automatico |
| miPuntero     | Puntero | automatico |
| miPuntero^    | Integer | dinamico   |

## Ejercicio 9

> Elija un lenguaje y escriba un ejemplo:

> **a.** En el cual el tiempo de vida de un identificador sea mayor que su alcance
> **b.** En el cual el tiempo de vida de un identificador sea menor que su alcance
> **c.** En el cual el tiempo de vida de un identificador sea igual que su alcance

```c
 static int aux;
 int v2;
 static int fun2( ){ 
	 extern int v1;
	 aux=aux+1;
 }
 int fun3( ){ 
	 int aux;
	 aux=aux+1;
 }
```

| **Identificador** | **Lvalor** | **Rvalor** | **Alcance** | **T. vida** |
| ----------------- | ---------- | ---------- | ----------- | ----------- |
| aux               | estática   | 0-1        | 1-8 10->    | <1-10>      |
| v2                | automática | 0          | 2-10        | 1-10        |
| fun2              |            |            | 3-10        | 3 - 6       |
| v1                | automática | indef      | 4-6         | 3-6         |
| fun3              |            |            | 7-10        | 7 - 10      |
| aux               | automática | indef      | 8-10        | 7-10        |
Se puede ver en `v2` un tiempo de vida mayor que su alcance
Se puede ver en `fun2` un alcance mayor que su tiempo de vida
Se puede ver en `fun3` un alcance igual al tiempo de vida

## Ejercicio 10

> Si tengo la siguiente declaración al comienzo de un procedimiento:

- int c; **en C** 
- var c:integer; **en Pascal** 
- c: integer; **en ADA**

>Y ese procedimiento NO contiene definiciones de procedimientos internos. ¿Puedo asegurar que el alcance y el tiempo de vida de la variable “c” es siempre todo el procedimiento en donde se encuentra definida?. Analícelo y justifique la respuesta, para todos los casos

No se puede asegurar en C y ADA ya que se pueden usar las sentencias declare, en pasca esto no existe asi que si se agura ahil, el tiempo de vida si puede asegurarse en los 3

## Ejercicio 11

> **a.** Responda Verdadero o Falso para cada opción. El tipo de dato de una variable es? 

1. Un string de caracteres que se usa para referenciar a la variable y operaciones que se pueden realizar sobre ella. **==F==**
2.  Conjunto de valores que puede tomar y un rango de instrucciones en el que se conoce el nombre. **==F==**
3. Conjunto de valores que puede tomar y lugar de memoria asociado con la variable. **==F==**
4. Conjunto de valores que puede tomar y conjunto de operaciones que se pueden realizar sobre esos valores. **==V==**

> **b.** Escriba la definición correcta de tipo de dato de una variable.

Conjunto de valores que puede tomar y conjunto de operaciones que se pueden realizar sobre esos valores.

## Ejercicio 12

> Sea el siguiente programa en ADA, completar el cuadro siguiente indicando para cada variable de que tipo es en cuanto al momento de ligadura de su l-valor, su r-valor al momento de alocación en memoria y para todos los identificadores cuál es su alcance y cual es su el tiempo de vida. Indicar para cada variable su r-valor al momento de alocación en memoria

```ada
with text_io; use text_io;
Procedure Main is
    type vector is array(integer range <>);
    a, n, p: integer;
    v1: vector(1..100);
    c1: constant integer := 10;
    Procedure Uno is
        type puntero is access integer;
        v2: vector(0..n);
        c1, c2: character;
        p, q: puntero;
    begin
        n := 4;
        v2(n) := v2(1) + v1(5);
        p := new puntero;
        q := p;
        .......
        free p;
        ......
        free q;
        ......
    end;
begin
    n := 5;
    .....
    Uno;
    a := n + 2;
    .....
end;
```

| ID       | Tipo         | R-Value | Alcance | T.V.    |
| -------- | ------------ | ------- | ------- | ------- |
| main (2) | ---          | ---     | 3 - 29  | 2 - 29  |
| a (4)    | automatica   | basura  | 5 - 29  | 2 - 29  |
| n (4)    | automatica   | basura  | 5 - 29  | 2 - 29  |
| p (4)    | automatica   | basura  | 5 - 29  | 2 -29   |
| v1 (5)   | automatica   | basura  | 6 - 29  | 2 - 29  |
| c1 (6)   | automatica   | basura  | 7 - 29  | 2 - 29  |
| Uno (7)  | ---          | ---     | 8 - 29  | 7 - 22  |
| v2 (9)   | semidinamico | basura  | 10 - 22 | 7 - 22  |
| c1 (10)  | automatica   | basura  | 11 - 22 | 7 - 22  |
| c2 (10)  | automatica   | basura  | 11 - 22 | 7 -22   |
| p        | automatica   | nil     | 12 - 22 | 7 - 22  |
| q        | automatica   | nil     | 12 - 22 | 7 - 22  |
| p^       | dinamica     | basura  | 12 - 22 | 15 - 18 |
| q^       | dinamica     | basura  | 12 - 22 | 16 - 20 |
## Ejercicio 13

> El nombre de una variable puede condicionar: 
> 	**a)** Su tiempo de vida. 
> 	**b)** Su alcance. 
> 	**c)** Su r-valor. 
> 	**d)** Su tipo. 
> Justifique la respuesta

El nombre puede condicionar el alcance de una variable, ya que si se elige el nombre de una variable local de un proceso, en esa parte se va a enmascarar

## Ejercicio 14

>Sean los siguientes archivos en C, los cuales se compilan juntos 
>Indicar para cada variable de que tipo es en cuanto al momento de ligadura de su l-valor. 
>Indicar para cada identificador cuál es su alcance y cual es su el tiempo de vida. 
>Indicar para cada variable su r-valor al momento de alocación en memoria

```c
int v1;  // Aca empieza el archivo1.c
int *a;
int fun2() { 
    int v1, y;
    for(y = 0; y < 8; y++) { 
        extern int v2;
        ...}
}
main() {
    static int var3;
    extern int v2;
    int v1, y;
    for(y = 0; y < 10; y++) { 
        char var1 = 'C';
        a = &v1;}
}
static int aux; // Aca empieza el archivo2.c
int v2;
static int fun2() { 
    extern int v1;
    aux = aux + 1;
    ...
}
int fun3() { 
    int aux;
    aux = aux + 1;
    ...
}
```

| ID        | Tipo       | R-Value | Alcance                        | T.V.     |
| --------- | ---------- | ------- | ------------------------------ | -------- |
| v1 (1)    | automatica | 0       | 2 - 4 -> 9 - 13 -> 20 - 22 ->  | 1 - 28   |
| a (2)     | automatica | null    | 3 - 16                         | 1 - 28   |
| fun2 (3)  | ---        | ---     | 4 - 16                         | 3 - 8    |
| v1 (4)    | automatica | basura  | 5 - 8                          | 3 - 8    |
| y (4)     | automatica | basura  | 5 - 8                          | 3 - 8    |
| main (9)  | ---        | ---     | 10 - 16                        | 9 - 16   |
| var3 (10) | estatica   | 0       | 11 - 16                        | <1 - 28> |
| v1 (12)   | automatica | basura  | 13 - 16                        | 9 - 16   |
| y (12)    | automatica | basura  | 13 - 16                        | 9 - 16   |
| var1 (14) | automatica | basura  | 15                             | 9 - 16   |
| aux (17)  | estatica   | 0       | 18 - 25 -> 28 ->               | <1 - 28> |
| v2 (18)   | automatica | 0       | 7 -> 12 - 16 -> <br>19 - 28 -> | 1 - 28   |
| fun2 (19) | ---        | ---     | 20 - 28                        | 19 - 23  |
| fun3 (24) | ---        | ---     | 25 - 28                        | 24 - 28  |
| aux       | automatica | basura  | 26 - 28                        | 24 - 28  |
