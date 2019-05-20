---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Découvrez les options qui permettent d’orchestrer des microservices et des applications multiconteneurs pour fournir une scalabilité et une disponibilité élevées. Découvrez également les possibilités offertes par Azure Dev Spaces durant le développement du cycle de vie des applications Kubernetes.
ms.date: 09/20/2018
ms.openlocfilehash: 3b7383f6153b787ce8bfad87e3902c34afba0fb2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644890"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité

L’utilisation d’orchestrateurs pour les applications prêtes pour la production est essentielle si votre application est basée sur des microservices ou si elle est simplement répartie entre plusieurs conteneurs. Comme expliqué précédemment, dans une approche basée sur les microservices, chaque microservice détient son modèle et ses données, ce qui le rend autonome du point de vue du développement et du déploiement. Toutefois, même si vous avez une application plus classique composée de plusieurs services (par exemple SOA), vous aurez également plusieurs conteneurs ou services constituant une même application métier, qui doivent être déployés en tant que système distribué. Ces types de systèmes sont complexes à monter en charge et à gérer : pour cette raison, vous avez absolument besoin d’un orchestrateur si vous voulez disposer d’une application multiconteneur prête pour la production et scalable.

La figure 4-23 illustre un déploiement dans un cluster d’une application composée de plusieurs microservices (conteneurs).

![Applications Docker composées dans un cluster : vous utilisez un conteneur pour chaque instance de service. Les conteneurs Docker sont des « unités de déploiement », et un conteneur est une instance de Docker. Un hôte gère de nombreux conteneurs.](./media/image23.png)

**Figure 4-23**. Un cluster de conteneurs

Ceci ressemble à une approche logique. Mais comment gérez-vous l’équilibrage de charge, le routage et l’orchestration de ces applications composées ?

Le moteur Docker standard dans des hôtes Docker individuels répond aux besoins de la gestion des instances avec une seule image sur un seul hôte, mais il ne peut pas faire face quand il s’agit de gérer plusieurs conteneurs déployés sur plusieurs hôtes pour des applications distribuées plus complexes. Dans la plupart des cas, vous avez besoin d’une plateforme de gestion qui va démarrer automatiquement les conteneurs, monter en charge les conteneurs avec plusieurs instances par image, les suspendre ou les arrêter si nécessaire, et idéalement, contrôler comment ils accèdent à des ressources comme le réseau et le stockage de données.

Pour aller au-delà de la gestion de conteneurs individuels ou d’applications composées très simples et passer à des applications d’entreprise plus grandes avec des microservices, vous devez faire appel à l’orchestration et au clustering des plateformes.

Du point de vue de l’architecture et du développement, si vous générez de grosses applications d’entreprise basées sur des microservices, il est important de comprendre les plateformes et les produits suivants, qui prennent en charge des scénarios avancés :

**Clusters et orchestrateurs.** Quand vous devez effectuer un scale-out des applications sur plusieurs hôtes Docker, comme dans le cas d’une application imposante basée sur des microservices, il est essentiel de pouvoir gérer tous ces hôtes sous la forme d’un seul cluster, en faisant abstraction de la complexité de la plateforme sous-jacente. C’est précisément ce que les clusters de conteneurs et les orchestrateurs permettent de faire. Azure Service Fabric et Kubernetes sont des exemples d’orchestrateurs. Kubernetes est disponible dans Azure via Azure Kubernetes Service.

**Planificateurs.** La *planification* signifie qu’un administrateur a la possibilité de lancer des conteneurs dans un cluster : ils doivent donc également fournir une interface utilisateur. Un planificateur de cluster a plusieurs responsabilités : utiliser efficacement les ressources du cluster, définir les contraintes fournies par l’utilisateur, équilibrer efficacement la charge des conteneurs entre les nœuds ou les hôtes, et faire preuve de robustesse face aux erreurs, tout en offrant une haute disponibilité.

Les concepts de cluster et de planificateur sont étroitement liés : les produits fournis par les différents fournisseurs offrent souvent les deux ensembles de fonctionnalités. La liste suivante montre les choix les plus importants pour les plateformes et les logiciels dont vous disposez pour les clusters et les planificateurs. Ces orchestrateurs sont généralement proposés dans des clouds publics comme Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plateformes logicielles pour le clustering, l’orchestration et la planification de conteneurs

### <a name="kubernetes"></a>Kubernetes

![Logo Kubernetes](./media/image24.png)

> [*Kubernetes*](https://kubernetes.io/) est un produit open source qui offre des fonctionnalités allant de l’infrastructure de cluster et la planification de conteneurs aux fonctionnalités d’orchestration. Il vous permet d’automatiser le déploiement, la mise à l’échelle et le fonctionnement de conteneurs d’application entre des clusters d’hôtes.
>
> *Kubernetes* fournit une infrastructure orientée conteneur, qui regroupe les conteneurs d’application dans des unités logiques pour en faciliter la gestion et la découverte.
>
> *Kubernetes* est suffisamment mature dans Linux, mais il l’est moins dans Windows.

### <a name="azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS)

![Logo Azure Kubernetes Service](./media/image41.png)

> [AKS (Azure Kubernetes Service)](https://azure.microsoft.com/services/kubernetes-service/) est un service managé d’orchestration de conteneur Kubernetes dans Azure, qui simplifie la gestion, le déploiement et les opérations liés au cluster Kubernetes.

### <a name="azure-service-fabric"></a>Azure Service Fabric

![Logo Azure Service Fabric](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) est une plateforme de microservices de Microsoft pour la création d’applications. Il s’agit d’un [orchestrateur](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de services, qui crée des clusters de machines. Service Fabric peut déployer des services en tant que conteneurs ou en tant que processus standard. Il peut même combiner des services dans des processus avec des services dans des conteneurs au sein de la même application et du même cluster.
>
> Vous pouvez déployer les clusters *Service Fabric* dans Azure, localement ou dans un cloud. Toutefois, le déploiement dans Azure est simplifié grâce à une approche managée.
>
> *Service Fabric* fournit des [modèles de programmation Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) supplémentaires prescriptifs et facultatifs, par exemple les [services avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> *Service Fabric* est suffisamment mature dans Windows (plusieurs années d’évolution dans Windows), mais il l’est moins dans Linux.
>
> Les conteneurs Linux et Windows sont pris en charge dans Service Fabric depuis 2017.

### <a name="azure-service-fabric-mesh"></a>Azure Service Fabric Mesh

![Logo Azure Service Fabric Mesh](./media/image35.png)

> [*Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) offre la même fiabilité, les mêmes performances critiques et la même scalabilité que Service Fabric, tout en proposant en plus une plateforme complètement managée et serverless. Vous n’avez pas besoin de gérer un cluster, des machines virtuelles, le stockage ou la configuration réseau. Vous vous concentrez uniquement sur le développement de votre application.
>
> *Service Fabric Mesh* prend en charge les conteneurs Windows et Linux, ce qui vous permet de développer avec le langage et le framework de programmation de votre choix.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Utilisation d’orchestrateurs basés sur des conteneurs dans Microsoft Azure

Plusieurs fournisseurs de cloud offrent la prise en charge des conteneurs Docker, ainsi que celle des clusters et de l’orchestration Docker, notamment Microsoft Azure, Amazon EC2 Container Service et Google Container Engine. Microsoft Azure fournit une prise en charge des clusters et des orchestrateurs Docker via Azure Kubernetes Service (AKS), Azure Service Fabric et Azure Service Fabric Mesh.

## <a name="using-azure-kubernetes-service"></a>Utilisation d’Azure Kubernetes Service

Un cluster Kubernetes regroupe plusieurs hôtes Docker et les expose sous la forme d’un seul hôte Docker virtuel. Vous pouvez donc déployer plusieurs conteneurs sur le cluster et effectuer un scale-out d’un nombre illimité d’instances de conteneurs. Le cluster prend en charge tous les détails complexes de la gestion, comme la scalabilité , l’intégrité, etc.

AKS offre un moyen de simplifier la création, la configuration et la gestion d’un cluster de machines virtuelles dans Azure. Ces machines virtuelles sont préconfigurées pour exécuter des applications conteneurisées. À l’aide d’une configuration optimisée d’outils open source courants de planification et d’orchestration, AKS vous permet d’utiliser vos compétences existantes ou de profiter de l’expertise importante et toujours croissante de la communauté pour déployer et gérer des applications conteneurisées sur Microsoft Azure.

Azure Kubernetes Service optimise la configuration des technologies et outils open source courants de clustering Docker spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour la configuration de votre application. Il vous suffit de sélectionner la taille, le nombre d’hôtes et les outils de l’orchestrateur, AKS gère tout le reste.

![Structure de cluster Kubernetes : il existe un nœud principal qui gère le système DNS, le planificateur, le proxy, etc., et plusieurs nœuds de travail, qui hébergent les conteneurs.](media/image36.png)

**Figure 4-24**. Structure et topologie simplifiées du cluster Kubernetes

Sur la figure 4-24, vous pouvez voir la structure d’un cluster Kubernetes où un nœud principal (machine virtuelle) contrôle la majeure partie de la coordination du cluster. Vous pouvez déployer des conteneurs sur le reste des nœuds, qui sont managés sous forme de pool unique du point de vue d’une application. De plus, vous pouvez effectuer un scale-out de milliers, voire de dizaines de milliers de conteneurs.

## <a name="development-environment-for-kubernetes"></a>Environnement de développement pour Kubernetes

Pour l’environnement de développement, [Docker a annoncé en juillet 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) que Kubernetes pouvait également s’exécuter sur une seule machine de développement (Windows 10 ou macOS) à condition simplement d’installer [Docker Desktop](https://docs.docker.com/install/). Vous pouvez ensuite effectuer un déploiement sur le cloud (AKS) pour d’autres tests d’intégration, comme indiqué sur la figure 4-25.

![Docker a annoncé la prise en charge des machines de développement pour les clusters Kubernetes en juillet 2018 avec Docker Desktop.](media/image37.png) 

**Figure 4-25**. Exécution de Kubernetes sur la machine de développement et dans le cloud

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Bien démarrer avec AKS (Azure Kubernetes Service) 

Pour commencer à utiliser AKS, vous devez déployer un cluster AKS à partir du Portail Azure ou à l’aide de l’interface CLI. Pour plus d’informations sur le déploiement d’un cluster Azure Container Service, consultez [Déployer un cluster AKS (Azure Kubernetes Service)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Aucun coût n’est facturé pour les logiciels installés par défaut dans le cadre d’AKS. Toutes les options par défaut sont implémentées avec des logiciels open source. AKS est disponible pour plusieurs machines virtuelles dans Azure. Vous payez seulement pour les instances de calcul que vous choisissez ainsi que pour les autres ressources de l’infrastructure sous-jacente consommées, comme le stockage et le réseau. Aucun coût supplémentaire n’est facturé pour AKS.

Pour plus d’informations sur l’implémentation du déploiement sur Kubernetes à partir de fichiers kubectl et .yaml d’origine, consultez le billet relatif à la [configuration d’eShopOnContainers dans AKS (Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Déploiement à l’aide de charts Helm sur des clusters Kubernetes

Durant le déploiement d’une application sur un cluster Kubernetes, vous pouvez utiliser l’outil CLI kubectl.exe d’origine et des fichiers de déploiement basés sur le format natif (fichiers .yaml), comme indiqué dans la section précédente. Toutefois, pour les applications Kubernetes plus complexes, par exemple quand vous déployez des applications de microservices complexes, il est recommandé d’utiliser [Helm](https://helm.sh/).

Les charts Helm facilitent la définition, la gestion de versions, l’installation, le partage, la mise à niveau ou la restauration des applications Kubernetes les plus complexes.

De plus, l’utilisation de Helm est également recommandée, car d’autres environnements Kubernetes dans Azure, par exemple [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces), sont également basés sur des charts Helm.

Helm est géré par le [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/), en collaboration avec Microsoft, Google, Bitnami et la communauté de contributeurs Helm.

Pour plus d’informations sur l’implémentation de charts Helm et de Kubernetes, consultez le billet relatif à l’[utilisation de charts Helm afin de déployer eShopOnContainers sur AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Utiliser Azure Dev Spaces pour le cycle de vie de votre application Kubernetes

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) fournit aux équipes une expérience de développement rapide et itérative de Kubernetes. Avec une configuration minimale de la machine de développement, vous pouvez exécuter et déboguer des conteneurs de manière itérative directement dans AKS (Azure Kubernetes Service). Développez sur Windows, Mac ou Linux à l’aide d’outils familiers, tels que Visual Studio et Visual Studio Code, ou à partir de la ligne de commande.

Comme cela a déjà été indiqué, Azure Dev Spaces utilise des charts Helm durant le déploiement d’applications conteneurisées.

Azure Dev Spaces permet aux équipes de développement d’être plus productives sur Kubernetes, car il permet d’itérer et de déboguer rapidement du code directement dans un cluster Kubernetes global au sein d’Azure, en utilisant simplement Visual Studio 2017 ou Visual Studio Code. Ce cluster Kubernetes dans Azure est un cluster Kubernetes managé partagé, ce qui permet à votre équipe de travailler de manière collaborative. Vous pouvez développer votre code de manière isolée, puis le déployer sur le cluster global et effectuer des tests de bout en bout avec d’autres composants sans réplication ou simulation des dépendances.

Comme indiqué sur la figure 4-26, la fonctionnalité la plus différenciée dans Azure Dev Spaces est la création d’« espaces » pouvant être intégrés au reste du déploiement global dans le cluster.

![Azure Dev Spaces peut mélanger et associer de manière transparente des microservices de production à une instance de conteneur de développement pour faciliter le test des nouvelles versions.](media/image38.png)

**Figure 4-26**. Utilisation de plusieurs espaces dans Azure Dev Spaces

Vous pouvez configurer un espace de développement partagé dans Azure. Chaque développeur peut se concentrer simplement sur sa partie de l’application et développer de manière itérative du code de prévalidation dans un espace de développement qui contient déjà tous les autres services et ressources cloud dont dépendent leurs scénarios. Les dépendances sont toujours à jour, et les développeurs travaillent comme en production.

Le concept d’espace propre à Azure Dev Spaces vous permet de travailler de manière relativement isolée sans craindre de perturber les membres de votre équipe. Chaque espace de développement fait partie d’une structure hiérarchique qui vous permet de remplacer un microservice (ou plusieurs), à partir de l’espace de développement principal « en haut », par votre microservice en cours d’élaboration.

Cette fonctionnalité est basée sur les préfixes d’URL. Par conséquent, lorsque vous utilisez un préfixe d’espace de développement dans l’URL, une requête est envoyée à partir du microservice cible s’il existe dans l’espace de développement. Dans le cas contraire, cette requête est transférée à la première instance du microservice cible trouvée dans la hiérarchie, pour éventuellement atteindre l’espace de développement principal en haut.

Vous pouvez voir la [page wiki d’eShopOnContainers sur Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS) pour obtenir un exemple concret.

Pour plus d’informations, consultez l’article sur le [développement en équipe avec Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Bien démarrer avec AKS (Azure Kubernetes Service)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** : site officiel. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Précédent](resilient-high-availability-microservices.md)
>[Suivant](using-azure-service-fabric.md)
