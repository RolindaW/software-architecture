# Fundamentals of Software Architecture

## Control Flow and Dependency Order

Control Flow y Dependency Order son topics inherentes a todo Software System, independientemente de que se le haya aplicado un patron de arquiectura - y de cual sea - o no.
Es importante entender estos conceptos, como se relacionan y como poder controlarlos - cuando se requira - en nuestro beneficio.
Terminos relacionados: Caller y Calle (control flow); Coupling/Decoupling (dependency)

Las dependencias (Coupling) siempre van a estar presentes, la clave es entender como las podemos organizar para nuestro propio beneficio.
Pricipalmente queremos proteger los elementos mas importantes (Policies - Abstract) - aquellos con menor tendencia a cambiar - de los menos importantes (Details - Concrete) - aquellos que son mas propensos a sufrir cambios.
Importancia y frencuencia de cambio esta relacionado. ALgo importante (Business - Domain and Application , es decir, las reglas del juego) tendra menor tendencia a cambiar debido a su propia naturaleza; de la misma forma, algo menos importante (Persistance, UI, Network, es decir detalles de almacenamiento presentacion, comunicacion, herramientas, tecnologias, etc.) tendra mas tendencia a cambiar.

## Caller and Calle

En el control flow Caller sera la pieza de codigo (funcion, modulo, componente, servicio) que efectue la llamada y Calle sera quien es llamado.
Esto, de primeras, es inpendendiente de quien sea la entidad mas o menos relevente
El flujo de control siempre va marcado por quien llama a quien, y esta necesiad siempre va a existir
Incluso puede ser codigo que llame a otro codigo en el mismo Scope - da lo mismo donde este el codigo - la clave es que siempre habra alguien llamando a otro alquien.

## Contract Location

Entonces la clave de todo esto esta en el contrato.
Caller siempre depende del contrato - la clave esta en quien o donde se define dicho contrato
En un uso nominal - donde una pieza de codigo Caller hace uso de otra Callee, el contrato lo define implicitamente el Callee.
Asi, Caller, que depende explicitamente del Callee, dependera tambien explicitamente de dicho contrato.

TODO: terminar - ver movil

## SOLID

TODO: xplicar brevemente los principios

## Platform: Lowest Dependency

La dependencia de mas bajo nivel es la plataforma (hardware + OS - si es que lo hay) para la que se desarrollara el sistema software.
Procesador, otros.
PC, consolas, disposivitos moviles (tablet, smartphone), otros
Windows, Linux, MacOs, Android, otros
Device Independence: nunca escribir codigo dependiente de dispositivo - e.g. tecnologia disco - es importante tratar de abstraerse (en la medida de lo posible)
Salvo en aquellos casos en que queramos desallorrar un sistema dedicado que exprima al maximo las caracteriistas del host machine.
Hoy en dia el OS se encarga de toda abstraccion con respecto a la maquina fisica - disco, memoria, I/O (input devices, graphics, sound, network) - pero no todos los sistemas presentan un OS (e.g. MicroControllers, SoC/SoPC)

## Programming Language: Lowest Level Software Dependency

La dependencia de mas bajo nivel en todo sistema software es el lenguage de programacion seleccionado para la codificacion - mas alla de cualquier libreria, framework, runtime, otros...
El lenuage de programacion determina la portabilidad del sistema
Tambien determina la especialidad/dominio (e.g. para la web, salvo que utilicemos transpilacion para Angular (TypeScript), React (JS), Vue (Python), el lenguage de progrmacion JavaScript es el unico soportado por los navegadores)
Tambien es posible tener en cuenta los recursos (librerias, frameworks) que existan a disposicion del dominio (e.g. para C++ windowing and context creation libraries, extension loading libraries, maths/algebra 3D graphics calculations)
La eleccion del lenguage de programacion no es trivial
