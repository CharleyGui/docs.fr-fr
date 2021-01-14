---
title: Conception d’un microservice orienté DDD
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre la conception du microservice orienté DDD (Domain Driven Design) et de ses couches d’application.
ms.date: 01/13/2021
ms.openlocfilehash: 1d17f0842bb371ce65e96f33d25b2d6e94493396
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188333"
---
# <a name="design-a-ddd-oriented-microservice"></a>Concevoir un microservice orienté DDD

La conception DDD (Domain-Driven Design) préconise une modélisation basée sur la réalité de l’entreprise applicable à vos cas d’usage. Dans le contexte de la génération d’applications, DDD traite les problèmes comme des domaines. Elle décrit les problèmes indépendants comme des contextes délimités (chaque contexte délimité correspond à un microservice) et met l’accent sur un langage commun pour discuter de ces problèmes. Elle suggère également de nombreux concepts et modèles techniques, tels que les entités de domaine avec des modèles enrichis (aucun [modèle de domaine anémique](https://martinfowler.com/bliki/AnemicDomainModel.html)), des objets de valeur, des agrégats et des règles de racine d’agrégat (ou d’entité racine) pour prendre en charge l’implémentation interne. Cette section présente la conception et l’implémentation de ces modèles internes.

Parfois, ces modèles et règles techniques DDD sont considérés comme des obstacles avec une courbe d’apprentissage importante pour implémenter les approches DDD. Toutefois, le plus important ne concerne pas les modèles proprement dits, mais l’organisation du code afin qu’il soit aligné sur les problèmes métier et l’utilisation des mêmes termes métier (langage omniprésent). En outre, les approches DDD doivent être appliquées uniquement si vous implémentez des microservices complexes avec des règles métier importantes. Des responsabilités plus simples, comme un service CRUD, peuvent être gérées avec des approches plus simples.

Le tracé des limites est la tâche clé lors de la conception et de la définition d’un microservice. Les modèles DDD vous aident à comprendre la complexité dans le domaine. Pour le modèle de domaine de chaque contexte délimité, vous identifiez et définissez les entités, les objets de valeur et les agrégats qui modélisent votre domaine. Vous générez et affinez un modèle de domaine contenu dans une limite qui définit votre contexte. Et qui est explicite sous la forme d’un microservice. Les composants au sein de ces limites finissent par être vos microservices bien que, dans certains cas, un contexte délimité ou des microservices métier peuvent être composés de plusieurs services physiques. La conception DDD concerne les limites, tout comme les microservices.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Maintenir les limites de contexte de microservices relativement faibles

Le choix de l’emplacement des limites entre les contextes délimités assure l’équilibre de deux objectifs concurrents. Tout d’abord, vous voulez créer initialement les plus petits microservices possibles, même si cela ne doit pas être le principal facteur ; vous devez créer une limite autour des éléments en manque de cohésion. En second lieu, vous voulez éviter les communications bavardes entre microservices. Ces objectifs peuvent être contradictoires. Vous devez les équilibrer en décomposant le système en autant de petits microservices que possible jusqu’à ce que vous voyiez l’augmentation rapide des limites de communication avec chaque nouvelle tentative de séparation d’un nouveau contexte délimité. La cohésion est essentielle dans un contexte délimité unique.

Elle est similaire aux [mauvaises odeurs (ou « code smell »)](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) lors de l’implémentation de classes. Si deux microservices doivent beaucoup collaborer entre eux, ils doivent probablement représenter le même microservice.

Une autre façon d’examiner cet aspect est l’autonomie. Si un microservice doit s’appuyer sur un autre service pour traiter directement une demande, il n’est pas réellement autonome.

## <a name="layers-in-ddd-microservices"></a>Couches dans les microservices DDD

La plupart des applications d’entreprise avec une importante complexité technique et métier sont définies par plusieurs couches. Les couches sont un artefact logique et ne sont pas liées au déploiement du service. Elles existent pour aider les développeurs à gérer la complexité dans le code. Les différentes couches (comme la couche de modèle de domaine par rapport à la couche de présentation, etc.) peuvent avoir des types différents, qui exigent des traductions entre ces types.

Par exemple, une entité peut être chargée à partir de la base de données. Par la suite, une partie de ces informations, ou une agrégation d’informations dont des données supplémentaires provenant d’autres entités, peut être envoyée à l’interface utilisateur du client via une API web REST. L’intérêt ici est que l’entité de domaine est contenue dans la couche de modèle de domaine et qu’elle ne doit pas être propagée à d’autres zones auxquelles elle n’appartient pas, comme à la couche de présentation.

En outre, vous devez disposer d’entités toujours valides (consultez la section [Conception de validations dans la couche de modèle de domaine](domain-model-layer-validations.md)) contrôlées par les racines d’agrégat (entités racine). Par conséquent, les entités ne doivent pas liées aux vues clientes, car il est possible que certaines données ne soient pas encore validées au niveau de l’interface utilisateur. C’est la raison pour laquelle le ViewModel est destiné. Ce dernier est un modèle de données destiné exclusivement à répondre aux besoins de la couche de présentation. Les entités de domaine n’appartiennent pas directement au ViewModel. Au lieu de cela, vous devez effectuer la conversion entre ViewModels et entités de domaine, et vice versa.

Quand le problème de la complexité est abordé, il est important de disposer d’un modèle de domaine contrôlé par les racines d’agrégat qui vérifient que l’ensemble des invariants et règles associés à ce groupe d’entités (agrégat) fonctionne via un point d’entrée unique (une porte), la racine d’agrégat.

La figure 7-5 montre l’implémentation d’une conception par couches dans l’application eShopOnContainers.

![Diagramme montrant les couches dans un microservice de conception piloté par domaine.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Figure 7-5**. Couches DDD dans le microservice de commandes dans eShopOnContainers

Les trois couches dans un microservice DDD comme Ordering. Chaque couche est un projet Visual Studio : la couche Application est Ordering.API, la couche Domaine est Ordering.Domain et la couche Infrastructure est Ordering.Infrastructure. Vous souhaitez concevoir le système afin que chaque couche communique uniquement avec certaines autres couches. Cette approche peut être plus facile à appliquer si les couches sont implémentées en tant que bibliothèques de classes différentes, car vous pouvez identifier clairement les dépendances qui sont définies entre les bibliothèques. Par exemple, la couche de modèle de domaine ne nécessite pas de dépendance sur une autre couche (les classes de modèle de domaine doivent être des classes d’objets CLR traditionnels ou [OCT](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)). Comme le montre la figure 7-6, la bibliothèque de couches **Ordering. Domain** a des dépendances uniquement sur les bibliothèques .net ou les packages NuGet, mais pas sur une autre bibliothèque personnalisée, telle que la bibliothèque de données ou la bibliothèque de persistance.

![Capture d’écran des dépendances de classement. domain.](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Figure 7-6**. Les couches implémentées comme des bibliothèques permettent de mieux contrôler les dépendances entre les couches

### <a name="the-domain-model-layer"></a>Couche de modèle de domaine

L’excellent livre d’Eric Evans [Domain Driven Design](https://domainlanguage.com/ddd/) affirme ce qui suit à propos de la couche de modèle de domaine et de la couche d’application.

**Couche de modèle de domaine** : chargée de représenter les concepts de l’entreprise, des informations sur sa situation ainsi que ses règles. L’état qui reflète la situation de l’entreprise est contrôlé et utilisé ici, même si les détails techniques du stockage sont délégués à l’infrastructure. Cette couche est au cœur des logiciels d’entreprise.

La couche de modèle de domaine est l’endroit où l’entreprise s’exprime. Quand vous implémentez une couche de modèle de domaine de microservice dans .NET, cette couche est codée comme une bibliothèque de classes avec les entités de domaine qui capturent les données ainsi que le comportement (méthodes avec logique).

Selon les principes [d’ignorance de la persistance](https://deviq.com/persistence-ignorance/) et [d’ignorance de l’infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance), cette couche doit ignorer complètement les détails de persistance des données. Ces tâches de persistance doivent être effectuées par la couche d’infrastructure. Par conséquent, cette couche ne nécessite pas de dépendances directes sur l’infrastructure, ce qui signifie qu’il est important que vos classes d’entité de modèle de domaine soient des classes [OCT](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object).

Les entités de domaine ne doivent pas avoir de dépendance directe (par exemple, une dérivation d’une classe de base) sur un framework d’infrastructure d’accès aux données comme Entity Framework ou NHibernate. Dans l’idéal, vos entités de domaine ne doivent pas dériver d’un type ni implémenter un type défini dans un framework d’infrastructure.

La plupart des frameworks ORM modernes comme Entity Framework Core autorisent cette approche, afin que vos classes de modèle de domaine ne soient pas couplées à l’infrastructure. Toutefois, il n’est pas toujours possible d’avoir des entités OCT lors de l’utilisation de certains frameworks et bases de données NoSQL, comme Actors et Reliable Collections dans Azure Service Fabric.

Même quand il est important de suivre le principe d’ignorance de la persistance pour votre modèle de domaine, vous ne devez pas ignorer les questions liées à la persistance. Il est toujours important de comprendre le modèle de données physique et la façon dont il est mappé à votre modèle objet d’entité. Dans le cas contraire, vous pouvez créer des conceptions impossibles.

En outre, cet aspect ne signifie pas que vous pouvez prendre un modèle conçu pour une base de données relationnelle et le déplacer directement vers une base de données NoSQL ou orientée document. Dans certains modèles d’entité, le modèle peut correspondre, mais ce n’est généralement pas le cas. Il existe toujours des contraintes que votre modèle d’entité doit respecter, basées sur les technologies de stockage et ORM.

### <a name="the-application-layer"></a>Couche d’application

En passant à la couche d’application, nous pouvons à nouveau citer le livre d’Eric Evans [Domain Driven Design](https://domainlanguage.com/ddd/) :

**Couche d’application :** définit les travaux que le logiciel est supposé effectuer et dirige les objets de domaine expressifs pour résoudre les problèmes. Les tâches dont cette couche est responsable sont significatives pour l’entreprise ou nécessaires pour l’interaction avec les couches d’application d’autres systèmes. Cette couche reste mince. Elle ne contient pas de règles métier ni de connaissances métier, mais coordonne uniquement les tâches et le travail des délégués pour les collaborations des objets de domaine dans la couche suivante. Elle ne présente pas d’état reflétant la situation de l’entreprise, mais peut avoir un état qui reflète la progression d’une tâche pour l’utilisateur ou le programme.

La couche d’application d’un microservice dans .NET est généralement codée comme un projet d’API Web ASP.NET Core. Le projet implémente l’interaction du microservice, l’accès réseau distant et les API Web externes utilisées à partir de l’interface utilisateur ou des applications clientes. Il inclut des requêtes dans le cadre d’une approche CQRS, des commandes acceptées par le microservice et même la communication pilotée par événements entre les microservices (événements d’intégration). L’API web ASP.NET Core qui représente la couche d’application ne doit pas contenir de règles métier ni de connaissances de domaine (notamment des règles de domaine pour les transactions ou les mises à jour) : celles-ci doivent appartenir à la bibliothèque de classes de modèle de domaine. La couche d’application doit uniquement coordonner les tâches et ne doit pas contenir ni définir d’état de domaine (modèle de domaine). Elle délègue l’exécution des règles métier aux classes de modèle de domaine (racines d’agrégat et entités de domaine) qui vont finalement mettre à jour les données au sein de ces entités de domaine.

En fait, la logique d’application est l’endroit où vous implémentez tous les cas d’usage qui dépendent d’un frontend donné, par exemple l’implémentation liée à un service API web.

L’objectif est que la logique de domaine dans la couche de modèle de domaine, ses invariants, le modèle de données et les règles métier associées soient complètement indépendants des couches de présentation et d’application. Surtout, la couche de modèle de domaine ne doit pas dépendre directement d’un framework d’infrastructure.

### <a name="the-infrastructure-layer"></a>Couche d’infrastructure

La couche d’infrastructure représente la façon dont les données qui sont initialement contenues dans les entités de domaine (en mémoire) sont conservées dans les bases de données ou un autre magasin persistant. Un exemple est l’utilisation de code Entity Framework Core pour implémenter les classes de modèle de dépôt qui utilisent un DBContext pour conserver les données dans une base de données relationnelle.

Conformément aux principes d’ignorance de la [persistance](https://deviq.com/persistence-ignorance/) et d’ignorance de l' [infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance) mentionnés précédemment, la couche d’infrastructure ne doit pas « contaminer » la couche de modèle de domaine. Les classes d’entité de modèle de domaine doivent rester étrangères à l’infrastructure qui vous permet de rendre persistantes des données (EF ou tout autre framework) en évitant les dépendances dures sur les frameworks. Votre bibliothèque de classes de couche de modèle de domaine doit avoir uniquement votre code de domaine, simplement des classes d’entité [OCT](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) qui implémentent le cœur de votre logiciel et qui sont complètement découplées des technologies d’infrastructure.

Ainsi, vos couches ou vos bibliothèques et projets de classes doivent au final s’appuyer sur votre couche de modèle de domaine (bibliothèque), et pas l’inverse, comme illustré dans la figure 7-7.

![Diagramme montrant les dépendances qui existent entre les couches de service de DDD.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Figure 7-7**. Dépendances entre les couches dans DDD

Dépendances dans un service de conception DDD : la couche Application dépend des couches Domaine et Infrastructure, la couche Infrastructure dépend de la couche Domaine, mais la couche Domaine ne dépend d’aucune couche. Cette conception de couche doit être indépendante pour chaque microservice. Comme indiqué précédemment, vous pouvez implémenter les microservices les plus complexes suivant des modèles DDD, tout en implémentant des microservices pilotés par des données plus simples (CRUD de base dans une couche unique) plus simplement.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **DevIQ. Principe d’ignorance de la persistance** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Ignorance de l’infrastructure** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Ange Lopez. Architecture en couches dans Domain-Driven conception** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Précédent](cqrs-microservice-reads.md) 
> [Suivant](microservice-domain-model.md)
