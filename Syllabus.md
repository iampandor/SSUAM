# Syllabus
## 120 temas de 10 mins
###	Java/Spring boot
#### Estructuras de datos
1. Importancia de las ED
1. Arreglos
1. Listas
1. Conjuntos
1. Hash
1. Montículos
#### Java
7. ¿Por qué?
   Java es uno de los lenguajes de programación más influyentes y utilizados en el mundo del desarrollo de software. Su importancia radica en varios factores clave que lo han convertido en una elección popular tanto para principiantes como para desarrolladores experimentados.

En primer lugar, Java es un lenguaje versátil que se puede utilizar en una amplia variedad de aplicaciones. Se utiliza en el desarrollo de aplicaciones móviles, aplicaciones web, sistemas embebidos, aplicaciones de escritorio y mucho más. Su capacidad para adaptarse a diferentes plataformas y entornos lo hace invaluable en el mundo de la programación.

Java es también conocido por su portabilidad. El lema "Write Once, Run Anywhere" (Escribe una vez, ejecuta en cualquier lugar) se ha convertido en una de las características distintivas de Java. Esto significa que un programa Java escrito en una plataforma puede ejecutarse en prácticamente cualquier otra plataforma que tenga una máquina virtual Java (JVM) compatible. Esta portabilidad ha allanado el camino para el desarrollo de aplicaciones multiplataforma que funcionan en diferentes sistemas operativos sin necesidad de modificaciones significativas.

Además de su portabilidad, Java es altamente seguro. La seguridad es una preocupación importante en el mundo digital actual, y Java ha sido diseñado con características de seguridad robustas desde su inicio. El sistema de seguridad de Java incluye la verificación de código, la gestión de permisos y la capacidad de aislar y restringir el acceso a recursos del sistema. Esto hace que Java sea una opción popular para el desarrollo de aplicaciones críticas en términos de seguridad, como aplicaciones bancarias y sistemas de gestión de datos confidenciales.

Java también es conocido por su amplia comunidad de desarrolladores y su rico ecosistema de bibliotecas y marcos de trabajo. Esto facilita el desarrollo rápido de aplicaciones, ya que los desarrolladores pueden aprovechar las soluciones preexistentes para abordar problemas comunes. La comunidad de Java es activa y participativa, lo que significa que siempre hay recursos disponibles para ayudar a los desarrolladores a resolver problemas y aprender nuevas técnicas.

En resumen, Java es importante en la programación debido a su versatilidad, portabilidad, seguridad y comunidad activa. Estas características lo convierten en una elección sólida para una amplia variedad de aplicaciones y proyectos de desarrollo de software.

7. Objetos/Clases
   Los objetos y las clases son conceptos fundamentales en Java y en la programación orientada a objetos en general. En Java, todo es un objeto o se basa en objetos. Este enfoque es esencial para la organización y estructura de los programas Java.

En Java, una clase es una plantilla o un plano para crear objetos. Define los atributos (variables) y métodos (funciones) que un objeto de esa clase tendrá. Por ejemplo, si estuviéramos creando una aplicación de gestión de estudiantes, podríamos tener una clase llamada "Estudiante" con atributos como nombre, edad y número de identificación, y métodos como "registrar" y "calcularPromedio".

Los objetos son instancias concretas de una clase. Usando la clase "Estudiante" como ejemplo, podríamos crear objetos individuales para cada estudiante, como "estudiante1" y "estudiante2". Cada objeto tiene sus propios valores de atributos y puede realizar sus propias operaciones a través de los métodos definidos en su clase.

El uso de objetos y clases en Java permite la encapsulación, que es uno de los principios clave de la programación orientada a objetos. La encapsulación significa que los datos (atributos) y el comportamiento (métodos) están agrupados en un solo objeto, y el acceso a estos elementos se controla mediante modificadores de acceso como público, privado o protegido. Esto promueve la modularidad y la organización, lo que facilita la comprensión y el mantenimiento del código.

La herencia es otro concepto importante en Java relacionado con las clases. Permite la creación de clases derivadas (subclases) basadas en una clase existente (superclase). Las subclases heredan los atributos y métodos de la superclase, lo que facilita la reutilización del código y la creación de jerarquías de clases.

El polimorfismo es un tercer concepto relevante en Java. Significa que objetos de diferentes clases pueden responder a un mismo mensaje de manera diferente. Esto se logra mediante la implementación de métodos con el mismo nombre pero comportamientos diferentes en diferentes clases. El polimorfismo permite escribir código genérico que puede trabajar con objetos de diferentes tipos, lo que mejora la flexibilidad y la extensibilidad de las aplicaciones.

En resumen, los objetos y las clases son fundamentales en Java y en la programación orientada a objetos. Estos conceptos permiten la encapsulación, la herencia y el polimorfismo, que son pilares esenciales en la creación de aplicaciones Java estructuradas y mantenibles
7. Funciones lambda 
  Las funciones lambda son una característica importante introducida en Java 8. Permiten tratar las funciones como objetos de primera clase, lo que mejora la legibilidad y la concisión del código. Las funciones lambda son especialmente útiles en programación funcional y en la manipulación de colecciones de datos.

Una función lambda en Java es una función anónima que se puede utilizar como argumento en métodos o asignar a variables. Se componen de parámetros, una flecha (->) y una expresión que representa el cuerpo de la función. Aquí hay un ejemplo sencillo:

java
```
(Parámetros) -> Expresión
```
Por ejemplo, podríamos utilizar una función lambda para ordenar una lista de números en orden ascendente:

java
```
List<Integer> numeros = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5);
numeros.sort((a, b) -> a.compareTo(b));
```

En este ejemplo, la función lambda (a, b) -> a.compareTo(b) se utiliza como argumento en el método sort de la lista numeros. La función lambda toma dos parámetros a y b y devuelve el resultado de llamar al método compareTo, que se utiliza para comparar los elementos de la lista.

Las funciones lambda son especialmente útiles cuando se trabaja con las API de transmisión (Stream API) de Java. La Stream API permite operaciones de alto nivel en colecciones de datos, como filtrar, mapear y reducir elementos. Las funciones lambda se integran perfectamente con la Stream API, lo que permite escribir código más conciso y legible para manipular datos.

Por ejemplo, supongamos que tenemos una lista de personas y queremos filtrar solo aquellas que sean mayores de 18 años y luego imprimir sus nombres:

java

```
List<Persona> personas = obtenerListaDePersonas();
personas.stream()
    .filter(p -> p.getEdad() > 18)
    .forEach(p -> System.out.println(p.getNombre()));
```
En este código, utilizamos la función lambda (p -> p.getEdad() > 18) como argumento para el método filter, que filtra las personas mayores de 18 años. Luego, usamos otra función lambda (p -> System.out.println(p.getNombre())) para imprimir el nombre de cada persona que cumple con el filtro.

Las funciones lambda no solo hacen que el código sea más conciso, sino que también mejoran la legibilidad al enfocarse en la lógica específica que se está aplicando a los datos. Esto hace que el código sea más fácil de entender y mantener.

Además, las funciones lambda en Java son compatibles con la inferencia de tipos, lo que significa que no es necesario especificar explícitamente el tipo de parámetros en muchas situaciones. Java puede deducir automáticamente los tipos de parámetros, lo que reduce aún más la verbosidad del código.

En resumen, las funciones lambda son una característica poderosa y versátil en Java que permite el tratamiento de funciones como objetos de primera clase. Facilitan la escritura de código conciso y legible, especialmente cuando se trabaja con la Stream API, y mejoran la modularidad y la expresividad del código.
7. Colectiones 
  Las colecciones en Java son estructuras de datos que permiten almacenar y manipular conjuntos de elementos de manera eficiente. Java proporciona una amplia variedad de clases de colección en su biblioteca estándar, lo que facilita la gestión y el acceso a datos en aplicaciones.

Las colecciones se dividen en dos categorías principales en Java: colecciones y mapas.

Colecciones: Las colecciones almacenan elementos como listas, conjuntos y colas. Algunos tipos comunes de colecciones en Java incluyen:
ArrayList: Una lista dinámica que puede cambiar de tamaño automáticamente.
LinkedList: Una lista enlazada que permite la inserción y eliminación eficiente de elementos en cualquier posición.
HashSet: Un conjunto que no permite duplicados y no garantiza un orden específico.
TreeSet: Un conjunto ordenado basado en un árbol binario de búsqueda.
Queue: Una interfaz que representa una cola de elementos, donde se sigue el principio "primero en entrar, primero en salir" (FIFO).
Mapas: Los mapas almacenan pares clave-valor, donde cada clave está asociada a un valor. Algunos tipos comunes de mapas en Java incluyen:
HashMap: Un mapa que no garantiza un orden específico y permite un acceso rápido mediante claves.
TreeMap: Un mapa ordenado basado en un árbol binario de búsqueda.
LinkedHashMap: Un mapa que mantiene el orden de inserción de las claves.
Hashtable: Una versión antigua y sincronizada de un mapa en Java.
ConcurrentHashMap: Un mapa diseñado para la concurrencia que permite múltiples operaciones de lectura y escritura concurrentes.
El uso adecuado de colecciones es esencial para el desarrollo de aplicaciones Java eficientes y limpias. Las colecciones proporcionan métodos y operaciones convenientes para agregar, eliminar, buscar y manipular elementos de datos.

Además de las clases de colección básicas, Java también ofrece interfaces de colección que permiten la programación orientada a interfaces. Esto significa que puedes escribir código que dependa de interfaces como List, Set o Map, en lugar de clases concretas. Esto promueve la flexibilidad y la extensibilidad del código, ya que puedes cambiar la implementación subyacente sin modificar el código cliente.

En resumen, las colecciones en Java son estructuras de datos esenciales que facilitan la gestión de datos en aplicaciones. Java proporciona una variedad de clases de colección y mapas en su biblioteca estándar, lo que permite a los desarrolladores elegir la estructura de datos más adecuada para sus necesidades.
7. Stream 
  La API de Streams en Java es una característica poderosa introducida en Java 8 que simplifica el procesamiento de secuencias de datos de manera declarativa y funcional. Streams permite a los desarrolladores realizar operaciones de procesamiento de datos en colecciones de manera más eficiente y concisa.

Un Stream en Java representa una secuencia de elementos que pueden ser procesados en paralelo o secuencialmente. Puedes pensar en un Stream como una tubería que lleva elementos de una colección y permite aplicar operaciones de transformación, filtrado, mapeo y reducción a esos elementos de manera fácil y efectiva.

Aquí hay un ejemplo simple de cómo trabajar con Streams en Java:

java
```
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

int sumaDeCuadrados = numeros.stream()
    .filter(n -> n % 2 == 0)  // Filtrar números pares
    .map(n -> n * n)          // Elevar al cuadrado
    .reduce(0, Integer::sum);  // Sumar todos los cuadrados

System.out.println("La suma de los cuadrados de los números pares es: " + sumaDeCuadrados);
```
En este ejemplo, creamos un Stream a partir de una lista de números, filtramos los números pares, elevamos al cuadrado cada número y luego sumamos los cuadrados resultantes. Todo esto se hace de manera declarativa y funcional en una sola línea de código.

Las operaciones de Streams se dividen en dos categorías: operaciones intermedias y operaciones terminales. Las operaciones intermedias incluyen filter, map, flatMap, distinct, sorted, peek y otras que transforman o filtran los elementos del Stream. Las operaciones terminales, como collect, forEach, reduce y count, cierran el Stream y producen un resultado o efecto final.

Una de las ventajas clave de usar Streams es su capacidad para paralelizar automáticamente el procesamiento de datos cuando es apropiado. Esto significa que puedes obtener un rendimiento significativamente mejorado al aprovechar los múltiples núcleos de CPU en sistemas multiprocesador. La API de Streams maneja la concurrencia internamente, lo que facilita la escritura de código paralelo sin la necesidad de manejar directamente los hilos (threads) en la mayoría de los casos.

Además de la eficiencia, las Streams promueven un código más limpio y legible. La programación funcional y declarativa fomenta la escritura de código más claro y conciso, lo que facilita la comprensión y el mantenimiento del mismo. Esto se traduce en una mayor productividad y menos errores.

Otra ventaja de las Streams es su capacidad para trabajar con grandes conjuntos de datos sin necesidad de cargar todo el conjunto en memoria. Esto es especialmente útil cuando se trabaja con datos de transmisión, ya que se pueden procesar elementos uno a uno o en pequeños bloques sin agotar la memoria.

En resumen, la API de Streams en Java es una característica poderosa que facilita el procesamiento de secuencias de datos de manera eficiente, concisa y legible. Permite realizar operaciones de procesamiento de datos en paralelo de manera automática y se integra perfectamente con las colecciones en Java.
7. Versiones de java 
  Java ha evolucionado significativamente desde su primera versión. Cada nueva versión ha introducido características y mejoras que han enriquecido el lenguaje y su ecosistema. A continuación, se presentan algunas de las versiones clave de Java y las características que introdujeron:

Java 1.0 (1996): La primera versión oficial de Java introdujo los conceptos fundamentales del lenguaje, como clases, objetos, excepciones y la máquina virtual Java (JVM).
Java 1.1 (1997): Esta versión agregó la API de colecciones y la biblioteca de eventos AWT (Abstract Window Toolkit), lo que mejoró la capacidad de desarrollo de interfaces gráficas de usuario.
Java 1.2 (Java 2 Platform, Standard Edition 1.2, 1998): Esta versión trajo consigo el Swing GUI Toolkit, que reemplazó a AWT y mejoró significativamente la creación de interfaces de usuario. También introdujo la API de colecciones con las clases ArrayList, HashMap, entre otras.
Java 5 (2004): Java 5 fue un hito importante que introdujo las funciones de tipo genérico, que permiten escribir código más seguro y reutilizable. También se introdujeron las anotaciones y las enumeraciones.
Java 6 (2006): Esta versión se centró en mejoras de rendimiento y estabilidad, así como en la introducción de la API de scripting con el motor de scripts Java (javax.script).
Java 7 (2011): Java 7 trajo el soporte para las operaciones de tipo switch con cadenas, el paquete java.nio.file para manipulación de archivos y la introducción de las funciones de cierre (try-with-resources) para la gestión de recursos.
Java 8 (2014): Una de las versiones más influyentes, Java 8 introdujo las funciones lambda y la API de Streams, que revolucionaron la programación en Java al permitir un enfoque más funcional y declarativo. También se introdujo el paquete java.time para el manejo de fechas y horas.
Java 9 (2017): Esta versión introdujo el sistema de módulos (Jigsaw) para mejorar la modularidad de las aplicaciones Java y permitir un mejor manejo de las dependencias.
Java 10 (2018): Java 10 trajo características como inferencia de tipos locales y mejoras en el recolector de basura (Garbage Collector).
Java 11 (2018): Esta versión marcó el inicio del ciclo de lanzamiento a largo plazo (LTS) y trajo varias mejoras en la API y en el rendimiento, así como la eliminación de características obsoletas.
Java 12 (2019): Introdujo características como la expresión switch mejorada y el operador teeing en la API de Streams.
Java 13 (2019): Incluyó mejoras en la administración de memoria y la API de Streams.
Java 14 (2020): Introdujo registros (record types), una forma concisa de definir clases de datos inmutables, y mejoras en el manejo de patrones en las expresiones instanceof.
Java 15 (2020): Introdujo patrones de texto y mejoras en la gestión de excepciones.
Java 16 (2021): Incluyó nuevas características como la recolección de registros (record-class garbage collection) y mejoras en el rendimiento y la seguridad.
Java 17 (2021): La última versión LTS en el momento de mi conocimiento en 2022, trajo mejoras en el rendimiento, actualizaciones de las bibliotecas estándar y un soporte continuado a largo plazo.
Es importante tener en cuenta que Java sigue evolucionando con nuevas versiones y características. Los desarrolladores pueden elegir la versión de Java que mejor se adapte a sus necesidades y requerimientos de compatibilidad.

En resumen, Java ha experimentado una evolución significativa a lo largo de los años, con cada versión introduciendo nuevas características y mejoras. Las versiones más recientes han centrado su atención en mejorar el rendimiento, la seguridad y la legibilidad del código, lo que hace que Java siga siendo un lenguaje de programación relevante y popular en la industria del desarrollo de software.
### Spring
13. ¿Por qué?
13. Reactivo Orientado 
13. Nube y serverless
13. Applicaciones Web
13. Orientado a eventos
13. Lotes
### Spring boot
19. ¿Por qué? Dependencias 
19. Beans 
19. Componentes
19. Seguridad
19. Repositorios
19. Controladores
### Configuracion
25. ¿Por qué? CaaS
25. Yaml
25. Seguridad
25. Ambientes
25. Docker
25. Kubernetes
## Arquitectura
### Servicios
31. ¿Por qué? SoA
31. Separacion por responsabilidad
31. Separación por dominio
31. Arquitectura de microservicios
31. Principios
31. Patrones
### Bases de datos
37. ¿Por qué? BD
37. SQL
37. Indexes
37. NoSQL
37. Documentos
37. Nodos
### SOLID
43. Single responsibility principle
43. Open/Close principle
43. Liskov substitution principle
43. Iterface segregation principle
43. Dependency Inversion principle
43. Results
### Mensajería
49. Sistemas distribuidos
49. Mensajes
49. Clientes
49. Consumidor
49. Productor
49. Tecnologías
### Ambientes
55. Porque separar por ambientes?
55. Prod
55. Local
55. Dev
55. QA
55. Performance
## Agile
### Cascada
61. ¿Qué es?
61. Por qué existe
61. Fases
61. Ventajas
61. Desventajas
61. Gantt
### Agile
67. ¿Qué es?
67. ¿Por qué existe?
67. ¿Cuándo se usa?
67. Manifiesto Agile
67. Fases
67. Lean
### XP
73. ¿Qué es?
73. ¿Cuándo se usa?
73. Ciclo de vida 
73. Valores 
73. Reglas
73. Prácticas
### TDD
79. ¿Por qué?
79. Beneficios
79. Tests antes del código
79. Fases
79. Mejores Prácticas
79. Niveles de uso
### Herramientas de Seguimiento de tareas
85. ¿Qué son las herramientas de seguimiento y para qué sirven?
85. Gannt
85. Kanban
85. Poker de Puntos de historia 
85. 
85. 
## Calidad
### Calidad en arquitectura
91. ¿Cómo es un sistema bien hecho?
91. Requerimientos
91. Sistemas a la medida
91. Test regresión
91. Test performance
91. Correctitud
### Calidad en código
97. ¿Qué es código bien hecho?
97. Requerimientos
97. Modularidad
97. Coverage
97. Test unitarios
97. Correctitud
### Calidad en el trabajo en equipo
103. Comunicación
103. KTs
103. Indice de distancia al poder
103. Comentarios
103. Confianza
103. Logros
## Valor agregado
### Expectativas en valor agregado
109. ¿Por qué?
109. Análisis técnico 
109. Diseño de sistemas
109. Utilizacion de recursos
109. Investigación 
109. Docencia
### Oportunidades en valor agregado
115. 
115. 
115. 
115. 
115. 
115. 
