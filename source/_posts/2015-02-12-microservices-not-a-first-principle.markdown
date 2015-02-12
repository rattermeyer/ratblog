---
layout: post
title: "Microservices: Not a first principle"
date: 2015-02-12 21:03:29 +0100
comments: true
categories: 
---
(first published on ["The cattle crew blog"](https://thecattlecrew.wordpress.com/2014/10/30/microservices-a-different-view/) )

Up to now (see our article on Microservices from a SOA perspective) we considered Microservices as an architectural pattern: We discussed the statical structure of your system and the consequences. It seems nowadays that you design explicitely for a microservices architecture. We believe that this is the wrong way to approach the problem.
Don't build the system with the microservices pattern in mind, but ask more important questions about how you want to develop, what are the principles to follow when building a new system... and a microservices architecture emerges naturally.

Believers in an agile development methodology we are. But still, if you are trying to implement systems of a certain size, you must do some management work and answer several questions:

* What is the right team size?
* How to split the teams?
* How to minimize dependencies between teams?
* What roles should be present on the teams?

And beyond team size, you might be considering your development process. If you aim for continuous delivery and potentially continuous deployment you must require other qualities from the system

* Isolating dependencies: It should be possible to deploy two different parts of an enterprise application that require different dependencies (Java version, Programming Language, ...)
* Isolation of orthogonal services: two unrelated services that happen to run on the same machine should not be able to negatively affect one another
* Repeatability of deployments: If we need to revert to a previous version of a software, this is easily possible. The release is self-contained (not dependent on any state of the host environment)
* Version everything (not only source code, but also infrastructure description) to manage organization and deployment of application / service versions
* Team is responsible for development and maintenance (Team size and members may vary over time).

Regarding the team aspects, agile development methodologies give us some rules of thumb:

* Team size: 7 +/- 2
* All roles present: Developer, Tester, UI, ...
* Full stack development: split around business functionality not around technology

The reason for these aspects is that the team should take as many decisions as possible autonomously. This can best be achieved when the team has full responsibility for a cohesive set of features. Full responsibility includes front-end, back-end, development and operations responsibility. Somehow this can be also seen as another example of Conways law [1]. Conways law states "organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations".
We believe that an organization that fully implements self-sufficient teams with authority over their area of work will eventually arrive at a microservices architecture.

And if you have the whole application lifecycle in mind, you will see, that at some point you might throw away your system and build something new. Design for re-use is hard (very hard indeed). What we have seen quite often is that the step of rebuilding the system was further and further delayed to the future, because of a monolithic application. It was not easy to replace some parts, either all or nothing. So, you should probably not design for reuse, but design for replacement.
We have observed on various projects, that following these principles  will result in small, self-contained deployment units, nowadays named microservices. So the long debated question: "What is the right size for a Microservice" is equivalent to ask "How to organize my teams and maximize their output"?
