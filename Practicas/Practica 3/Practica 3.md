## Ejercicio 1

>¿Qué define la semántica?

La semantica de un lenguaje de programacion es el conjunto de reglas que se encarga de describir el significado exacto de los simbolos, palabras, expresiones y unidades

## Ejercicio 2

> a) ¿Qué significa compilar un programa?

Compilar significa traducir por completo el codigo fuente (escrito por el programador) a un lenguaje mas bajo nivel (como lenguaje de maquina) antes de que sea ejecutado.

> b) Describa brevemente cada uno de los pasos necesarios para compilar un programa.

1. **Etapa de analisis:** 
	1. **Analisis lexico:** Lee los caracteres del codigo y losa grupa en palanras clave o tokens.
	2. **Analisis sintactico:** Revisa que los tokens formen oraciones estructuralmente validas segun las reglas del lenguaje
	3. **Analisis semantico:** Verifica que el codigo tenga significado logico, controlando los tipos de datos y declaraciones
2. **Etapa de sintesis:**
	1. **Generacion de codigo intermedio:** Traduce el programa a una versiona bstracta que no depende de ningun hardware
	2. **Optimizacion (opcional):** Mejora el programa para que se ejecute mas rapido o use menos memoria
	3. **Generacion de codigo objeto:** Traduce finalmente el programa a instrucciones de lenguaje de maquina (ceros y unos)
3. **Armado final**
	1. **Enlazador:** Junta todos los pedazos de codigo objeto y bibliotecas externas para crear un solo archivo ejecutable
	2. **Cargador:** Sube el programa ejecutable a memoria para iniciar su ejecucion

> c) ¿En qué paso interviene la semántica y cual es su importancia dentro de la compilación?

La semantica interviene en la **etapa del analisis**, despues del analisis lexico y sintactico. SU importancia se basa en atrapar errores logicos, gestioanr la tabla de simbolos (identificadores, tipo de dato y alcance) y preparar la traduccion. 

## Ejercicio 3

> Con respecto al punto anterior ¿es lo mismo compilar un programa que interpretarlo? Justifique su respuesta mostrando las diferencias básicas, ventajas y desventajas de cada uno.

**Compilacion (traduce TODO el programa antes de ejecutar)**
- **Ventajas:** La ejecucion es mas rapida y eficiente. Detecta muchos errores antes de correr el programa y genera un .exe independiente
- **Desventajas:** Es mas dificil rastrear la linea exacta del error si falla en ejecucion. Tiene baja portabilidad (Se compila por cada sistema operativo o arquictectura distinta)
**Interpretacion (traduce y ejecuta LINEA POR LINEA en tiempo real)**
- **Ventajas:** Excelente para encontrar y corregir errores. Es muy portable porque el mismo codigo funciona para cualquier maquina con el interprete instalado
- **Desventajas:** La ejecucion es mucho mas lenta(de 10 a 100 veces mas lenta). Ademas requiere que siempre tengas a mano el codigo fuente y el interprete

## Ejercicio 4

> Explique claramente la diferencia entre un error sintáctico y uno semántico. Ejemplifique
   cada caso.

La principal diferencia esta en si es un fallo en la forma (sintacticto) o un fallo en la logica (semantico)
- **Error en la forma:** La instruccion es mal escrita estructuralmente. El traductor del lenguaje ni siquiera reconoce la instruccion porque no se respetaron las reglas basicas del lenguaje
	- **Ejemplos:** Olvidarse de cerrar un parentesis, olvidarse un ;, usar un operador de asignacion incorrecto (ejemplo en java poner int e := 1), etc.
- **Error en la logica:** La oracion esta estructuralmente perfecta pero lo que estas pidiendo es irracional, inconsistente o imposible. Hay restricciones que la sintaxis no puede detectar porque carece de contexto
	- **Ejemplo:** Intentar hacer resul = (int)num + (string)str, usar una variable no declarada antes, declarar dos varialbes con el mismo nombre, etc.

## Ejercicio 5

> Sean los siguientes ejemplos de programas. Analice y diga qué tipo de error se produce (Semántico o Sintáctico) y en qué momento se detectan dichos errores (Compilación o Ejecución). Aclaración: Los valores de la ayuda pueden ser mayores.

>**a). Pascal**
```pascal
Program P
var 5: integer; 
var a:char; 
Begin 
	for i:=5 to 10 do begin 
		write(a); 
		a=a+1; 
	end; 
End
```
>Ayuda: Sintáctico 2, Semántico 3

**Errores sintacticos:**
- Falta un ; en program
- la variable "5" esta mal porque deberia empezar con algo distinto de un digito
- la asignacion a=a+1 esta mal porque es a:=a+1
- Falta un . en el End
**Errores semanticos:**
- var esta escrito dos veces
- se quiere sumarle 1 a un caracter
- la variable i no esta declarada
- la variable a se quiere usar sin estar inicializada

> **b). Java**
```java
public String tabla(int numero, arrayList<Boolean> listado) {
	String result = null;
	for(i = 1; i < 11; i--) {
		 result += numero + "x" + i + "=" + (i*numero) + "\n";
		 listado.get(listado.size()-1)=(BOOLEAN) numero>i; 
	} 
	return true; 
}
```
> Ayuda: Sintácticos 4, Semánticos 3, Lógico 1

**Errores sintacticos:**
* ArrayList se escribe con mayuscula en la A
* BOOLEAN se escribe Boolean
* listado.get() devuelve un elemtno, no se le puede asignar algo
* 
**Errores semanticos:**
- Variable i no declarada
- Retorna true cuando el valor de retorno es String
- Hace += sobre un string inicializado en null
- 
**Errores logicos:**
- Bucle infinito en el for
>**c) C**
```C
# include <stdio.h>
int suma; /* Esta es una variable global */
int main() { 
	int indice; 
	encabezado; 
	for (indice = 1 ; indice <= 7 ; indice ++) 
		cuadrado (indice); 
	final(); Llama a la función final */ 
	return 0; 
}
cuadrado (numero) 
int numero; 
{ 
	int numero_cuadrado; 
	numero_cuadrado == numero * numero; 
suma += numero_cuadrado; 
	printf("El cuadrado de %d es %d\n",
	 numero, numero_cuadrado); 
}
```
>Ayuda: Sintácticos 2, Semánticos 6

**Errores sintacticos:**
* `encabezado` no tiene un tipo definido
* El comentario `Llama a la función final */` no abre con `/*`
**Errores semanticos:**
- `final();` nunca es declarada como funcion (estatico)
- `cuadrado(numero)` no tiene tipo de retorno y declara el parametro mas abajo (estatico)
- `numero_cuadrado == numero * numero;`, el `*` no es un operador logico
- `numero_cuadrado == numero * numero;`, `numero` no tiene un valor inicial
- `suma += numero_cuadrado;` numero cuadrado no tiene valor

>**d) Python**
```python
#!/usr/bin/python 
print "\nDEFINICION DE NUMEROS PRIMOS" 
r = 1 
while r = True: 
    N = input("\nDame el numero a analizar: ") 
    i = 3 
    fact = 0 
    if (N mod 2 == 0) and (N != 2): 
        print "\nEl numero %d NO es primo\n" % N 
    else: 
        while i <= (N^0.5): 
            if (N % i) == 0: 
                mensaje="\nEl numero ingresado NO es primo\n" % N 
                msg = mensaje[4:6] 
                print msg 
                fact = 1 
            i+=2 
        if fact == 0: 
            print "\nEl numero %d SI es primo\n" % N 
    r = input("Consultar otro número? SI (1) o NO (0)--->> ")
```
> **Ayuda:** Sintácticos 2, Semánticos 3

**Errores sintacticos:**
- A `print` le faltan los parentesis
- en `while r = true:` usa un solo `=` cuando deberia ser `==`.
**Errores semanticos:**
- `mod` no es un operador de python (estatico)
- El `^` no significa potencia, se usa `**`. (estatico)
- El input retorna string, y se usa como numero (runtime).
- Se usa `% N` sin que haya un `%d` en el string

>**e) Ruby**
```ruby
def ej1
	Puts 'Hola, ¿Cuál es tu nombre?'
	nom = gets.chomp
	puts 'Mi nombre es ', + nom
	puts 'Mi sobrenombre es 'Juan''
	puts 'Tengo 10 años'
	meses = edad*12
	dias = 'meses' *30
	hs= 'dias * 24'
	puts 'Eso es: meses + ' meses o ' + dias + ' días o ' + hs + ' horas'
	puts 'vos cuántos años tenés'
	edad2 = gets.chomp
	edad = edad + edad2.to_i
	puts 'entre ambos tenemos ' + edad + ' años'
	puts '¿Sabes que hay ' + name.length.to_s + ' caracteres en tu nombre, ' + name + '?'
end
```
> **Ayuda:** Semanticos +4

**Errores sintacticos:**
- Puts con mayuscula
- Mal uso de comillas en `puts 'Mi sobrenombre es 'Juan''`.
- Mal uso de comiilas en `'Eso es: meses + ' meses o ' + dias + ' días o ' + hs + ' horas'`
**Errores semanticos:**
- `edad` se usa sin estar definida
- `meses` es un string en `dias = 'meses' *30`.
- `hs = 'dias * 24'` es un string literal
- `puts 'entre ambos tenemos ' + edad + ' años'` no parsea el int a string
- `name.length.to_s` usa name en lugar de nom, name no declarada
## Ejercicio 6

> Explique cuál es la semántica para las variables predefinidas en lenguaje Ruby self y nil. ¿Qué valor toman; cómo son usadas por el lenguaje?
##### Self
Es una **pseudovariable** que un objeto usa para hacer referencia a si mismo
Toma el valor de la instancia especifica de un objeto
Se usa principalmente para que un objeto invoque sus propios metodos o para enviar alertas de error sobre su propio estado 
##### Nil
Es una direccion de un puntero que no representa una direccion de memoria valida
Se usa para aclarar que un puntero no tiene una direccion de memoria asignada. Se suele usar como valor inicial o por defecto en los punteros 
## Ejercicio 7

> Determine la semántica de null y undefined para valores en javascript.¿Qué diferencia hay entre ellos?
##### Undefined
Este valor se utiliza en JavaScript cuando se intenta acceder a una propiedad de un objeto que no existe. Se usa para indicar que una variable existe pero no tiene valor.
##### Null
Es un valor especial que indica de forma explicita que no apunta a ningun objeto ni a ninguna dir. de memoria valida.
La diferencia es que undefined representa una ausencia implicita o por defecto, null representa una ausencia explicita e intencional.

## Ejercicio 8
