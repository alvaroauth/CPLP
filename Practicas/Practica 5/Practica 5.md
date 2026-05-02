## Ejercicio 1

> Explique claramente cual es la utilidad del registro de activación y que representan cada una de sus partes.(Basado en el modelo debajo detallado)

La utilidad de un registro de activacion o frame es guardar el contexto (informacion necesaria) necesaria oara la ejecucion de una instancia particular de una rutina o subprograma

Se crea una nueva de estas cada vez que se llama a una rutina. El mismo contiene estos datos:
- **Variables locales:** Hay un espacio de memoria para variables locales y resultados temporales a evaluar
- **Parametros formales:** Almacenan parametros o argumentos recibidos de la rutina llamadora
- **Punto de retorno:** Guarda la direccion de la instruccion exacta donde debe volver el flujo de control una vez que termina la subrutina
- **Valor de retorno:** Si tiene que devolver un valor, lo guarda en un lugar para que sea recuperado por la rutina llamadora

A esto se le suman los enlaces estaticos y dinamicos
- **Enlace dinamico:** Es un puntero que dirige al regidtro de activacion de la rutina llamadora (caller), por ejemplo en una recursion estaria apuntando a la instancia de la recursion que me llamo
- **Enlace estatico:** Es un puntero que dirige al bloque que contiene estaticamente al subprograma. es decir que miro el codigo y veo donde esta contenido, mas alla de quien me llamo

## Ejercicio 2

> Dado el siguiente programa escrito en Pascal-like, continuar la realización de las pilas de ejecución hasta finalizar las mismas.
> 	**a)** Siguiendo la cadena estática 
> 	**b)** Siguiendo la cadena dinámica

```pascal
Program Main 
	Var a: array[1..10] of integer; 
		x,y,z:integer 
Procedure A () 
	var y,t: integer; 
	begin 
		a(1):= a(1)+1;z:=z+1; 
		t:=1; y:=2; 
		B(); a(y):=a(y)+3; y:=y+1; 
		If z=11 Then Begin 
			a(z-1):=a(z-2) + 3; 
			z:=z-4; 
			a(z-y):=a(z) – a(y) + 5; 
		End; 
	end; 
Function t():integer 
	begin 
	y:=y+1; z:=z-6;
	return(y+x); 
	end;
Procedure B() 
	var d:integer; 
	Procedure I () 
	begin 
		x:=0; x:=x+6; 
	end; 
	begin 
		x:=x+t; d:=0;
		while x>d do begin 
			I(); x:=x-1; d:=d + 2; 
		end; 
	end; 
begin 
	For x:=1 To 10 do a(x):=x; 
	x:=5; y:=1; z:=10;
	A(); 
	For x:=1 To 10 do write(a(x),x); 
end.
```

|     | Siguiendo la cadena estática |     | Siguiendo la cadena dinámica |
| :-- | :--------------------------- | :-- | :--------------------------- |
|     | *** Reg Activ Main           |     | *** Reg Activ Main           |
| *1  | Pto retorno                  | *1  | Pto retorno                  |
|     | A(1)= 1                      |     | A(1)= ~~1~~, ~~2~~, 5        |
|     | A(2)= 2                      |     | A(2)= 2                      |
|     | A(3)= 3                      |     | A(3)= 3                      |
|     | A(4)= 4                      |     | A(4)= 4                      |
|     | A(5)= 5                      |     | A(5)= 5                      |
|     | A(6)= 6                      |     | A(6)= 6                      |
|     | A(7)= 7                      |     | A(7)= 7                      |
|     | A(8)= 8                      |     | A(8)= 8                      |
|     | A(9)= 9                      |     | A(9)= 9                      |
|     | A(10)= 10                    |     | A(10)= 10                    |
|     | X= ~~1~~, ~~10~~, 5          |     | X= ~~1~~, ~~10~~, 5          |
|     | Y= ~~1~~ - 2                 |     | Y= ~~1~~ - 2                 |
|     | Z= ~~10~~ - ~~11~~ - 5       |     | Z= ~~10~~ - 11               |
|     | Procedure A                  |     | Procedure A                  |
|     | Function T                   |     | Function T                   |
|     | Procedure B                  |     | Procedure B                  |
|     | VR . . . . . . . .           |     | VR . . . . . . . .           |
| *2  | ***Reg Activ A               | *2  | ***Reg Activ A               |
|     | Pto Retorno                  |     | Pto Retorno                  |
|     | EE (*1)                      |     | EE (*1)                      |
|     | ED (*1)                      |     | ED (*1)                      |
|     | Y = 2                        |     | Y = 2                        |
|     | T = 1                        |     | T = 1                        |
|     | VR . . . . . . . .           |     | VR . . . . . . . .           |
|     | *** Reg Activ B              | *3  | *** Reg Activ B              |
|     | Pto Retorno                  |     | Pto Retorno                  |
|     | EE                           |     | EE (*1)                      |
|     | ED                           |     | ED (*2)                      |
|     | D =                          |     | D =                          |
|     | Procedure I                  |     | Procedure I                  |
|     | VR . . ¿? . .                |     | VR . . ¿? . .                |
|     | *** Reg Activ...(a partir de | *4  | *** Reg Activ...(a partir de |
|     | acá lo debe continuar...     |     | acá lo debe continuar...     |
|     | ........................     |     | ........................     |
