# What is Software Architecture?

TODO: Resumir conclusiones puesta en comun de todos los articulos analizados.

## [Martin Fowler - Software Architecture Guide](https://martinfowler.com/architecture/)

People in the software industry: "Hazily defined notion of the most important aspects of the internal design of a software system."
> Concepcion general: los aspectos mas importantes del diseno interno de un sistema software. Pero... Cuales? No se especifica; vagamente definido.

Side note: It often suggests a separation from programming and an unhealthy dose of pomposity.
> Frecuentemente sugiere diferenciarse de la programacion. En ciertas empresas el rol de arquitecto software implica no programar. Es una mala practica, pues quien mejor para experimentar el impacto de las decisiones de diseno que quien las toma.
> Tambien tinte pomposo, ostentoso. Con el fin de impresionar o llamar la atencion.
> Todo esto, negativamente.

Own thoughts: Good architecture supports its own evolution, and is deeply intertwined with programming.
> Buena arquitetura soporta su propia evolucion.
> Tambien estrechamente relacionada con la programacion.

Good architecture is important. Why? Otherwise it becomes slower and more expensive to add new capabilities in the future.
> Buena arquitectura es imporante. Agilizar y abaratar incluir nuevas funcionalidades en el futuro.
> Interesante punto de vista de interes de negocio.

What is architecture?

People in the software world have long argued about a definition of architecture.
> La definicion de arquitectura lleva mucho tiempo siendo discutida.

1: The fundamental organization of a system. The way the highest level components are wired together.
> Organizacion fundamental de un sistema. Como los componentes de mas alto nivel se conectan entre si.
Ralph Johnson: There is no objective way to define what is fundamental, or high level. A better view of architecture is the shared understanding that the expert developers have of the system design.
> No hay forma objetiva de definir que es fundamental o alto nivel. Y, asi, el problema con la concepcion general ("los aspectos mas importantes...". Cuales?).
> Comprension del diseno del sistema compartida por los desarrolladores expertos.

2: The design decisions that need to be made early in a project.
> Las decisiones de diseno que tienen que ser tomadas temprano en un proyecto.
Ralph Johnson: The decisions you wish you could get right early in a project.
> Las decisiones que quisieras poder tomar correctamente temprano en un proyecto.
> De hecho, este pensamiento es bastante comun. Robert C. Martin indica que es practicamente imposible tomar las decisiones de diseno correctas en la fase temprana de un proyecto (considerando ademas que la arquitectura de un sistema tiende a cambiar y, por tanto, decisiones que originalmente pudieran ser correctas podrian no ser serlo mas adelante).

3: Ralph Johnson: Architecture is about the important stuff. Whatever that is.
> Lo importante, sea lo que sea.
Martin Fowler: Decide what is important, (i.e. what is architectural), and then expend energy on keeping those architectural elements in good condition. Recognize what elements are likely to result in serious problems should they not be controlled.
> Decidir que es importante (arquitectonico) y dedicar energia a mantener dichos elementos arquitectonicos en buen estado.
> Reconocer que elementos pueden resultar en serios problemas de no ser controlados.

Why does architecture matters?

Tricky subject for the customers and users of software products. It isn't something they immediately perceive.
A poor architecture is a major contributor to the growth of cruft. Software that contains a lot of cruft is much harder to modify, leading to features that arrive more slowly and with more defects.
> Una mala arquitectura es el contribuyente principal al crecimiento de "cruft" (codigo no deseado, innecesario, mal disenado). El codigo es mucho mas dificil de modificar.
> Afecta los intereses de clientes y usuarios de productos software de forma encubierta (funcionalidades que llegan mas lentamente y con mas defectos) y retroactiva (no se percibe inmediatamente).

High internal quality leads to faster delivery of new features. There is less cruft to get in the way.
> Alta calidad interna (menor "cruft" en el camino) conlleva entregas (de nueva funcionalidad) mas rapidas.

We can sacrifice quality for faster delivery in the short term (before the build up of cruft has an impact).
People underestimate how quickly the cruft leads to an overall slower delivery. Attention to internal quality pays off in weeks not months.
> Aun siendo posible secrificar calidad en pos de entregas mas rapidas a corto plazo, la falta de calidad interna pasa factura antes de lo previsto.
> Resultado de abandonar la arquitectura durante la fase temprana de un proyecto. Por que? Priorizar resultados inmediatos en pos de contentar a clientes y usuarios. Requiere encontrar un balance (tradeoff) entre falta y exceso de arquitectura.
> Mas en [Is High Quality Software Worth the Cost?](https://martinfowler.com/articles/is-quality-worth-cost.html)

Application Architecture & Entreprise Architecture

The important decisions in software development vary with the scale of the context that we're thinking about.
The key difference between this and enterprise architecture is that there is a significant degree of unified purpose around the social construction.
> Las decisiones importantes (recordemos, lo arquitectonico) en el desarrollo software varian con la escala del contexto objeto de estudio.
> Diseno/arquitectura aplica a distintos niveles, con distintas responsabilidades, convenciones y patrones segun el caso: coding best practices (naming conventions, comments, function size and responsibility), modulos (ficheros, clases, estructuras de datos + funciones), componentes (librerias, paquetes), servicios, sistema, ecosistema.

A common scale is that of an application, hence “application architecture”.
There's no clear definition of what an application is.
Martin Fowler: A social construction
> Mas en [Application Boundary](https://martinfowler.com/bliki/ApplicationBoundary.html)

"Enterprise architecture" looks architecture across a large enterprise.
Is about understanding what is worth the costs of central coordination, and what form that coordination should take.
At one extreme is a central architecture group.
The other extreme is no coordination at all.

## [Martin Fowler - Making Architecture Matter - Martin Fowler Keynote](https://www.youtube.com/watch?v=DngAZyWMGR0)

TODO

Architecture is the important stuff, whatever that happens to be.

## [Martin Fowler - Who Needs an Architect](https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf)

TODO

## [Ralph Johnson - ???]()

TODO

## [Robert C. Martin - Clean Architecture]()

TODO

## []

## [Ruth Malan - Software Archtecture and Related Concerns](https://www.bredemeyer.com/whatis.htm)

TODO

Muestra como el termino Software Architecture ha ido acunandose a lo largo de los anos de la mano de distintas figuras representativas en el dominio del Software.

## [Wikipedia - Software Architecture](https://en.wikipedia.org/wiki/Software_architecture)

TODO
