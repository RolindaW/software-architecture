# Dependency 02

## Dependency always exists

Las dependencias en código siempre existen. Son algo inherente a cualquier sistema software independientemente de si se ha aplicado un patrón de arquitectura o no.

## Importance

Quizás el mayor de los intereses de la arquitectura software son las dependencias. Es importante controlar las dependencias para que ellas no controlen el sistema, es decir, las dependencias si están descontroladas o mal gestionadas, pueden ser un problema que afecte de todas aquellas maneras que hemos dicho que una arquitectura bien planteada puede beneficiar a un sistema software: escalabilidad, trabajo de los equipos, release/deployment, etc.

La correcta gestión de las dependencias es el punto común que prácticamente todos los patrones de arquitectura conocidos discuten y tratan de priorizar su atención sobre este hecho.

## Control flow and Dependency Order

El control flow básicamente tiene que ver con quién llama a quién o quién usa qué. Aquí vamos a distinguir dos roles o dos papeles fundamentales que son el caller, que es quien llama, y callee, que es quién es llamado.

De forma natural, el orden de las dependencias fluye siempre según el control flow.

En ciertas ocasiones es posible que el orden de las dependencias coincida con el control flow y sea el que nos interesa para nuestro caso particular en el sistema. Sin embargo, en otras ocasiones nos interesa que el orden de las dependencias sea el opuesto al que marca el control flow y aquí es donde entra en juego el conocido como dependency inversion principle.

Entonces, lo primero que tenemos que entender es por qué el orden de dependencia importa, que aquí es donde está el kit de la cuestión. Si no entendemos por qué el orden de dependencia importa, entonces no tendría sentido hablar de invertir el orden de dependencias y, por tanto, no tendría sentido hablar de otras muchas cosas como la inyección de dependencias y la arquitectura software en general. Por eso vamos a introducir el porqué es importante gestionar el orden de dependencias según nos convenga, según nos beneficie.

El orden de dependencias se dice que tiene que seguir o fluir de un componente menos importante o un componente de menor nivel o categoría a un componente más importante o de mayor nivel o categoría. Y esto significa que el componente menos importante depende o debe depender del componente más importante.

## Why Dependency Order Matters?

El motivo porque el que queremos que siempre sean los componentes menos importantes los que dependan de los más importantes y, por tanto, que en ciertas ocasiones nos lleven a aplicar la inversión o el principio de inversión de dependencias es porque nos interesa proteger los componentes importantes frente a cambios en los componentes menos importantes, que en general siempre van a ser más frecuentes.

Además, los componentes importantes suelen ser componentes con lógica de negocio, es decir, código que representa la parte del Business, el dominio y la aplicación. Esto sería el CORE del sistema. Los componentes menos importantes son aquellos cuyo código está representando una implementación de un detalle concreto, como puede ser un adaptador, un controlador, cualquier cosa referente a la persistencia, a la presentación, etcétera.

## Dependency Inversion

El conocido dependency inversion principle, uno de los 5 principios SOLID, viene a decir que en caso de que el orden de dependencias entre dos componentes fluya del componente más importante al componente menos importante, entonces es necesario aplicar una inversión de dependencias.

Esto aplica a dependencias entre dos módulos o clases, según se vea, entre componentes, librerías estáticas o dinámicas o incluso servicios. Da igual a qué nivel se aplique el concepto, siempre es el mismo.

La forma en que se consigue la inversión de dependencias suele ser una combinación de una abstracción y una inyección de dependencias.

La abstracción puede conseguirse de distintas maneras, según el lenguaje de programación empleado y también según los recursos que queramos aplicar. Por ejemplo, en un lenguaje de programación de tipado estático como C++, C#, Java, esto se consigue mediante interfaces o clases abstractas. En un lenguaje de programación de tipado dinámico, como JavaScript o Python, esto se consigue directamente, pues viene ya integrado en el propio lenguaje, porque como no tenemos tipos en tiempo de compilación, no hay compilación y los tipos solo aplican en runtime, no necesitamos hacer nada para conseguir esta abstracción.

Es por eso que en el caso de los lenguajes de programación de tipado dinámico se suele aprovechar la naturaleza de estos tipos de lenguajes, donde no es necesario conocer el tipo de dato que se va a manejar de antemano. Es posible por ello hacer esto de diferentes formas, por ejemplo, lo primero sería confiar en que el objeto que te vaya a llegar implemente los métodos que necesitas y directamente usarlo en el caller sin ningún problema con eso. Con esto ya estamos aplicando esa abstracción que realmente no existe porque la abstracción es inherente, un building en el lenguaje. Un segundo paso, por ejemplo, podría ser en el que nosotros hacemos una comprobación de que el método exista antes de llamarlo, entonces aquí ya no estaríamos confiando en la buena fe, digamos, de quien esté implementando el código de ese contrato. Y el último caso ya, por ejemplo, sería utilizar una clase base que implemente estos métodos y que la implementación tenga un flow error, de forma que cuando en nuestro caller reciba la instancia de una clase hija, una subclase de esta superclase que en teoría tiene que hacer un override de todos los métodos porque esta superclase es el contrato. Si falta alguna de las implementaciones, entonces cuando el caller intente llamarlas petará. Pero bueno, la implementación más sencilla en este caso en los lenguajes de programación de tipado dinámico es simplemente, pues recibir en el caller el contrato se asume o se confía que se vaya a cumplir.

## Dependency Inyection - Inversion of COntrol (IoC)

Ahora, junto con la abstracción, el otro mecanismo que nos permite conseguir la inversión de dependencias es la dependency injection. En este caso lo único que hacemos es que la dependencia, el callee, en lugar de ser instanciado por el caller (de forma que ahí creamos una dependencia directa), el callee se recibe en el caller, ya sea en el constructor, en el caso de que sea una clase, o como argumento de la función que estemos llamando. Así, en vez de estar creando la dependencia o declarando la dependencia en el caller, lo que estamos haciendo es recibiendo la dependencia desde fuera y por eso se llama inyección de dependencia.

Finalmente, aclarar que la inyección de dependencias, también conocido como Inversion of Control, puede hacerse o bien manualmente, en nuestro fichero representando a la aplicación, que es donde al final tenemos la mayor cantidad de dependencias, es el fichero más dependiente, la clase o la pieza de código con más dependencias del sistema, en la que sería la de más bajo nivel desde el punto de vista de dependencias, que es la que depende de todos. Una forma es hacerlo todo manualmente y otra opción es hacerlo mediante contenedores. Uno muy conocido, por ejemplo, es Castle Windsor, que básicamente lo que hace es trabajar contra un fichero de configuración donde se especifica contra qué abstracciones se van a utilizar ciertas implementaciones y en el caso luego en el código, cada vez que se requiere una dependencia, se le pide a este contenedor y el contenedor es quien resuelve la dependencia, devolviéndote o inyectando en el constructor o en el método que sea necesario, esa dependencia.

Containers - Windsor Castle

## Contract

Un contrato indica qué hace algo, cómo se comporta, qué tipos de comportamientos ofrece. Un contrato en ningún momento determina cómo hace eso en concreto, un contrato es el qué y no el cómo.

En una llamada de código normal sin ninguna abstracción, una llamada de código directa entre un caller y un callee, el contrato está definido implícitamente en la propia implementación del callee. El callee es la implementación, el cómo va a comportarse, cómo va a funcionar y al mismo tiempo es el qué hace. Está mezclado el contrato con la implementación.

En lo que se refiere a las dependencias, el orden de dependencias y la posibilidad de conseguir una inversión de dependencias, el contrato es la guinda del pastel. Es la piedra angular, lo más importante, y más que el qué define ese contrato es el dónde está definido ese contrato y cómo se accede a él tanto por el caller como por el callee.

Para explicar esto, tenemos que conocer los conceptos caller y callee, que van a determinar el control flow. Contract, que es el contrato que existe entre ambos y, finalmente, componente de alto nivel (importancia) y componente de bajo nivel.

En el primer escenario tenemos un componente de alto nivel siendo el caller y un componente de bajo nivel, siendo el callee. Luego el control flow fluye del caller hacia el callee y en este caso esto no es correcto porque según el principio de inversión de dependencias, el orden de dependencias tendría que estar apuntando al revés y como hemos dicho que el orden de dependencias de forma natural sigue el control flow, en este caso tendríamos que invertir el orden de dependencias. El contrato, en este caso, está definido en el propio callee, entonces para lograr la inversión de dependencias tenemos que sacar el contrato de lo que es la propia definición del callee a una abstracción. Entonces eso puede ser bien una interfaz o una clase abstracta, imaginémonos que puede ser propiedad de tanto el componente caller como de un componente de más alto nivel todavía que el componente caller. Un ejemplo sera un Use Case (alto nivel) que quiere hacer uso de una Adapter de BBDD - o cualquier tipo de persistnecia en general - (bajo nivel).

En un segundo escenario tendríamos un componente de bajo nivel como caller y un componente de alto nivel como callee. En este caso, el control flow, que va del componente de bajo nivel al de alto nivel, determina que el orden de dependencias es correcto, porque las dependencias fluyen en el mismo sentido que el control flow y, por tanto, en este caso el orden es correcto: va del componente menos importante al componente más importante.
En este caso no es necesario definir o utilizar una abstracción para poder hacer la llamada, no nos interesa. Lo primero es que en este caso no nos interesa aplicar el principio de inversión de dependencias, porque no lo necesitamos. En caso de que usemos una abstracción, que tampoco lo necesitamos, realmente lo que vamos a hacer es lo que se conoce como el interface segregation principle. Aunque estemos utilizando una abstracción como una interfaz o una clase abstracta para que el caller (componente de bajo nivel) llame al componente de alto nivel, el callee, en este caso no lo hacemos por hacer una inversión de dependencias, sino que lo hacemos por proteger al caller (componente de bajo nivel) frente a cambios en el componente de alto nivel. Así, el componente de bajo nivel solo conoce la funcionalidad que le interesa del componente, en este caso callee.
Un ejemplo de esto seria un Controller de UI (bajo nivel) que hace uso de un Use CAse (alto nivel). El ordern de dependeicas, marcado por el control flow, es correcto, luego el principio de inversion de dependencias no aplica. En este caso, es comun utilizar una bastraccion para que el caller solo dependa de la porcion de codigo del calle de la que vaya  ahacer uso - y asi queda protegido frente a cambios en otras partes de ese componente que no le afecten (pero esto es un princiip disnton - interface segregation principle).

Si nos damos cuenta, la clave de todo esto es que independientemente de si el caller es un componente de alto nivel y el calle de bajo nivel, o viceversa, el contrato siempre tiene que estar o bien en el componente de alto nivel o bien en un componente de alto nivel más alto que el componente de alto nivel. La diferencia es que en un caso el primero que hemos visto, el contrato se utiliza para aplicar el principio de inversión de dependencias y en el segundo caso se utiliza para aplicar el principio de interface principal.
