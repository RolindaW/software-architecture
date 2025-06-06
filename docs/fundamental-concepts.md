# Fundamental concepts before choosing a software architecture

## What is software architecture

Software architecture es estructura.
Software architecture es organización de código (en módulos, componentes, servicios...) y la comunicación entre dichos elementos. Ambas son necesarias para poder hablar de arquitecura (es decir, por muy bien organizardo que tengas el codigo en modulos o componenetes, si el uso entre los mismos no es bueno - dependencias ciclicas, orden de dependendicas incorrecto - entonces no se estan siguienndo las buenas practicas minimas de arquitectura software).

En ocasiones se habla de arquitectura software o una falta de arquitectura en caso de que no se haya aplicado un patrón de arquitectura conocido o popular, como puede ser Clean Architecture, Hexagonal Architecture, Onion Architecture, Layered Architecture, etcétera. o cualquier variante/combicacion-hybrido de las mismas.

En mi opinión, siempre hay una arquitectura, incluso aunque no se haya aplicado un patrón convencional o una variante de algún patrón convencional. El hecho de que hayas construido un sistema software de cualquier manera implica que se le haya aplicado cierta arquitectura, aunque esa arquitectura sea una falta de arquitectura en si misma (o algo que no presente unas buenas prácticas de arquitectura).

## Benefits of software architecture

Los beneficios de la arquitectura software, entre los más conocidos, pues podemos hablar de la legibilidad del código, el hecho de organizar el código permite que se pueda leer y entender mucho más fácilmente.

También favorece al desarrollo al romper el código o estructurarlo u organizarlo en diferentes partes claramente diferenciables. Dependiendo del tipo de enfoque que se le dé, esto podrá ser distinto. Permite que distintos equipos puedan trabajar de forma más cómoda.

Otro beneficio interesante tiene que ver con las releases y el deployment. Si por ejemplo rompemos un sistema en diferentes componentes que se pueden realizar y se pueden poner a funcionar de forma independiente, hacemos que hacer cualquier tipo de build sea muy cómoda, entregar una nueva versión o parte de un sistema sea muy cómoda y que además también puedas hacer un deploy en hot, lo que se dice en caliente, mientras el sistema está corriendo y hacer una sustitución por un componente más actualizado con algún hotfix o lo que fuere.

Otro beneficio muy interesante de la arquitectura software es la escalabilidad, la posibilidad de que un sistema que a priori puede que no se haya pensado para que vaya a crecer mucho, pero puedes dejar abierta esa puerta y en el futuro poder extenderlo o poder ampliarlo. Dependiendo también de lo que te pueda interesar ampliar en tu caso. En algunos sistemas no interesará que el sistema pueda crecer de ninguna manera. En otros casos puede que el sistema tenga que crecer en el futuro o en un futuro más a corto plazo, pero en diferentes partes. Por ejemplo, en una arquitectura de servicios, es bastante lógico que vaya a incrementar el número de servicios que va a ofrecer el sistema. En una arquitectura que admita, que es una arquitectura que, por ejemplo, necesite que el código se modifique el comportamiento para ciertos clientes, pues más que crecer en servicios tendría que permitir que se pueda extender la funcionalidad, de forma que cambie según el cliente en el que está funcionando ese sistema.

Un punto muy curioso e importante a tener en cuenta es que no todas las arquitecturas proporcionan los mismos beneficios y tampoco en la misma medida. Un tipo de arquitectura puede ser muy buena, por ejemplo, para la escalabilidad y otra puede ser buena para escalabilidad, pero de otra forma o en otra magnitud. Por ejemplo, lo que hemos comentado antes: puede ser buena para escalar en el número de servicios que se puede ofrecer o de funcionalidades y otra puede ser mejor desde el punto de vista de cómo se va a poder extender una funcionalidad o funcionalidades existentes. Luego es importante tener en cuenta que no todas las arquitecturas ofrecen los mismos beneficios ni en la misma magnitud.

Y, por lo tanto, es importante conocer las distintas opciones de arquitectura que están a nuestra disposición para saber cómo debemos aplicar la que mejor se adapte a nuestras necesidades y al contexto, y no aplicar una arquitectura por aplicar sin ningún criterio.

## How to select the right architecture

Elegir una arquitectura software no es un proceso trivial, es necesario conocer una serie de requisitos o de características del proyecto en el que se va a trabajar antes de elegir la arquitectura que mejor se pueda adaptar. En estas características podríamos tener en cuenta, por ejemplo, la experiencia del equipo de desarrollo, algunos requisitos de cliente, herramientas y tecnologías que se vayan a elegir, plazos y presupuestos, etc.

Algunos profesionales recomiendan que la arquitectura no sea algo que haya que seleccionar en un principio y aferrarse a ella de forma muy estricta. Es posible que al principio del proyecto no sepamos muchas cosas y, por tanto, elegir una arquitectura de forma muy forzada sin tener en cuenta ciertas características del proyecto, sea o resulte en una mala decisión que nos perjudique en el futuro.

Tambien, en algunas fases del desarrollo, es posible que la arquitectura vaya cambiando, tiene que ser flexible. No es que tenga que cambia dracticamente, quiza mas alguna pincelada aqui y alla.

## Desmitifying Software Architecture

Opiniones muy diferentes sobre lo que verdaderamente Software Architecture aporta.
Algunos lo consideran parte critica de todo sistema software.
Otros lo ven como algo menos relevante, quiza incluso en ocasiones sobrevalorado.
Como es esto posible? Que haya opiniones de caracter tan opuesto en cuanto a un asunto que aparentemente puede marcar la diferencia entre el exito o fracaso de un sistema software.

## Common: Layers and Communication

Todas los patrones de aruquitectura comparten una premisa comun: Separations of Concerns y COmmunicaton
ALgunos lo hacen mediantes Layers, otros con Use Cases, otros son Hybrids
La sefunda parte de la premisa es como es la comunicacion entre dichas capas: en que sentido fluye, si se permiten saltos - bypass o passthrough - (open) o no (closed), etc.

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
