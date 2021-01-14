---
title: Orchestrer des microservices et des applications multiconteneurs pour un haut niveau de scalabilité et de disponibilité
description: Découvrez les options qui permettent d’orchestrer des microservices et des applications multiconteneurs pour fournir une scalabilité et une disponibilité élevées. Découvrez également les possibilités offertes par Azure Dev Spaces durant le développement du cycle de vie des applications Kubernetes.
ms.date: 01/13/2021
ms.openlocfilehash: 7ba0367bca98edbab1be2059ee37e863359edad3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189414"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrer des microservices et des applications multiconteneurs pour un haut niveau de scalabilité et de disponibilité

L’utilisation d’orchestrateurs pour les applications prêtes pour la production est essentielle si votre application est basée sur des microservices ou si elle est simplement répartie entre plusieurs conteneurs. Comme expliqué précédemment, dans une approche basée sur les microservices, chaque microservice détient son modèle et ses données, ce qui le rend autonome du point de vue du développement et du déploiement. Toutefois, même si vous avez une application plus classique composée de plusieurs services (par exemple SOA), vous aurez également plusieurs conteneurs ou services constituant une même application métier, qui doivent être déployés en tant que système distribué. Ces types de systèmes sont complexes à monter en charge et à gérer : pour cette raison, vous avez absolument besoin d’un orchestrateur si vous voulez disposer d’une application multiconteneur prête pour la production et scalable.

La figure 4-23 illustre un déploiement dans un cluster d’une application composée de plusieurs microservices (conteneurs).

![Diagramme montrant les applications d’ancrage composées dans un cluster.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Figure 4-23**. Un cluster de conteneurs

vous utilisez un conteneur pour chaque instance de service. Les conteneurs d’ancrage sont des « unités de déploiement » et un conteneur est une instance d’un ancrage. Un hôte gère de nombreux conteneurs. Ceci ressemble à une approche logique. Mais comment gérez-vous l’équilibrage de charge, le routage et l’orchestration de ces applications composées ?

Le moteur Docker standard dans des hôtes Docker individuels répond aux besoins de la gestion des instances avec une seule image sur un seul hôte, mais il ne peut pas faire face quand il s’agit de gérer plusieurs conteneurs déployés sur plusieurs hôtes pour des applications distribuées plus complexes. Dans la plupart des cas, vous avez besoin d’une plateforme de gestion qui démarre automatiquement les conteneurs, met à l’échelle les conteneurs avec plusieurs instances par image, les suspend ou les arrête si nécessaire. il contrôle idéalement également la manière dont ils accèdent aux ressources telles que le réseau et le stockage de données.

Pour aller au-delà de la gestion de conteneurs individuels ou d’applications composées simples et passer à des applications d’entreprise de plus grande envergure avec des microservices, vous devez vous tourner vers des plateformes d’orchestration et de clustering.

Du point de vue de l’architecture et du développement, si vous générez de grosses applications d’entreprise basées sur des microservices, il est important de comprendre les plateformes et les produits suivants, qui prennent en charge des scénarios avancés :

**Clusters et orchestrateurs.** Quand vous devez effectuer un scale-out des applications sur plusieurs hôtes Docker, comme dans le cas d’une application imposante basée sur des microservices, il est essentiel de pouvoir gérer tous ces hôtes sous la forme d’un seul cluster, en faisant abstraction de la complexité de la plateforme sous-jacente. C’est précisément ce que les clusters de conteneurs et les orchestrateurs permettent de faire. Kubernetes est un exemple d’orchestrateur disponible dans Azure par le biais d’Azure Kubernetes Service.

**Planificateurs.** La *planification* signifie qu’un administrateur a la possibilité de lancer des conteneurs dans un cluster : ils doivent donc également fournir une interface utilisateur. Un planificateur de cluster a plusieurs responsabilités : utiliser efficacement les ressources du cluster, définir les contraintes fournies par l’utilisateur, équilibrer efficacement la charge des conteneurs entre les nœuds ou les hôtes, et faire preuve de robustesse face aux erreurs, tout en offrant une haute disponibilité.

Les concepts de cluster et de planificateur sont étroitement liés : les produits fournis par les différents fournisseurs offrent souvent les deux ensembles de fonctionnalités. La liste suivante montre les choix les plus importants pour les plateformes et les logiciels dont vous disposez pour les clusters et les planificateurs. Ces orchestrateurs sont généralement proposés dans des clouds publics comme Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plateformes logicielles pour le clustering, l’orchestration et la planification de conteneurs

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Image du logo Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) est un produit open source qui offre des fonctionnalités allant de l’infrastructure de cluster et la planification de conteneurs aux fonctionnalités d’orchestration. Il vous permet d’automatiser le déploiement, la mise à l’échelle et le fonctionnement de conteneurs d’application entre des clusters d’hôtes. <br><br> *Kubernetes* fournit une infrastructure orientée conteneur, qui regroupe les conteneurs d’application dans des unités logiques pour en faciliter la gestion et la découverte. <br><br> *Kubernetes* est suffisamment mature dans Linux, mais il l’est moins dans Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![Image du logo du service Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS](https://azure.microsoft.com/services/kubernetes-service/) est un service d’orchestration de conteneur Kubernetes géré dans Azure qui simplifie la gestion, le déploiement et les opérations d’un cluster Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Utilisation d’orchestrateurs basés sur des conteneurs dans Microsoft Azure

Plusieurs fournisseurs de cloud offrent la prise en charge des conteneurs Docker, ainsi que celle des clusters et de l’orchestration Docker, notamment Microsoft Azure, Amazon EC2 Container Service et Google Container Engine. Microsoft Azure fournit une prise en charge des clusters et des orchestrateurs Docker par le biais d’Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Utilisation d’Azure Kubernetes Service

Un cluster Kubernetes regroupe plusieurs hôtes Docker et les expose sous la forme d’un seul hôte Docker virtuel. Vous pouvez donc déployer plusieurs conteneurs sur le cluster et effectuer un scale-out d’un nombre illimité d’instances de conteneurs. Le cluster prend en charge tous les détails complexes de la gestion, comme la scalabilité , l’intégrité, etc.

AKS offre un moyen de simplifier la création, la configuration et la gestion d’un cluster de machines virtuelles dans Azure. Ces machines virtuelles sont préconfigurées pour exécuter des applications conteneurisées. À l’aide d’une configuration optimisée d’outils open source courants de planification et d’orchestration, AKS vous permet d’utiliser vos compétences existantes ou de profiter de l’expertise importante et toujours croissante de la communauté pour déployer et gérer des applications conteneurisées sur Microsoft Azure.

Azure Kubernetes Service optimise la configuration des technologies et outils open source courants de clustering Docker spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour la configuration de votre application. Il vous suffit de sélectionner la taille, le nombre d’hôtes et les outils de l’orchestrateur, AKS gère tout le reste.

![Diagramme montrant une structure de cluster Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Figure 4-24**. Structure et topologie simplifiées du cluster Kubernetes

Dans la figure 4-24, vous pouvez voir la structure d’un cluster Kubernetes dans lequel un nœud principal contrôle la plus grande partie de la coordination du cluster et vous pouvez déployer des conteneurs sur le reste des nœuds, qui sont gérés en tant que pool unique à partir d’un point de vue d’application et vous permet de mettre à l’échelle des milliers, voire des dizaines de milliers de conteneurs.

## <a name="development-environment-for-kubernetes"></a>Environnement de développement pour Kubernetes

Dans l’environnement de développement, l' [Ancrable a annoncé en juillet 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) que Kubernetes peut également s’exécuter sur un seul ordinateur de développement (Windows 10 ou MacOS) en installant le Bureau de l’ordinateur d' [amarrage](https://docs.docker.com/install/). Vous pouvez ensuite effectuer un déploiement sur le cloud (AKS) pour d’autres tests d’intégration, comme indiqué sur la figure 4-25.

![Diagramme montrant Kubernetes sur un ordinateur de développement déployé sur AKS](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Figure 4-25**. Exécution de Kubernetes sur la machine de développement et dans le cloud

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Bien démarrer avec AKS (Azure Kubernetes Service)

Pour commencer à utiliser AKS, vous devez déployer un cluster AKS à partir du Portail Azure ou à l’aide de l’interface de ligne de commande. Pour plus d’informations sur le déploiement d’un cluster Kubernetes dans Azure, consultez [Déployer un cluster AKS (Azure Kubernetes Service)](/azure/aks/kubernetes-walkthrough-portal).

Aucun coût n’est facturé pour les logiciels installés par défaut dans le cadre d’AKS. Toutes les options par défaut sont implémentées avec des logiciels open source. AKS est disponible pour plusieurs machines virtuelles dans Azure. Vous êtes facturé uniquement pour les instances de calcul que vous choisissez et les autres ressources d’infrastructure sous-jacentes consommées, telles que le stockage et la mise en réseau. Aucun coût supplémentaire n’est facturé pour AKS.

L’option de déploiement de production par défaut pour Kubernetes consiste à utiliser des graphiques Helm, qui sont présentés dans la section suivante.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Déployer à l’aide de charts Helm sur des clusters Kubernetes

Durant le déploiement d’une application sur un cluster Kubernetes, vous pouvez utiliser l’outil CLI kubectl.exe d’origine et des fichiers de déploiement basés sur le format natif (fichiers .yaml), comme indiqué dans la section précédente. Toutefois, pour les applications Kubernetes plus complexes, par exemple quand vous déployez des applications de microservices complexes, il est recommandé d’utiliser [Helm](https://helm.sh/).

Les charts Helm facilitent la définition, la gestion de versions, l’installation, le partage, la mise à niveau ou la restauration des applications Kubernetes les plus complexes.

Pour aller plus loin, l’utilisation de Helm est également recommandée, car d’autres environnements Kubernetes dans Azure, tels que les [Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces) , sont également basés sur des graphiques Helm.

Helm est géré par la [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) , en collaboration avec Microsoft, Google, BitNami et la communauté de contributeurs Helm.

Pour plus d’informations sur l’implémentation des graphiques Helm et Kubernetes, consultez l’article [utilisation de graphiques Helm pour déployer eShopOnContainers vers AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) .

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Utiliser Azure Dev Spaces pour le cycle de vie de votre application Kubernetes

[Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces) offre une expérience de développement Kubernetes rapide et itérative pour les équipes. Avec une configuration minimale de machine de développement, vous pouvez exécuter et déboguer de manière itérative les conteneurs directement dans Azure Kubernetes Service (AKS). Développez sur Windows, Mac ou Linux en utilisant des outils populaires comme Visual Studio, Visual Studio Code ou la ligne de command.

Comme cela a déjà été indiqué, Azure Dev Spaces utilise des charts Helm durant le déploiement d’applications conteneurisées.

Azure Dev Spaces aide les équipes de développement à être plus productives sur Kubernetes, car elle vous permet d’itérer et de déboguer rapidement du code directement dans un cluster Kubernetes global dans Azure à l’aide de Visual Studio 2019 ou Visual Studio Code. Ce cluster Kubernetes dans Azure est un cluster Kubernetes managé partagé, ce qui permet à votre équipe de travailler de manière collaborative. Vous pouvez développer votre code de manière isolée, puis le déployer sur le cluster global et effectuer des tests de bout en bout avec d’autres composants sans réplication ou simulation des dépendances.

Comme indiqué sur la figure 4-26, la fonctionnalité la plus différenciée dans Azure Dev Spaces est la création d’« espaces » pouvant être intégrés au reste du déploiement global dans le cluster.

![Diagramme montrant l’utilisation de plusieurs espaces dans Azure Dev Spaces.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Figure 4-26**. Utilisation de plusieurs espaces dans Azure Dev Spaces

Vous pouvez configurer un espace de développement partagé dans Azure. Chaque développeur peut se concentrer simplement sur sa partie de l’application et développer de manière itérative du code de prévalidation dans un espace de développement qui contient déjà tous les autres services et ressources cloud dont dépendent leurs scénarios. Les dépendances sont toujours à jour et la façon de travailler des développeurs reflète celle des équipes de production.

Le concept d’espace propre à Azure Dev Spaces vous permet de travailler de manière relativement isolée sans craindre de perturber les membres de votre équipe. Chaque espace de développement fait partie d’une structure hiérarchique qui vous permet de remplacer un microservice (ou plusieurs), à partir de l’espace de développement principal « en haut », par votre microservice en cours d’élaboration.

Cette fonctionnalité est basée sur les préfixes d’URL. Par conséquent, lorsque vous utilisez un préfixe d’espace de développement dans l’URL, une requête est envoyée à partir du microservice cible s’il existe dans l’espace de développement. Dans le cas contraire, cette requête est transférée à la première instance du microservice cible trouvée dans la hiérarchie, pour éventuellement atteindre l’espace de développement principal en haut.

Pour obtenir une vue pratique sur un exemple concret, consultez la [page wiki eShopOnContainers sur Azure dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces).

Pour plus d’informations, consultez l’article sur le [développement en équipe avec Azure dev Spaces](/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Prise en main du service Azure Kubernetes (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** : site officiel. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Précédent](resilient-high-availability-microservices.md) 
> [Suivant](../docker-application-development-process/index.md)
