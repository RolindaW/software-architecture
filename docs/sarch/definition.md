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

Infamous architecture and architect

00:35 I do not really like the term "Software Architect" because it summons these images of some senior person in an organization who is setting rules and standards of how software should be written but has not actually written any software for maybe 10 or 20 years.
00:57 Joel Spolsky used the term "Architecture Astronauts". 
01:01 Often cause a lot of problems for software projects.
01:05 So the whole term "Architect" and "Architecture" has that kind of nasty taste to it.
01:13 It is something that we need to change as industry because the way we write code is important.
01:31 If you are going to be a technical person you have to be someone who is familiar and confortable with the act of programming.
01:38 There has been for quite a while, in architecture particularly, this notion that architecture is kind of beyond programming and if you are an architect you should not be programming anymore.
01:49 That is something that I have always thought is very wrong.
> Arquitectura sugiere diferenciarse de la programacion. Figura de arquitecto tinte pomposo. Lo mismo que indica en la introduccion de "Software Architecture Guide".

What is architecture?

01:54 What really is architecture? What does even the word mean in a software context?
02:02 Borrowing the term from buildings and construction, it actually means something completely different. 
> Las analogias con la construccion y edificacion quiza no sean la mejor forma de tratar de definirlo.

02:20 Kind of official definition. ANSI/IEEE Std 1471-2000: the fundamental organization of a system, embodied in its components, their relationships to each other and the environment, and the principles governing its design and evolution.
02:28 That kind of definition has been around for a while.

02:35 What architecture does mean. A reaction to a statement like that (the one given before)
02:42 Ralph Johnson. Probably best known as one of the authors of the design patterns the gang of 4 book.
03:12 He would sent an email once that was a reaction to that definition of architecture.
03:16 I ended up stealing it completely on a column on architecture.
> Ver "Who Needs an Architect".

03:32 He basically took this definition and said...
03:34 The problem with this definition is that it relies on this notion of somehow what are the highest level most critical important components.
03:50 What does that mean? How do you select which components, what relationships, are important? There is a gazillion components and relationships in a product.
04:00 What matters to make some of them architectural and some of them not?
> El problema con la definicion oficial es el como es posible determinar que es lo importante.

04:30 Ralph Johnson: Expert developers shared understanding of the system design.
04:38 Architecture is much a social thing. It is that fuzzy embedded understanding that really matters.
04:44 There may be diagrams here and there, there might be documents here and there and they may have architecture written on them but there are just a representation, and usually an imperfect representation, of that shared understanding.
04:57 What you are trying to do with a software project, particularly as software projects grow, is you want to make sure you have a good shared understanding between the people who are leading the project. That is really what matters.
> La arquitectura es el entendimiento compartido por los expertos de un sistema.

05:16 Another definition that is also quite important: the set of design decisions that must be made early.
05:30 Ralph Johnson: Really is what you wish you could get right early on.
05:35 Because the point is, the decisions you might need to make early you do not have the information. You only learn about what the software product should be structured like as you are building it.
> La arquitectura es las decisiones que quisieras poder tomar correctamente temprano.
> No es posible realizarlas antes por falta de informacion. Se aprende a estructurar el proyecto software a medida que se construye.

05:45 What it really boils down to is you concerned about "the decisions that are hard to change".
05:55 A useful way of thinking about architecture "what is hard to change?".
05:58 It does lead to some different thoughts about what are the main components and how do they fit together.
06:06 The choice of programming language is a decision that is hard to change. But it is not usually considered what are the top level components.
> La arquitectura es las decisiones dificiles de cambiar.
> Lenguage de programacion (aunque no suele considerarse un componente de alto nivel).

06:25 We have got to things here (shared understanding and hard to change) but they actually boild down to what in his view (Ralp Johnson) and in my view too is the definition of architecture: the important stuff, whatever that is.
> Lo importante es lo importante, sea lo que sea.

06:42 It sounds like an almost silly statement.
06:46 But actually it is a very profound statement.
06:50 If you are trying to think about your software system and what its architecture is, the first thing you have to do is to figure out what is important. What do we as the technical leadership of a project consider to be the most important things in there? Or even in a solo project, what is the key things about the system? What is the most important thing of the codebase that I have to keep at the top of my head when I am working on it? That decision about hat is important is really the key thing that goes on. And that is the thing that trumps in everything else.
07:32 Martin Fowler: architecture (and I follow Ralph and I say) is the important stuff. Architecture is the important stuff, whatever that happens to be.
> La arquitecture es lo importante.
> Personalmente, no termino de entender esta propuesta.

Why is architecture important?

08:00 We need to put less effort on quality so we can build more features for our next release.
08:08 We need to sort of do not worry so much about modularity in these design ideas, we got to crank out features.
> Frecuentemente, la direccion sacrifica la arquitectura (calidad interna) para centrarse en entregar nueva funcionalidad a la mayor brevedad.

08:18 The reaction of a lot of people to this is they get frustrated and they try to argue in terms of "we got to do a decent job as software professionals, we got to stand up to our professional standard"
08:32 It is almost like taking a moral response: "software architecture is important for moral reasons. We need to do a good job. We need to be craftmans"
> Los desarrolladores se frustran. Una especie de respuesta moral.
> Tratar de discutir en terminos morales, de honrar su labor de artesania.

08:45 Unfortunately, if taken that line you have lost.
08:53 You are making a battle between craftmanship and economics, and economics always wins.
> La batalla entre artesania y economia siempre estara dominada por esta ultima. No es una ruta viable.

09:00 If you want to say why is architecture important you have to instead cast it in economic terms.
09:06 The problem with this arguments is it got a notion of what is quality based on an idea that quality is something I can trade off for cost. A trade off on quality and cost.
> Requiere argumentar la calidad en terminos economicos.
> El problema es que esto suscita la idea de que la calidad puede intercambiarse por costo. Un compromiso directo calidad/coste que implique menor coste a expensas de menor calidad y, viceversa. Esto puede alentar a las figuras externas responsables del proyecto a sacrificar calidad en pos reducir costo.

09:24 But quality in software means a whole bunch of different things.
09:30 Some of these things can be seen by an external person (user, manager, customer), but some of them can not.
09:40 Whether your software has a good architecture, or a good modular design or whatever, that is not something that is visible.
09:50 Two forms of quality: external (visible to users and customers) and internal (not directly visible).
09:55 Architecture is about internal quality.
TODO

10:27 What matters in terms of internal quality is more a long-term picture
TODO








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
