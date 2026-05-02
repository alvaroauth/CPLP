### Ejercicio 1

>Los lenguajes de programación más representativos son:
>- 1951 - 1955: Lenguajes tipo assembly
>- 1956 - 1960: FORTRAN, ALGOL 58, ALGOL 60, LISP
>- 1961 - 1965: COBOL, ALGOL 60, SNOBOL, JOVIAL
>- 1966 - 1970: APL, FORTRAN 66, BASIC, PL/I, SIMULA 67, ALGOL-W
>- 1971 - 1975: Pascal, C, Scheme, Prolog
>- 1976 - 1980: Smalltalk, Ada, FORTRAN 77, ML
>- 1981 - 1985: Smalltalk 80, Turbo Pascal, Postscript
>- 1986 - 1990: FORTRAN 90, C++, SML
>- 1991 - 1995: TCL, PERL, HTML
>- 1996 - 2000: Java, Javascript, XML
>Indique para cada uno de los períodos presentados cuales son las características nuevas que se incorporan y cual de ellos la incorpora.

- **1951 - 1955:** El lenguaje **Assembly** introduce el uso de mnemónicos. Esto permitió a los programadores dejar de escribir directamente en código máquina (secuencias de ceros y unos) y utilizar instrucciones más comprensibles que abstraen las operaciones del procesador.
- **1956 - 1960:** **FORTRAN** incorpora el primer compilador de alto nivel optimizado para el cálculo científico. Por su parte, **LISP** introduce la programación funcional y la recolección automática de memoria (garbage collection), mientras que **ALGOL 60** sienta las bases de la programación estructurada mediante el uso de bloques.
- **1961 - 1965:** **COBOL** se destaca por incorporar una sintaxis muy cercana al idioma inglés. Su principal innovación es facilitar el procesamiento de registros y archivos de datos en el ámbito comercial y empresarial.
- **1966 - 1970:** **SIMULA 67** marca un hito al introducir por primera vez los conceptos centrales de la Programación Orientada a Objetos (clases y objetos). Además, **BASIC** surge con el objetivo de hacer accesible la programación interactiva a estudiantes de diversas disciplinas no técnicas.
- **1971 - 1975:** **C** logra combinar la abstracción de los lenguajes de alto nivel con el control del hardware a bajo nivel, siendo una pieza clave para el desarrollo de sistemas operativos. **Prolog** introduce el paradigma de programación lógica, y **Pascal** implementa un tipado de datos estricto para fomentar buenas prácticas educativas.
- **1976 - 1980:** **Ada** incorpora herramientas avanzadas para la programación concurrente y el manejo de tiempo real, enfocándose en el desarrollo seguro de sistemas críticos e industriales.
- **1981 - 1985:** **Smalltalk 80** consolida la Programación Orientada a Objetos pura, integrándola con un entorno de desarrollo gráfico pionero. A su vez, **Turbo Pascal** revoluciona el mercado al ofrecer el primer Entorno de Desarrollo Integrado (IDE) de uso masivo, unificando el editor y el compilador.
- **1986 - 1990:** **C++** incorpora las características de la orientación a objetos al lenguaje C, logrando una herramienta de alto rendimiento y gran flexibilidad para proyectos complejos.
- **1991 - 1995:** **HTML** establece el estándar para el marcado y la estructuración de documentos, dando forma a la Web. En paralelo, **PERL** se consolida como un lenguaje fundamental para la automatización de tareas y el procesamiento avanzado de textos mediante expresiones regulares.
- **1996 - 2000:** **Java** introduce el concepto de portabilidad universal a través de su Máquina Virtual (JVM), permitiendo ejecutar el mismo código en distintas plataformas. Finalmente, **Javascript** incorpora la capacidad de procesar lógica en el lado del cliente, aportando dinamismo e interactividad directamente en los navegadores web.

### Ejercicio 2

>Escriba brevemente la historia del lenguaje de programación que eligió en la encuesta u otro de su preferencia.

Python fue desarrollado a fines de la decada de 1980 por el programador **Guido van Rossum**. Su primera version fue lanzada en **1991** en Centrum Wiskunde & Informatica - CWI.
El lenguaje experimento grandes avances en el desarrollo de codigo abierto, utilizando PEPs (”Propuestas de Mejora de Python”) como principal herramienta de mejora y discusiones dentro la comunidad.
Hoy en dia Python es uno de los lenguajes que crece mas rapidamente en relevancia y es valorado por su **agilidad, practicidad y versatilidad** en proyectos complejos.

### Ejercicio 3

>¿Qué atributos debería tener un buen lenguaje de programación? Por ejemplo, ortogonalidad, expresividad, legibilidad, simplicidad, etc. De al menos un ejemplo de un lenguaje que cumple con las características citadas.  

**Atributos**
**Simplicidad y legibilidad (incluye Expresividad):** Es fácil de aprender, leer y programar rapido.
**Ortogonalidad:** Sus piezas se pueden combinar libremente y siempre tienen sentido, sin encontrarte con restricciones ilógicas o contradicciones.
Confiabilidad:** Es un lenguaje seguro que detecta errores rápido y los ataja para que el programa no se rompa (excepciones).
**Abstracción:** Te deja ocultar tareas muy complejas dentro de bloques simples (como módulos o clases) sin preocuparte por el detalle interno.
**Claridad en los bindings:** Sabés perfectamente y sin confusiones a qué dato está apuntando una variable en cada momento.
**Soporte:** Viene con buenas herramientas extras (compiladores, librerías, buena documentación).
**Eficiencia:** El programa final consume poca memoria y procesador.
**Ejemplos:**
- **Python:** Es muy destacado por ser **simple, legible y confiable** gracias a su manejo de errores.
- **Ruby:** El mejor ejemplo de **ortogonalidad**: como casi todo en el lenguaje es un objeto y toda instrucción es una expresión, podés combinar código libremente casi sin limitaciones.

### Ejercicio 4

>Tome uno o dos lenguajes de los que ud. Conozca y
>-Describa los tipos de expresiones que se pueden escribir en él/ellos
>- Describa las facilidades provistas para la organización del programa
>- Indique cuáles de los atributos del ejercicio anterior posee el/los lenguaje/s elegidos y cuáles no posee, justifique en cada caso.

Lenguajes - ADA

**Lenguaje: Python**
**Expresiones:** Utiliza tipado dinámico. Permite expresiones aritméticas, lógicas (con evaluación de cortocircuito mediante `and` y `or`) y relacionales. Se destacan las comprensiones de listas (_list comprehensions_) para generar colecciones de forma muy compacta, y el uso de funciones anónimas (expresiones `lambda`).
**Organización:** Se estructura en **módulos** (archivos `.py`) y **paquetes** (directorios que agrupan módulos). Al ser multiparadigma, permite organizar el código tanto en funciones independientes (estructurado) como en clases (orientado a objetos).
**Atributos:**
- **Legibilidad (Sí):** Su diseño obliga a utilizar indentación para definir los bloques de código, garantizando un formato visualmente limpio y muy fácil de seguir para cualquier programador.
- **Escribibilidad (Sí):** Es un lenguaje sumamente ágil. Su sintaxis minimalista permite desarrollar prototipos o resolver problemas complejos escribiendo muy pocas líneas de código.
- **Confiabilidad estricta (No):** Al ser interpretado y de tipado dinámico, muchos errores (como incompatibilidad de tipos de datos) recién se detectan en tiempo de ejecución, lo que lo hace menos seguro que los lenguajes compilados para sistemas críticos.

### Ejercicio 5

>Describa las características más relevantes de Ada, referida a:
>- Tipos de datos
>- Tipos abstractos de datos – paquetes
>- Estructuras de datos
>- Manejo de excepciones
>- Manejo de concurrencia


**Características relevantes de Ada:**
- **Tipos de datos:** Tipado estático muy fuerte. Permite definir **subtipos** con rangos estrictos (ej. del 1 al 10); el sistema verifica estos límites al ejecutarse para prevenir fallas.

- **Tipos abstractos (Paquetes):** Se manejan mediante **paquetes** que separan la interfaz pública de la implementación interna. Usando el modificador `private`, se logra un encapsulamiento total de la información.

- **Estructuras de datos:** Soporta arreglos y **registros** (que pueden cambiar su forma o tamaño según sea necesario). Utiliza "tipos de acceso" en lugar de punteros tradicionales para proteger la memoria.

- **Manejo de excepciones:** Sistema nativo mediante bloques de código. Atrapa errores automáticamente (como el desbordamiento de un arreglo) y permite definir excepciones propias, propagándolas si no se resuelven localmente.

- **Manejo de concurrencia:** Tiene soporte integrado a través de **tareas** (_tasks_). Estas se sincronizan de forma segura utilizando **Rendezvous** (puntos de encuentro) y objetos protegidos para evitar conflictos al modificar datos.