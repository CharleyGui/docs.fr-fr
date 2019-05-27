---
title: Utilisation d’Azure Service Fabric
description: Découvrez les modèles d’application Azure Service Fabric à utiliser, en plus de l’orchestration des conteneurs.
ms.date: 09/20/2018
ms.openlocfilehash: 3c629b473a429b64243b5756c96fef6585c939b7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644525"
---
# <a name="using-azure-service-fabric"></a>Utilisation d’Azure Service Fabric

Azure Service Fabric est né quand Microsoft est passé de la livraison de produits en coffret, qui étaient généralement de type monolithique, à la fourniture de services. La génération et l’exploitation de services à grande échelle, comme Azure SQL Database, Azure Cosmos DB, Azure Service Bus ou le back-end de Cortana, ont façonné Service Fabric. La plateforme a évolué au fil du temps car de plus en plus de services l’ont adoptée. Surtout, Service Fabric devait s’exécuter non seulement dans Azure, mais également dans des déploiements de Windows Server autonomes.

L’objectif de Service Fabric est de résoudre les difficiles problèmes de la création et de l’exécution d’un service, et de l’utilisation efficace des ressources de l’infrastructure, afin que les équipes puissent solutionner les problèmes métier en utilisant une approche par microservices.

Service Fabric fournit deux grands composants principaux pour vous aider à créer des applications qui utilisent une approche par microservices :

- Une plateforme qui fournit des services système pour déployer, mettre à l’échelle, mettre à niveau, détecter et redémarrer les services ayant connu une défaillance, découvrir l’emplacement des services, gérer les états et surveiller l’intégrité. Ces services système permettent de mettre en œuvre de nombreuses caractéristiques des microservices décrites précédemment.

- Des API ou frameworks de programmation pour vous aider à générer des applications en tant que microservices : [Reliable Actors et Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Vous pouvez choisir n’importe quel code pour générer votre microservice, mais ces API vous facilitent le travail et s’intègrent à la plateforme de façon plus étroite. De cette manière, vous pouvez obtenir des informations sur l’intégrité et les diagnostics, ou vous pouvez bénéficier d’une gestion fiable des états.

Service Fabric est agnostique quant à la façon dont vous créez votre service, et vous pouvez utiliser n’importe quelle technologie. Il fournit cependant des API de programmation intégrées qui facilitent la création de microservices.

Comme indiqué sur la figure 4-27, vous pouvez créer et exécuter des microservices dans Service Fabric en tant que simples processus ou en tant que conteneurs Docker. Il est également possible de combiner des microservices basés sur des conteneurs avec des microservices basés sur des processus dans le même cluster Service Fabric.

![Comparaison entre clusters Azure Service Fabric : microservices en tant que processus où chaque nœud exécute un processus pour chaque microservice ; microservices en tant que conteneurs où chaque nœud exécute Docker avec plusieurs conteneurs, à raison d’un conteneur par microservice.](./media/image30.png)

**Figure 4-27**. Déploiement de microservices en tant que processus ou en tant que conteneurs dans Azure Service Fabric

Les clusters Service Fabric basés sur des hôtes Linux et Windows peuvent exécuter des conteneurs Linux Docker et des conteneurs Windows, respectivement.

Pour obtenir des informations récentes sur la prise en charge des conteneurs dans Azure Service Fabric, consultez [Service Fabric et les conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric est un bon exemple d’une plateforme où vous pouvez définir une architecture logique (microservices métier ou contextes délimités) différente de l’implémentation physique, lesquelles ont été présentées dans la section [Architecture logique et architecture physique](logical-versus-physical-architecture.md). Par exemple, si vous implémentez des [services fiables avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction), qui sont présentés plus loin dans la section [Microservices sans état et avec état](#stateless-versus-stateful-microservices), vous pouvez avoir un concept de microservice métier avec plusieurs services physiques.

Comme indiqué sur la figure 4-28, en adoptant une perspective de microservice logique/métier, au moment de l’implémentation d’un service fiable avec état Service Fabric, vous devez généralement implémenter deux niveaux de services. Le premier est le service fiable avec état backend, qui gère plusieurs partitions (chaque partition est un service avec état). Le second est le service frontal, ou service de passerelle, en charge du routage et de l’agrégation des données entre plusieurs partitions ou instances de service avec état. Ce service de passerelle gère également la communication côté client avec des boucles de nouvelles tentatives pour l’accès au service back-end. Il est appelé service de passerelle si vous implémentez votre service personnalisé. Toutefois, vous pouvez également utiliser le [proxy inverse](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) fourni avec Service Fabric.

![](./media/image31.png)

**Figure 4-28**. Microservice métier avec plusieurs instances de service avec état et une passerelle personnalisée frontale

Dans tous les cas, quand vous utilisez des services fiables avec état Service Fabric, vous avez également un microservice (contexte délimité) logique ou métier, qui est généralement constitué de plusieurs services physiques. Chacun d’eux (service de passerelle et service de partition) peut être implémenté en tant que service d’API Web ASP.NET, comme indiqué sur la figure 4-28.

Dans Service Fabric, vous pouvez regrouper et déployer des groupes de services sous la forme d’une [application Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), qui est l’unité d’empaquetage et de déploiement pour l’orchestrateur ou le cluster. Ainsi, l’application Service Fabric peut également être mappée à cette limite de microservice logique et métier autonome (ou contexte délimité) : vous pouvez donc déployer ces services de façon autonome.

## <a name="service-fabric-and-containers"></a>Service Fabric et les conteneurs

Pour ce qui est des conteneurs dans Service Fabric, vous pouvez également déployer des services dans des images de conteneur au sein d’un cluster Service Fabric. Comme indiqué sur la figure 4-29, la plupart du temps, il n’y a qu’un seul conteneur par service.

![Une application Service Fabric peut exécuter plusieurs conteneurs accédant à une base de données externe. L’ensemble constitue la limite logique d’un microservice métier.](./media/image32.png)

**Figure 4-29**. Microservice métier avec plusieurs services (conteneurs) dans Service Fabric

Toutefois, les conteneurs appelés conteneurs « sidecar » (deux conteneurs qui doivent être déployés ensemble dans le cadre d’un service logique) sont également possibles dans Service Fabric. Le point essentiel est qu’un microservice métier est la limite logique autour de plusieurs éléments cohésifs. Dans de nombreux cas, il peut s’agit d’un seul service avec un seul modèle de données, mais dans d’autres cas, vous pouvez également avoir plusieurs services physiques.

Notez que vous pouvez combiner des services dans des processus et des services dans des conteneurs dans la même application Service Fabric, comme indiqué sur la figure 4-30.

![Application Service Fabric exécutant à la fois des services et des conteneurs dans le même nœud.](./media/image33.png)

**Figure 4-30**. Microservice métier mappé à une application Service Fabric avec des conteneurs et des services avec état

Pour plus informations sur la prise en charge des conteneurs dans Azure Service Fabric, consultez [Service Fabric et les conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microservices sans état et avec état

Comme mentionné précédemment, chaque microservice (contexte délimité logique) doit avoir son modèle de domaine (données et logique). Dans le cas de microservices sans état, les bases de données sont externes et utilisent des options relationnelles (par exemple SQL Server), ou des options NoSQL (par exemple Azure Cosmos DB ou MongoDB).

Cependant, les services eux-mêmes peuvent également être avec état dans Service Fabric, ce qui signifie que les données se trouvent dans le microservice. Ces données peuvent exister non seulement sur le même serveur, mais aussi dans le processus du microservice et en mémoire, et être conservées sur des disques durs et répliquées sur d’autres nœuds. La figure 4-30 montre les différentes approches.

![Dans les services sans état, l’état (persistance, base de données) est conservé en dehors du microservice. Dans les services avec état, les états sont conservés dans le microservice.](./media/image34.png)

**Figure 4-31**. Microservices sans état et avec état

Une approche sans état est parfaitement valide et est plus facile à implémenter que des microservices avec état, car cette approche est similaire aux modèles traditionnels bien connus. Les microservices sans état imposent cependant de la latence entre les processus et les sources de données. Ils impliquent également le déplacement d’un plus grand nombre d’éléments quand vous essayez d’améliorer le niveau de performance avec des caches et des files d’attente supplémentaires. Le résultat est que vous pouvez vous retrouver avec des architectures complexes qui ont trop de niveaux.

En revanche, les [microservices avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peuvent exceller dans les scénarios avancés, car il n’existe aucune latence entre la logique et les données du domaine. Les traitements de données lourds, les back-end de jeux, les bases de données en tant que service et tous les autres scénarios avec une latence faible tirent parti des services avec état, qui permettent un état local pour un accès plus rapide.

Les services sans état et avec état sont complémentaires. Par exemple, vous pouvez voir dans la figure 4-31, dans le diagramme de droite, qu’un service avec état peut être divisé en plusieurs partitions. Pour accéder à ces partitions, vous pouvez avoir besoin d’un service sans état agissant comme un service de passerelle, qui sait comment atteindre chaque partition en fonction de clés de partition.

Les services avec état présentent des inconvénients. Ils imposent un niveau de complexité qui permet la montée en charge. Les fonctionnalités qui seraient habituellement implémentées par des systèmes de base de données externes doivent être fournies pour des tâches comme la réplication des données entre des microservices avec état et le partitionnement des données. C’est un des domaines où un orchestrateur comme [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) avec ses [services fiables avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peut être le plus utile, en simplifiant le développement et le cycle de vie des microservices avec état grâce à [l’API Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Les autres frameworks de microservices qui permettent les services avec état, qui prennent en charge le modèle d’acteur et qui améliorent la tolérance de panne et la latence entre la logique métier et les données sont Microsoft [Orléans](https://github.com/dotnet/orleans) de Microsoft Research et [Akka.NET](https://getakka.net/). Les deux frameworks améliorent actuellement leur prise en charge de Docker.

Notez que les conteneurs Docker sont eux-mêmes sans état. Si vous voulez implémenter un service avec état, vous avez besoin d’un des frameworks normatifs et de plus haut niveau supplémentaires précédemment indiqués.

## <a name="using-azure-service-fabric-mesh"></a>Utilisation d’Azure Service Fabric Mesh 

Azure Service Fabric Mesh est un service complètement managé qui permet aux développeurs de générer et déployer des applications critiques sans avoir à gérer d’infrastructures. Utilisez Service Fabric Mesh pour générer et exécuter des applications de microservices sécurisées, distribuées et scalables à la demande. 

Comme indiqué sur la figure 4-32, les applications hébergées sur Service Fabric Mesh s’exécutent et sont scalables sans que vous ayez à vous soucier de l’infrastructure sous-jacente.

![Vous pouvez déployer une application multiconteneur s’exécutant dans Docker Desktop sur Azure Service Fabric Mesh sans vous soucier de l’infrastructure.](media/image39.png)

**Figure 4-32**. Déploiement d’une application basée sur des microservices/conteneurs sur Service Fabric Mesh

Service Fabric Mesh est constitué de clusters de milliers de machines. Toutes les opérations de cluster sont masquées pour le développeur. Il vous suffit simplement de charger vos conteneurs et de spécifier les ressources nécessaires, leurs exigences de disponibilité et leurs limites. Service Fabric Mesh alloue automatiquement l’infrastructure nécessaire au déploiement de votre application. Il gère également les défaillances de l’infrastructure, ce qui permet ainsi de garantir la haute disponibilité de vos applications. Vous devez uniquement vous soucier de l’intégrité et de la réactivité de votre application, et non de l’infrastructure.

Pour plus d’informations, consultez la [documentation relative à Service Fabric Mesh](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Choix des orchestrateurs dans Azure

Le tableau suivant fournit une aide sur le type d’orchestrateur à utiliser en fonction des charges de travail et du focus du système d’exploitation.

![Azure Kubernetes Service est plus mature sur Linux que sur Windows. Il est principalement utilisé pour le déploiement de microservices basés sur des conteneurs. Azure Service Fabric (clusters et maillages) est plus mature sur Windows que sur Linux. Il est généralement utilisé pour les microservices basés sur des conteneurs, les microservices basés sur des processus simples et les services avec état.](media/image40.png)

**Figure 4-33**. Sélection de l’orchestrateur dans l’aide d’Azure

>[!div class="step-by-step"]
>[Précédent](scalable-available-multi-container-microservice-applications.md)
>[Suivant](../docker-application-development-process/index.md)
