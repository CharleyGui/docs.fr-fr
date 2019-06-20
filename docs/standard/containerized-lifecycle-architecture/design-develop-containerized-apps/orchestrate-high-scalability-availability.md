---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Les véritables applications de production doivent être déployées et gérées avec des orchestrateurs qui gèrent l’intégrité, la charge de travail et les cycles de vie de tous les conteneurs.
ms.date: 02/15/2019
ms.openlocfilehash: bde9a2815d0496608b3172582481c169cab37f04
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "66195651"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité

L’utilisation d’orchestrateurs pour les applications prêtes pour la production est essentielle si votre application est basée sur des microservices ou si elle est répartie entre plusieurs conteneurs. Comme expliqué précédemment, dans une approche basée sur les microservices, chaque microservice détient son modèle et ses données, ce qui le rend autonome du point de vue du développement et du déploiement. Toutefois, même si vous avez une application plus classique composée de plusieurs services (par exemple SOA), vous aurez également plusieurs conteneurs ou services constituant une même application métier, qui doivent être déployés en tant que système distribué. Ces types de systèmes sont complexes à monter en charge et à gérer : pour cette raison, vous avez absolument besoin d’un orchestrateur si vous voulez disposer d’une application multiconteneur prête pour la production et scalable.

La figure 4-6 illustre un déploiement dans un cluster d’une application composée de plusieurs microservices (conteneurs).

![Applications Docker composées dans un cluster : vous utilisez un conteneur pour chaque instance de service. Les conteneurs Docker sont des « unités de déploiement », et un conteneur est une instance de Docker. Un hôte gère de nombreux conteneurs.](./media/image6.png)

**Figure 4-6**. Un cluster de conteneurs

Ceci ressemble à une approche logique. Mais comment gérez-vous l’équilibrage de charge, le routage et l’orchestration de ces applications composées ?

Si l’interface de ligne de commande (CLI) Docker répond parfaitement aux besoins de gestion d’un conteneur unique sur un seul hôte, elle ne peut pas faire face quand il s’agit de gérer plusieurs conteneurs déployés sur plusieurs hôtes pour des applications distribuées plus complexes. Dans la plupart des cas, vous avez besoin d’une plateforme de gestion capable de démarrer automatiquement les conteneurs, d’effectuer le scale-out des conteneurs avec plusieurs instances par image, de les suspendre ou les arrêter si nécessaire, et idéalement, de contrôler la façon dont ils accèdent à des ressources comme le réseau et le stockage de données.

Pour aller au-delà de la gestion de conteneurs individuels ou d’applications composées simples et passer à des applications d’entreprise de plus grande envergure avec des microservices, vous devez vous tourner vers des plateformes d’orchestration et de clustering.

Du point de vue de l’architecture et du développement, si vous créez de grosses applications d’entreprise basées sur des microservices, il est important de comprendre les plateformes et les produits suivants, qui prennent en charge des scénarios avancés :

- **Clusters et orchestrateurs.** Quand vous devez effectuer le scale-out d’applications sur plusieurs hôtes Docker, comme dans le cas d’une application d’envergure basée sur des microservices, il est essentiel de pouvoir gérer tous ces hôtes en tant que cluster unique, en faisant abstraction de la complexité de la plateforme sous-jacente. C’est précisément ce que les clusters de conteneurs et les orchestrateurs permettent de faire. Azure Service Fabric et Kubernetes sont des exemples d’orchestrateurs. Kubernetes est disponible dans Azure via Azure Kubernetes Service.

- **Planificateurs.** Pour un administrateur, *planifier* signifie pouvoir lancer des conteneurs dans un cluster. Autrement dit, les planificateurs proposent aussi une interface utilisateur pour leur permettre de le faire. Un planificateur de cluster a plusieurs responsabilités : utiliser efficacement les ressources du cluster, définir les contraintes fournies par l’utilisateur, équilibrer efficacement la charge des conteneurs entre les nœuds ou les hôtes, et faire preuve de robustesse face aux erreurs, tout en offrant une haute disponibilité.

Les concepts de cluster et de planificateur sont étroitement liés : les produits fournis par les différents fournisseurs offrent souvent les deux ensembles de fonctionnalités. La section ci-dessous présente les choix les plus importants en matière de plateformes et de logiciels pour les clusters et les planificateurs. Ces orchestrateurs sont couramment proposés dans les clouds publics comme Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plateformes logicielles pour le clustering, l’orchestration et la planification de conteneurs

| Plateforme | Commentaires |
|:---:|:---|
| **Kubernetes** <br/> ![Logo Kubernetes](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) est un produit open source qui offre des fonctionnalités allant de l’infrastructure de cluster et la planification de conteneurs aux fonctionnalités d’orchestration. Il vous permet d’automatiser le déploiement, la mise à l’échelle et le fonctionnement de conteneurs d’application entre des clusters d’hôtes. <br/> <br/> *Kubernetes* fournit une infrastructure orientée conteneur, qui regroupe les conteneurs d’application dans des unités logiques pour en faciliter la gestion et la découverte. <br/> <br/> *Kubernetes* est suffisamment mature dans Linux, mais il l’est moins dans Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Logo Azure Kubernetes Service](./media/aks-logo.png) | [AKS (Azure Kubernetes Service)](https://azure.microsoft.com/services/kubernetes-service/) est un service managé d’orchestration de conteneur Kubernetes dans Azure, qui simplifie la gestion, le déploiement et les opérations liés au cluster Kubernetes. |
| **Azure Service Fabric** <br/> ![Logo Azure Service Fabric](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) est une plateforme de microservices de Microsoft pour la création d’applications. Il s’agit d’un [orchestrateur](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de services, qui crée des clusters de machines. Service Fabric peut déployer des services en tant que conteneurs ou en tant que processus standard. Il peut même combiner des services dans des processus avec des services dans des conteneurs au sein de la même application et du même cluster. <br/> <br/> Vous pouvez déployer les clusters *Service Fabric* dans Azure, localement ou dans un cloud. Toutefois, le déploiement dans Azure est simplifié grâce à une approche managée. <br/> <br/> *Service Fabric* fournit des [modèles de programmation Service Fabric](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) supplémentaires prescriptifs et facultatifs, par exemple les [services avec état](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) et [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/). <br/> <br/> *Service Fabric* est suffisamment mature dans Windows (plusieurs années d’évolution dans Windows), mais il l’est moins dans Linux. <br/> <br/> Les conteneurs Linux et Windows sont pris en charge dans Service Fabric depuis 2017. |
| **Azure Service Fabric Mesh** <br/> ![Logo Azure Service Fabric Mesh](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) offre la même fiabilité, les mêmes performances critiques et la même scalabilité que Service Fabric, tout en proposant en plus une plateforme complètement managée et serverless. Vous n’avez pas besoin de gérer un cluster, des machines virtuelles, le stockage ou la configuration réseau. Vous vous concentrez uniquement sur le développement de votre application. <br/> <br/> *Service Fabric Mesh* prend en charge les conteneurs Windows et Linux, ce qui vous permet de développer avec le langage et le framework de programmation de votre choix.

## <a name="using-container-based-orchestrators-in-azure"></a>Utilisation d’orchestrateurs basés sur des conteneurs dans Azure

Plusieurs fournisseurs de cloud offrent la prise en charge des conteneurs Docker, ainsi que celle des clusters et de l’orchestration Docker, notamment Azure, Amazon EC2 Container Service et Google Container Engine. Azure assure la prise en charge des clusters et des orchestrateurs Docker via Azure Kubernetes Service (AKS), Azure Service Fabric et Azure Service Fabric Mesh.

## <a name="using-azure-kubernetes-service"></a>Utilisation d’Azure Kubernetes Service

Un cluster Kubernetes regroupe plusieurs hôtes Docker et les expose sous la forme d’un seul hôte Docker virtuel. Vous pouvez donc déployer plusieurs conteneurs sur le cluster et effectuer un scale-out avec un nombre illimité d’instances de conteneurs. Le cluster prend en charge tous les détails complexes de la gestion, comme la scalabilité , l’intégrité, etc.

AKS offre un moyen de simplifier la création, la configuration et la gestion d’un cluster de machines virtuelles dans Azure. Ces machines virtuelles sont préconfigurées pour exécuter des applications conteneurisées. À l’aide d’une configuration optimisée d’outils open source courants de planification et d’orchestration, AKS vous permet d’utiliser vos compétences existantes ou de profiter de l’expertise importante et toujours croissante de la communauté pour déployer et gérer des applications conteneurisées sur Microsoft Azure.

Azure Kubernetes Service optimise la configuration des technologies et outils open source courants de clustering Docker spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour la configuration de votre application. Il vous suffit de sélectionner la taille, le nombre d’hôtes et les outils de l’orchestrateur, AKS gère tout le reste.

![Structure de cluster Kubernetes : il existe un nœud principal qui gère le système DNS, le planificateur, le proxy, etc., et plusieurs nœuds de travail, qui hébergent les conteneurs.](media/image36.png)

**Figure 4-7**. Structure et topologie simplifiées du cluster Kubernetes

La figure 4-7 illustre la structure d’un cluster Kubernetes dans lequel un nœud principal (machine virtuelle) contrôle la majeure partie de la coordination du cluster. Vous pouvez déployer des conteneurs sur le reste des nœuds, qui sont managés comme un pool unique du point de vue d’une application. Cela vous permet d’effectuer une mise à l’échelle avec des milliers, voire des dizaines de milliers de conteneurs.

## <a name="development-environment-for-kubernetes"></a>Environnement de développement pour Kubernetes

Dans l’environnement de développement que [Docker a annoncé en juillet 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), Kubernetes peut aussi s’exécuter sur une seule machine de développement (Windows 10 ou macOS) en installant simplement [Docker Desktop](https://www.docker.com/community-edition). Vous pouvez ensuite effectuer un déploiement sur le cloud (AKS) pour d’autres tests d’intégration, comme illustré dans la figure 4-8.

![Docker a annoncé la prise en charge des machines de développement pour les clusters Kubernetes en juillet 2018 avec Docker Desktop.](media/kubernetes-development-environment.png)

**Figure 4-8**. Exécution de Kubernetes sur la machine de développement et dans le cloud

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Bien démarrer avec AKS (Azure Kubernetes Service)

Pour commencer à utiliser AKS, vous devez déployer un cluster AKS à partir du Portail Azure ou à l’aide de l’interface de ligne de commande. Pour plus d’informations sur le déploiement d’un cluster Kubernetes dans Azure, consultez [Déployer un cluster AKS (Azure Kubernetes Service)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Aucun coût n’est facturé pour les logiciels installés par défaut dans le cadre d’AKS. Toutes les options par défaut sont implémentées avec des logiciels open source. AKS est disponible pour plusieurs machines virtuelles dans Azure. Vous payez seulement pour les instances de calcul que vous choisissez ainsi que pour les autres ressources de l’infrastructure sous-jacente consommées, comme le stockage et le réseau. Aucun coût supplémentaire n’est facturé pour AKS.

Pour plus d’informations sur l’implémentation du déploiement sur Kubernetes à partir de fichiers `kubectl` et `.yaml` d’origine, consultez le billet relatif à la [configuration d’eShopOnContainers dans AKS (Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Déployer à l’aide de charts Helm sur des clusters Kubernetes

Durant le déploiement d’une application sur un cluster Kubernetes, vous pouvez utiliser l’outil CLI `kubectl.exe` d’origine et des fichiers de déploiement basés sur le format natif (fichiers `.yaml`), comme indiqué dans la section précédente. Toutefois, pour les applications Kubernetes plus complexes, par exemple quand vous déployez des applications de microservices complexes, il est recommandé d’utiliser [Helm](https://helm.sh/).

Les charts Helm facilitent la définition, la gestion de versions, l’installation, le partage, la mise à niveau ou la restauration des applications Kubernetes les plus complexes.

De plus, l’utilisation de Helm est également recommandée, car d’autres environnements Kubernetes dans Azure, par exemple [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces), sont également basés sur des charts Helm.

Helm est géré par le [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) en collaboration avec Microsoft, Google, Bitnami et la communauté de contributeurs Helm.

Pour plus d’informations sur l’implémentation de charts Helm et de Kubernetes, consultez le billet relatif à l’[utilisation de charts Helm afin de déployer eShopOnContainers sur AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Utiliser Azure Dev Spaces pour le cycle de vie de votre application Kubernetes

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) fournit aux équipes une expérience de développement rapide et itérative de Kubernetes. Avec une configuration minimale de la machine de développement, vous pouvez exécuter et déboguer des conteneurs de manière itérative directement dans AKS (Azure Kubernetes Service). Vous pouvez développer sur Windows, Mac ou Linux à l’aide d’outils familiers comme Visual Studio et Visual Studio Code ou à partir de la ligne de commande.

Comme cela a déjà été indiqué, Azure Dev Spaces utilise des charts Helm durant le déploiement d’applications basées sur des conteneurs.

Azure Dev Spaces permet aux équipes de développement d’être plus productives sur Kubernetes, car il permet d’itérer et de déboguer rapidement du code directement dans un cluster Kubernetes global au sein d’Azure en utilisant simplement Visual Studio 2017 ou Visual Studio Code. Ce cluster Kubernetes dans Azure est un cluster Kubernetes managé partagé, ce qui permet à votre équipe de travailler de manière collaborative. Vous pouvez développer votre code de manière isolée, puis le déployer sur le cluster global et effectuer des tests de bout en bout avec d’autres composants sans réplication ou simulation des dépendances.

Comme le montre la figure 4-9, la fonctionnalité la plus distinctive d’Azure Dev Spaces est celle qui permet de créer des « espaces » pouvant être intégrés au reste du déploiement global dans le cluster.

![Azure Dev Spaces peut mélanger et associer de manière transparente des microservices de production à une instance de conteneur de développement pour faciliter le test des nouvelles versions.](media/image38.png)

**Figure 4-9**. Utilisation de plusieurs espaces dans Azure Dev Spaces

Azure vous permet avant tout de configurer un espace de développement partagé. Chaque développeur peut se concentrer simplement sur sa partie de l’application et développer de manière itérative du code « prévalidé » dans un espace de développement qui contient déjà tous les autres services et ressources cloud dont dépendent leurs scénarios. Les dépendances sont toujours à jour, et les développeurs travaillent comme en production.

Le concept d’espace propre à Azure Dev Spaces vous permet de travailler de manière isolée sans craindre de perturber les membres de votre équipe. Cette fonctionnalité est basée sur des préfixes d’URL ; si vous utilisez un préfixe d’espace de développement dans l’URL d’une demande de conteneur, Azure Dev Spaces exécute une version spéciale du conteneur qui est déployé pour cet espace, s’il en existe un. Sinon, la version globale/regroupée est exécutée.

Vous pouvez consulter la [page wiki d’eShopOnContainers sur Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) pour obtenir un exemple concret.

Pour plus d’informations, consultez l’article sur le [développement en équipe avec Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Bien démarrer avec AKS (Azure Kubernetes Service)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Le site officiel. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Utilisation d’Azure Service Fabric

Azure Service Fabric est né quand Microsoft est passé de la livraison de produits en boîte, qui étaient généralement de type monolithique, à la fourniture de services. La création et l’exploitation de services à grande échelle, comme Azure SQL Database, Azure Cosmos DB, Azure Service Bus ou le backend de Cortana, ont façonné Service Fabric. La plateforme a évolué au fil du temps car de plus en plus de services l’ont adoptée. Surtout, Service Fabric devait s’exécuter non seulement dans Azure, mais également dans des déploiements de Windows Server autonomes.

L’objectif de Service Fabric est de résoudre les difficiles problèmes de la création et de l’exécution d’un service, et de l’utilisation efficace des ressources de l’infrastructure, afin que les équipes puissent solutionner les problèmes métier en utilisant une approche par microservices.

Service Fabric fournit deux grands composants principaux pour vous aider à créer des applications qui utilisent une approche par microservices :

- Une plateforme qui fournit des services système pour déployer, mettre à l’échelle, mettre à niveau, détecter et redémarrer les services ayant connu une défaillance, découvrir l’emplacement des services, gérer les états et surveiller l’intégrité. Ces services système permettent de mettre en œuvre de nombreuses caractéristiques des microservices décrites précédemment.

- Des API de programmation, ou frameworks, pour vous aider à créer des applications en tant que microservices : [des acteurs fiables et des services fiables](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Vous pouvez choisir n’importe quel code pour générer votre microservice, mais ces API vous facilitent le travail et s’intègrent à la plateforme de façon plus étroite. De cette manière, vous pouvez obtenir des informations sur l’intégrité et les diagnostics, ou vous pouvez bénéficier d’une gestion fiable des états.

Service Fabric est agnostique quant à la façon dont vous créez votre service, et vous pouvez utiliser n’importe quelle technologie. Il fournit cependant des API de programmation intégrées qui facilitent la création de microservices.

Comme le montre la figure 4-10, vous pouvez créer et exécuter des microservices dans Service Fabric en tant que processus simples ou en tant que conteneurs Docker. Il est également possible de combiner des microservices basés sur des conteneurs avec des microservices basés sur des processus dans le même cluster Service Fabric.

![Comparaison entre clusters Azure Service Fabric : microservices en tant que processus où chaque nœud exécute un processus pour chaque microservice ; microservices en tant que conteneurs où chaque nœud exécute Docker avec plusieurs conteneurs, à raison d’un conteneur par microservice.](./media/azure-service-fabric-cluster-types.png)

**Figure 4-10**. Déploiement de microservices en tant que processus ou en tant que conteneurs dans Azure Service Fabric

Les clusters Service Fabric basés sur des hôtes Linux et Windows peuvent exécuter des conteneurs Linux Docker et des conteneurs Windows, respectivement.

Pour obtenir des informations récentes sur la prise en charge des conteneurs dans Azure Service Fabric, consultez [Service Fabric et les conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric est un bon exemple de plateforme dans laquelle vous pouvez définir une architecture logique (microservices métier ou contextes délimités) différente de l’implémentation physique. Par exemple, si vous implémentez des [services fiables avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) dans [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), qui sont présentés dans la section suivante « [Microservices sans état et avec état](#stateless-versus-stateful-microservices) », vous pouvez avoir un concept de microservice métier avec plusieurs services physiques.

Comme le montre la figure 4-10, en adoptant une perspective de microservice logique/métier, quand il s’agit d’implémenter un service fiable avec état Service Fabric, vous devez généralement implémenter deux niveaux de services. Le premier est le service fiable avec état backend, qui gère plusieurs partitions (chaque partition est un service avec état). Le second est le service frontal, ou service de passerelle, en charge du routage et de l’agrégation des données entre plusieurs partitions ou instances de service avec état. Ce service de passerelle gère également la communication côté client avec des boucles de nouvelles tentatives pour l’accès au service back-end. Il est appelé service de passerelle si vous implémentez votre service personnalisé. Toutefois, vous pouvez également utiliser le [proxy inverse](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) fourni avec Service Fabric.

![Service Fabric a pour prescription de prendre en charge plusieurs services fiables avec état dans des conteneurs.](./media/service-fabric-stateful-business-microservice.png)

**Figure 4-11**. Microservice métier avec plusieurs instances de service avec état et une passerelle personnalisée front-end

Dans tous les cas, quand vous utilisez des services fiables avec état Service Fabric, vous avez aussi un microservice (contexte délimité) logique ou métier, qui est constitué de plusieurs services physiques. Chacun d’eux (service de passerelle et service de partition) peut être implémenté en tant que service d’API Web ASP.NET, comme le montre la figure 4-11.

Dans Service Fabric, vous pouvez regrouper et déployer des groupes de services sous la forme d’une [application Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), qui est l’unité d’empaquetage et de déploiement pour l’orchestrateur ou le cluster. Ainsi, l’application Service Fabric peut également être mappée à cette limite de microservice logique et métier autonome (ou contexte délimité) : vous pouvez donc déployer ces services de façon autonome.

### <a name="service-fabric-and-containers"></a>Service Fabric et les conteneurs

Pour ce qui est des conteneurs dans Service Fabric, vous pouvez également déployer des services dans des images de conteneur au sein d’un cluster Service Fabric. Comme le montre la figure 4-12, la plupart du temps, il n’y a qu’un seul conteneur par service.

![Une application Service Fabric peut exécuter plusieurs conteneurs accédant à une base de données externe. L’ensemble constitue la limite logique d’un microservice métier.](./media/azure-service-fabric-business-microservice.png)

**Figure 4-12**. Microservice métier avec plusieurs services (conteneurs) dans Service Fabric

Toutefois, les conteneurs appelés conteneurs « sidecar » (deux conteneurs qui doivent être déployés ensemble dans le cadre d’un service logique) sont également possibles dans Service Fabric. Le point essentiel est qu’un microservice métier est la limite logique autour de plusieurs éléments cohésifs. Dans de nombreux cas, il peut s’agit d’un seul service avec un seul modèle de données, mais dans d’autres cas, vous pouvez également avoir plusieurs services physiques.

Notez que vous pouvez combiner des services dans des processus et des services dans des conteneurs dans une même application Service Fabric, comme le montre la figure 4-13.

![Application Service Fabric exécutant à la fois des services et des conteneurs dans le même nœud.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Figure 4-13**. Microservice métier mappé à une application Service Fabric avec des conteneurs et des services avec état

Pour plus informations sur la prise en charge des conteneurs dans Azure Service Fabric, consultez [Service Fabric et les conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microservices sans état et avec état

Comme mentionné précédemment, chaque microservice (contexte délimité logique) doit avoir son modèle de domaine (données et logique). Dans le cas de microservices sans état, les bases de données sont externes et utilisent des options relationnelles (par exemple SQL Server), ou des options NoSQL (par exemple Azure Cosmos DB ou MongoDB).

Cependant, les services eux-mêmes peuvent également être avec état dans Service Fabric, ce qui signifie que les données se trouvent dans le microservice. Ces données peuvent exister non seulement sur le même serveur, mais aussi dans le processus du microservice et en mémoire, et être conservées sur des disques durs et répliquées sur d’autres nœuds. La figure 4-30 montre les différentes approches.

![Dans les services sans état, l’état (persistance, base de données) est maintenu à l’extérieur du microservice. Dans les services avec état, l’état est maintenu à l’intérieur du microservice.](./media/stateless-vs-stateful-microservices.png)

**Figure 4-14**. Microservices sans état et avec état

Une approche sans état est parfaitement valide et est plus facile à implémenter que des microservices avec état, car cette approche est similaire aux modèles traditionnels bien connus. Les microservices sans état imposent cependant de la latence entre les processus et les sources de données. Ils impliquent également le déplacement d’un plus grand nombre d’éléments quand vous essayez d’améliorer le niveau de performance avec des caches et des files d’attente supplémentaires. Le résultat est que vous pouvez vous retrouver avec des architectures complexes qui ont trop de niveaux.

En revanche, les [microservices avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peuvent exceller dans les scénarios avancés, car il n’existe aucune latence entre la logique et les données du domaine. Les traitements de données lourds, les back-end de jeux, les bases de données en tant que service et tous les autres scénarios avec une latence faible tirent parti des services avec état, qui permettent un état local pour un accès plus rapide.

Les services sans état et avec état sont complémentaires. Par exemple, comme vous pouvez le voir dans le diagramme de droite de la figure 4-31, un service avec état peut être divisé en plusieurs partitions. Pour accéder à ces partitions, vous pouvez avoir besoin d’un service sans état agissant comme un service de passerelle, qui sait comment atteindre chaque partition en fonction de clés de partition.

Les services avec état présentent des inconvénients. Leur scale-out impose un haut niveau de complexité. Les fonctionnalités qui seraient habituellement implémentées par des systèmes de base de données externes doivent être fournies pour des tâches comme la réplication des données entre des microservices avec état et le partitionnement des données. C’est un des domaines où un orchestrateur comme [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) avec ses [services fiables avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peut être le plus utile, en simplifiant le développement et le cycle de vie des microservices avec état grâce à [l’API Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Les autres frameworks de microservices qui permettent les services avec état, qui prennent en charge le modèle d’acteur et qui améliorent la tolérance de panne et la latence entre la logique métier et les données sont Microsoft [Orléans](https://github.com/dotnet/orleans) de Microsoft Research et [Akka.NET](https://getakka.net/). Les deux frameworks améliorent actuellement leur prise en charge de Docker.

Ne perdez pas de vue que les conteneurs Docker sont eux-mêmes sans état. Si vous voulez implémenter un service avec état, vous avez besoin d’un des frameworks normatifs et de plus haut niveau supplémentaires précédemment indiqués.

## <a name="using-azure-service-fabric-mesh"></a>Utilisation d’Azure Service Fabric Mesh

Azure Service Fabric Mesh est un service complètement managé qui permet aux développeurs de générer et déployer des applications critiques sans avoir à gérer une quelconque infrastructure. Utilisez Service Fabric Mesh pour générer et exécuter des applications de microservices sécurisées, distribuées et scalables à la demande.

Comme le montre la figure 4-15, vous pouvez exécuter et mettre à l’échelle les applications hébergées sur Service Fabric Mesh sans avoir à vous soucier de l’infrastructure sous-jacente.

![Vous pouvez déployer une application multiconteneur s’exécutant dans Docker Desktop sur Azure Service Fabric Mesh sans avoir à vous soucier de l’infrastructure.](media/image39.png)

**Figure 4-15**. Déploiement d’une application basée sur des microservices/conteneurs sur Service Fabric Mesh

Service Fabric Mesh est constitué de clusters de milliers de machines. Toutes les opérations de cluster sont masquées pour le développeur. Il vous suffit simplement de charger vos conteneurs et de spécifier les ressources nécessaires, leurs exigences de disponibilité et leurs limites. Service Fabric Mesh alloue automatiquement l’infrastructure nécessaire au déploiement de votre application. Il gère également les défaillances de l’infrastructure, ce qui permet ainsi de garantir la haute disponibilité de vos applications. Vous devez uniquement vous soucier de l’intégrité et de la réactivité de votre application, et non de l’infrastructure.

Pour plus d’informations, consultez la [documentation relative à Service Fabric Mesh](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Choix des orchestrateurs dans Azure

Le tableau suivant fournit une aide sur le type d’orchestrateur à utiliser en fonction des charges de travail et du focus du système d’exploitation.

![Azure Kubernetes Service est plus mature sur Linux que sur Windows. Il est principalement utilisé pour le déploiement de microservices basés sur des conteneurs. Azure Service Fabric (clusters et maillages) est plus mature sur Windows que sur Linux. Il est généralement utilisé pour les microservices basés sur des conteneurs, les microservices basés sur des processus simples et les services avec état.](media/image40.png)

**Figure 4-16**. Sélection de l’orchestrateur dans l’aide d’Azure

>[!div class="step-by-step"]
>[Précédent](soa-applications.md)
>[Suivant](deploy-azure-kubernetes-service.md)
