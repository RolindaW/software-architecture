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

## Common: Layers and Communication

Todas los patrones de aruquitectura comparten una premisa comun: Separations of Concerns y COmmunicaton
ALgunos lo hacen mediantes Layers, otros con Use Cases, otros son Hybrids
La sefunda parte de la premisa es como es la comunicacion entre dichas capas: en que sentido fluye, si se permiten saltos - bypass o passthrough - (open) o no (closed), etc.

## Desmitifying Software Architecture

Opiniones muy diferentes sobre lo que verdaderamente Software Architecture aporta.
Algunos lo consideran parte critica de todo sistema software.
Otros lo ven como algo menos relevante, quiza incluso en ocasiones sobrevalorado.
Como es esto posible? Que haya opiniones de caracter tan opuesto en cuanto a un asunto que aparentemente puede marcar la diferencia entre el exito o fracaso de un sistema software.

## Three Layers: Presentation, Business, Persistance

Un patron que puede verse en todo sistema, independientemente de la arquitecura empleada, es la distincion del codigo en 3 capas: Presentation, Business, Persistance.

Algunas aplicaciones incorporan todas las capas, y otras no; la que tiene que estar por huevos es Business - es decir, lo que haga la aplicaion.
Un script sencillo que solamente recibe unos argumentos como input y da un output o modifica algo en el sistema no tiene ni presentacion (se maneja desde CLI pero realmente solo para ser invocado - no se si esto ya se consideraria en si mismo presentacion en forma de CLI) ni persistencia.
Otro ejemplo similar seria el de un servicio Stateless - no tiene presentacion ni persistencia
Este mismo ejemplo anterior podria tener persistencia si usase un fichero de configuracion interno para alguna cosa.
Un servicio no-Stateless tambien seria otro ejemplos
Y, una aplicacion grafica de escritorio con persistencia, Filesystem o DB (SQl o NoSQL, da lo mismo) tendria de todo.
Tambien una aplicacion web, componente presentacion (el app frontend, en el cliente) y componente de persistencia (si es que lo tiene) del laddo del servidor (app backend)

En algunos casos estas 3 capas (si es que estan todas - tambien podrian ser solo 2 de ellas) pueden encontrarse corriendo en el mismo proceso (e.g. una aplicacion de escritorio con Windows FOrms .Net o WPF .NET) - desde el punto de vista de usuario solo hay un artefacto.
En otros casos, las capas pueden estar corriendo en procesos distintos - o no, pero se entregan como artefcactos separados que funcionan como un todo el n RUntime. Esto se suele conocer como "n-Tier" (siendo "n-" el numero de Tiers).
En algunos casos estos procesos pueden estar en el mismo Host (e.g. Business corriendo como unos servicios, haciendo uso de un servidor de BBDDD o fileystem en el mismo host, y la UI una aplicacion "tonta" - "Thin Client" - que hace uso de los servicios). Este planteamiento suele utilizarse cuando distintas aplicaciones (frontend, otros servicios, etc.) tiene que hacer uso de un mismo core.
FInalemnte, los procesos pueden estar corriendo en host disitntos (e.g. una aplicacion web comun: el frontend - Presentation - corriendo en el cliente, un browser; el Business corriendo en un servidor como App Backend; la Persistante - filesystem, BBDD, blob-service - corriendo en el mismo server que el Business o incluso en otro server distinto). Ademas, en este ultimo caso es comun poder tener corriendo multiples instancias de los distintos Tiers: no se si llamarlo Clusters, porque aveces pueden ser instances de bloque/conjutnos de servicios.

-> COn relacion a este punto, es bastante comun que la gente beginner vea una aplicacion de escritorio, una aplicacion web, un videojuego...como aplicaciones totalmente diferentes. CUando, realmente, el unico cambio grande desde el punto de vista de arquitectura es donde corren las cosas y como se comunican entre ellas. Una aplicacion grafica de escritorio no es diferente de una aplicacion web en cuanto a """no se como referirme a esto enfoque-punto de vista""": en la aplicacion monolito (1 unico artefacto) de escritorio la UI esta muy pegadita al Business y este a la persistencia (independientemente de si se le aplica buenas practicas de arquitectura o no - todo esta ahi junto formando ese todo); en la aplicacion web la UI corre en el cliente (browser) y el Business - e imaginemos que tambien la Persitencia - en el server. SI te paras a pensarlo lo unico que cambia es que en este segundo caso la UI no esta pega al Business+Persitencia y que, ademas, estan corriendo en Host distintos y requieren de una pasarela intermedia - el Web Server - para poder comunicarse. Pero si nos abstraemos de todo esto, es exactamente lo mismo. Y si la UI fuera un ejecutable de escritorio y Business+Persistance corrieran cmo un servicio local tambien tendriamos lo mismo.

Hay otros elementos que se clasificarian en una de estas capas segun el uso que se le diera.
Por ejemplo, un web server en el backend seria parte de la Presentation - es la parte que permite que las Input (desde una UI o incluso otro servicio) lleguen al server donde acabaran ejecutando de una forma u otra el Business.
Si por el contrario, el server lo consumimos desde el backend podriamos estar hablando de Persistance (e.g. el Business invoca a traves de un cliente de BD al servidor de BD) o del propio Busineness (e.g. el Business consume un web service que complementa su funcionalidad - por ejemplo estos eria algo comun en una arquitecura orientada a servicios o simplemente el uso de un servicio externoque queremos incorporar en nuestra aplicacion) - en ciartas arquitecturas esto no se considera como parte del Business, sino como un Detail (Clean Arch) o un Adapter (Hexagonal Arch)
Tambien podemos encontrar otras cositas como I/O devices (graphcis, sound, network) que, ciertamente, aunque podrian tener parte en el Business, otra gran parte (la concreta, la implementacion/tecnolgoia/tool concreta a emplear) seria mas un Detail.

En resumen, las arquitecturas pueden decir misa (ya lo veremos mas adelante), pero estas 3 capas son algo inherente a practicamente cualquier pieza fotware.
No siempre estaran todas presentes, segun los requisitos/contexto.
Pueden formar parte de un todo (monolito, unico artefacto), o estar separadas como componentes (mismo host), o servicios (normalemnte disitntos host).
Hay algunas cosas que se clasificaran como parte de una capa segun el uso que se le de: servers, i/o devices.
Este tema es algo que aparentemente resulta tan evidente - lo tenemos tan interiorizado - que muchas veces lo pasamos por alto y nos hacemos la picha un lio.

Warning! Todo esto, repito, aunque si es algo que se toca en cualquier arquitectura que se vea (usando los mismos nombres u otros - View en lugar de Presentation, Model en lugar de Busines (+Persistance a veces)), realmente es un concepto elemental mas basico que a arquitectura en si misma.