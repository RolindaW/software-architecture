# Clean Architecture

## Decoupling

En la Clean Architecture se proponen dos enfoques para lograr el Decoupling del codigo
Primero, propone estructurar el sistema en Layers (capas) y Use Cases
Despues, propone distintos Modes para organizar esemismo codigo: Code, Component y Service
Ambos enfoques son compatibles, inclusivos, es decir, uno no exluye el otro

### Layers and Use Cases

La separacion en Layers propone organizar el codigo agrupado segun las distintas responsabilidades dentro del sistema: Business (diferenciando Domain - Entities - y Application - Use Cases), Adapters/Controllers (interfaz entre Business y Details) y, finalmente, Details (Persistance - Filesystem, Database, Blob Storage-, Presentation - UI, Services - Web, FTP, Socket).
Es una forma de aplicar el principio Separation of Concerns o, tambien, Single Responsibility Principle
De esta forma es posible que se organicen equipos de trabajo segun capas (e.g. un equipo de frontend UI)
Ademas, de ser la unica forma de orgainzar el sistea, tambien podria servir como mecanismo para las releases - donde cada componente/proceso fuera una Layer (esto de componenete/proceso...ya nos vamos al tema del Mode que veremos despues)

Despues, propone separar el sistema segun los Use Cases
De esta forma, se podrian organizar equipos de trabajo por Use Cases o agrupacion de Use Cases
Aplicaria igualmente a como se podria Release/Deploy el sistema - donde cada componentes/proceso fuera una Use Case

Finalmente, se indica que podria organizarse el sistema en dos niveles: primero por Use Cases y, segundo, por Layers - i.e. el codigo estaria estructurado por Use Cases que, internamente, diferenciaria claramente cada una de las Layers que lo componen
Esto permite maximizar tanto la variedad de formas de organizar los equpos de trabajo (por Layers y/o por Use Cases) y de Release/Deploy del sistema

Esta ultima propuesta es bastante criticada (TODO - encontrar los distintos enlaces que tengo que lo discute)
Ciertos individuos se quejan de la complejidad que esto anade a la legibilidad del codigo.
Es dificil seguir el flujo de ejecucion del codigo (teniendo en cuenta ademas todas las abstracciones que hay de por medio) e incluso algunos dicen que es imposible siquiera de debugear o de seguir el stack-trace (esto no lo termino de entender pero bueno... si fuera lo del stack trace podria lllegar a entender - que por las abstracciones en algun momento quedo Obscured - pero lo otro no lo entenderia)

### Mode

Independientemente de como decidamos estructurar el sistema segun la primera propuesta, tenemos el enfoque del Mode
El Mode especifica como se puede conseguir el Decoupling segun donde se ubique/ejecute el codigo y como se comunique
Diferenciando entre 3 propuestas: Code, Component y Service

Code viene a decir que el Decoupling ocurre solo internamente, a nivel de codigo - llamadas directas dentro de la misma solucion.
Es decir, el codigo no se organiza ni por componentes (e.g. DLL) ni por servicios.
En la practica puede ser un unico proyecto (monolito) o mas de uno, pero el sistema se entrega como un solo entregable/artefacto (e.g. un unico ejecutable - WIndows .EXE - o una unica libreria - Windows .DLL o .LIB, segun Dynamic o Static)
Este seria el ejemplo de la estructura tipica de un programa que cualquier desarrollador con menor/mayor experiencia podria hacer.
Obviamente, luego hay que ver como conseguir el Decoupling - aplicariamos el Dependency Inversion Principle con abstracciones (i.e. Interface, Abstratct Class - dependera del Programming Language) e Dependency Injection
La comunicacion entre los elementos es barata y, por tanto, frecuente. Todo existe en el mismo Virtual Memory Address Space luego los recursos se pueden acceder directamente.

Component viene a decir que el sistema se organiza por componentes
Ya no se entrega un unico entregable/artefacto, ahora el sistema se descompone en distintas piezas que se disponen a trabajar juntas en tiempo de ejecucion.
Entiendo que todo corre en el mismo proceso o, a lo sumo (Warning! Esto no lo tengo tan claro), en caso de haber multiples procesos que todos corren en el mismo Host y podrian, mediante un protocolo de comunicacion adecuado (IPC) comptartir recursos y comunicarse medianamente comodamente
Esto nos permite - en caso de tener un Healthy (Acyclic) Dependency Graph - poder Compile/Build/Release/Deploy el sistema por piezas
Ademas nos permite poder trabajar en equipos organizados (especializados) segun componentes
Tambien, si se aplica correctamente el Liskov Substitution Principle es posible sustituir dinamicamente disitntas piezas del sistema por otras que - respetando el mismo Contract - tengan un comportamiento distinto
Y, con el Open-Closed Principle, podriamos extender la funcionalidad dando la posibilidad de inyectar componentes al vuelo para incorporar (o modificar) nueva funcionalidad.

Services consiste en romper el sistema en servicios
Estos servicio pueden correr en el mismo host (No lo tengo tan claro - esto signigicaria un punto intermedio muerto entre la propuesta anterior y esta) o en host distintos
Obviamente la comunicacion es mucho mas cara (y, por tanto, - idealmente - menos frecuente), ya nos tenemos que ir a Sockets
En mas dificil compartir recursos - ni usan la misma memoria, ni pueden compartirla con ningun mecanismo: todo tiene que ser intercambiado completamente entre los sistemas (salvo que usen algun tipo de orquestador o manager comun que gestione los assets)
Esto, desde el punto de vista de trabajo da una libertad absoluta. Los desarrolladores pueden centrarse en respetar el contrato (input/output) requerido y de puertas para adentro hacer lo que les de la gana.
Tambien da mucha libertad desde el punto de vista de Build/Release/Despliegue, es muy comodo, no se depende del resto para nada (solo en lo concreto, en que esten bien implementados para que el todo funcione correctamente)
La escalabilidad a priori parece muy comoda porque nos limitados a incorporar nuevo servicios bajo demanda
Warning! Imagino que habra un pero mas alla del tema de que la comunicacion es cara y, por tanto, menos frecuente (y tambien el tema de compartir recursos). Sino, seria una propuesta de arquitectura con - a priori - mas puntos positivios que negativos. Pero ojo! Como todo, hay que ver si la arquitectura va bien para nuestro caso particular - quiza no tenga mucho sentido orgnaizar el sistema por servicios para nuestro tipo de aplicacion.
Este es un patron de arquitectura conocido como Service (o Service Oriented Architecture - SOA) o Microservices

TODO: Reference Robert C. Martin - Clean Architecture book
