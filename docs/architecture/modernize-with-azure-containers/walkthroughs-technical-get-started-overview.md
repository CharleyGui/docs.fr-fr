---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser les applications .NET existantes avec le cloud Azure et les conteneurs Windows (fr) Les procédures à pas et la technique commencent la vue d’ensemble
ms.date: 04/28/2018
ms.openlocfilehash: cff418d9b6e931a3082d8a2f8b818e7275139578
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987867"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Procédures pas à pas et vue d’ensemble technique pour le démarrage

Pour limiter la taille de ce livre électronique, des documents techniques supplémentaires et des procédures à pas complètes ont été mis à disposition dans un référentiel GitHub. La série en ligne de procédures à pas décrites dans ce chapitre couvre la configuration étape par étape des différents environnements qui sont basés sur les conteneurs Windows, et le déploiement à Azure.

Les sections suivantes expliquent ce qu’il s’agit, ses objectifs et sa vision de haut niveau, et fournit un diagramme des tâches qui sont impliquées. Vous pouvez obtenir les pas à pas eux-mêmes dans les applications <https://github.com/dotnet-architecture/eShopModernizing/wiki> *eShopModernizing* GitHub repo wiki à .

## <a name="technical-walkthrough-list"></a>Liste technique des pas à pas

Les procédures à pas qui suivent fournissent des conseils techniques cohérents et complets pour les applications d’échantillons que vous pouvez soulever et déplacer à l’aide de conteneurs, puis se déplacer en utilisant plusieurs choix de déploiement en Azure.

Chacune des procédures à pas suivantes utilise le nouvel exemple eShopLegacy et eShopModernizing <https://github.com/dotnet-architecture/eShopModernizing>applications, qui sont disponibles sur GitHub à .

- **Visite des applications héritées d’eShop (applications de base pour moderniser)**

- **Conteneurisez vos applications Web ASP.NET existantes (WebForms & MVC) avec des conteneurs Windows**

- **Conteneurisez vos services WCF existants (applications N-Tier) avec des conteneurs Windows**

- **Déployez votre application Windows Containers sur les VM Azure**

- **Déployez vos applications basées sur les conteneurs Windows sur Kubernetes dans azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Procédure pas à pas 1: Tour des applications héritées eShop

### <a name="technical-walkthrough-availability"></a>Disponibilité technique de procédure pas à pas

La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :

[eShopModernizing wiki pas à pas](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Vue d'ensemble

Dans cette procédure pas à pas, vous pouvez explorer la mise en œuvre initiale de trois applications héritées de l’échantillon. Les deux premières applications web d’échantillon ont une architecture monolithique, et ont été créées en utilisant des ASP.NET classiques. Une application est basée sur ASP.NET 4.x MVC; la deuxième application est basée sur ASP.NET 4.x Web Forms.
La troisième application est une application à 3 niveaux composée par une application WinForms cliente et un service [de la Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) côté serveur.

Toutes ces applications sont disponibles à [l’eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Objectifs

L’objectif principal de cette procédure pas à pas est simplement de se familiariser avec ces applications, et avec leur code et leur configuration. Vous pouvez configurer les applications afin qu’elles génèrent et utilisent des données fictives, sans utiliser la base de données SQL, à des fins de test. Ce config optionnel est basé sur l’injection de dépendance, d’une manière découplée.

### <a name="scenario-1-aspnet-web-apps"></a>Scénario 1 : ASP.NET applications Web

La figure ci-dessous montre le scénario simple de l’héritage original ASP.NET applications Web.

![Scénario d’architecture simple de l’héritage original ASP.NET applications web](./media/image5-1.png)

Du point de vue du domaine d’affaires, les deux applications offrent les mêmes fonctionnalités de gestion de catalogue. Les membres de l’équipe d’entreprise eShop utiliseraient l’application pour afficher et modifier le catalogue de produits.

Le chiffre suivant montre les captures d’écran initiales de l’application.

![ASP.NET des applications MVC et ASP.NET Web Forms (technologies existantes/héritées)](./media/image5-2.png)

Les dépendances dans ASP.NET versions 4.x ou antérieures (pour MVC ou pour les formulaires Web) signifient que ces applications ne s’exécuteront pas sur .NET Core à moins que le code ne soit entièrement réécrit en utilisant ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénario 2 : service WCF et application client WinForms (application 3-Tier)

La figure ci-dessous montre le scénario simple de l’application originale de l’héritage à 3 niveaux.

![Scénario d’architecture simple de l’application 3-Tier originale avec un service WCF et une application client WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Avantages

Les avantages de cette procédure pas à pas sont simples: Il suffit de se familiariser avec le code et les applications initiales.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :

- [Visite des applications « legacy » ASP.NET MVC et Web Forms](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Visite du service WCF de base et de l’application « héritage » de WinForms (3-Tier)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Procédure pas à pas 2 : Conteneurisez vos applications .NET existantes avec des conteneurs Windows

### <a name="overview"></a>Vue d'ensemble

Utilisez Windows Containers pour améliorer le déploiement d’applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, dans les environnements de production, de développement et de test.

### <a name="goals"></a>Objectifs

Le but de cette procédure pas à pas est de vous montrer plusieurs options pour la conteneurisation d’une application cadre .NET existante. Vous pouvez :

- Conteneurisez votre application en utilisant [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versions ultérieures).

- Conteneurisez votre application en ajoutant manuellement un [Dockerfile,](https://docs.docker.com/engine/reference/builder/)puis en utilisant le [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Conteneurisez votre application en utilisant l’outil [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (un outil open-source de Docker).

Ce pas-là se concentre sur l’approche Visual Studio 2017 Tools for Docker, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation de Dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénario 1 : Applications Web ASP.NET conteneurisées

Figure ci-dessous montre le scénario pour les applications d’applications web héritées de containerized eShop.

![Diagramme d’architecture simplifié des applications de ASP.NET conteneurisées dans un environnement de développement](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénario 2 : Service WCF conteneurisé

Figure ci-dessous montre le scénario d’une application à 3 niveaux avec un service WCF conteneurisé.

![Diagramme d’architecture simplifié du service WCF conteneurisé dans un environnement de développement](./media/image5-3.5.png)

### <a name="benefits"></a>Avantages

Il y a des avantages à exécuter votre application monolithique dans un récipient. Tout d’abord, vous créez une image pour l’application. À partir de ce moment, chaque déploiement se déroule dans le même environnement. Chaque conteneur utilise la même version OS, a la même version de dépendances installées, utilise la même version cadre .NET, et est construit en utilisant le même processus. Fondamentalement, vous contrôlez les dépendances de votre application en utilisant une image Docker. Les dépendances voyagent avec l’application lorsque vous déployez les conteneurs.

Un avantage supplémentaire est que les développeurs peuvent exécuter l’application dans l’environnement cohérent qui est fourni par Windows Containers. Les problèmes qui n’apparaissent qu’avec certaines versions peuvent être repérés immédiatement, au lieu de faire surface dans un environnement de mise en scène ou de production. Les différences dans les environnements de développement utilisés par les membres de l’équipe de développement sont moins importantes lorsque les applications s’exécutent dans des conteneurs.

Les applications conteneurisées ont également une courbe d’échelle plus plate. Les applications conteneurisées vous permettent d’avoir plus d’instances d’application et de service (basées sur des conteneurs) dans une machine VM ou physique par rapport aux déploiements d’applications réguliers par machine. Cela se traduit par une densité plus élevée et moins de ressources nécessaires, en particulier lorsque vous utilisez des orchestrateurs comme Kubernetes.

La conteneurisation, dans des situations idéales, ne nécessite\#aucune modification du code d’application (C ). Dans la plupart des scénarios, vous avez juste besoin des fichiers de métadonnées de déploiement Docker (fichiers Dockerfiles et Docker Compose).

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :

- [Comment conteneuriser les applications Web .NET Framework avec Windows Containers et Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Ajout d’un soutien Docker à un service WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Procédure pas à pas 3 : Déployez votre application Windows Containers sur les VM Azure

### <a name="technical-walkthrough-availability"></a>Disponibilité technique de procédure pas à pas

La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Vue d'ensemble

Le déploiement à un hôte Docker sur une machine virtuelle (VM) Windows Server 2016 dans Azure vous permet de configurer rapidement des environnements de développement/test/staging. Il vous donne également un endroit commun pour les testeurs ou les utilisateurs professionnels pour valider l’application. Les VM peuvent également être des environnements de production d’infrastructure valides en tant que service (IaaS).

### <a name="goals"></a>Objectifs

Le but de cette procédure pas à pas est de vous montrer les multiples alternatives que vous avez lorsque vous déployez des conteneurs Windows dans les machines à sous Azure qui sont basées sur Windows Server 2016 ou les versions ultérieures.

### <a name="scenarios"></a>Scénarios

Plusieurs scénarios sont couverts dans cette procédure pas à pas.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénario A : Déploiement à une VM Azure à partir d’un PC dev via la connexion Docker Engine

![Déployer sur une VM Azure à partir d’un PC dev via une connexion Docker Engine](./media/image5-4.png)

**Figure 5-4.** Déployer sur une VM Azure à partir d’un PC dev via une connexion Docker Engine

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénario B : Déploiement à une VM Azure par le biais d’un registre Docker

![Déploiement à une VM Azure par le biais d’un registre Docker](./media/image5-5.png)

**Figure 5-5.** Déploiement à une VM Azure par le biais d’un registre Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénario C : Déploiement à une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services

![Déploiement dans une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services](./media/image5-6.png)

**Figure 5-6.** Déploiement dans une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Sous-verre Azure pour les conteneurs Windows

Les machines à sous Azure pour les conteneurs Windows sont des machines VM basées sur Windows Server 2016, Windows 10, ou des versions ultérieures, toutes deux avec Docker Engine mis en place. Dans la plupart des cas, Windows Server 2016 est utilisé dans les VM Azure.

Azure fournit actuellement un VM nommé **Windows Server 2016 avec Conteneurs**. Vous pouvez utiliser ce VM pour essayer la nouvelle fonctionnalité De conteneur Windows Server, avec Windows Server Core ou Windows Nano Server. Les images de Container OS sont installées, puis la VM est prête à l’emploi avec Docker.

### <a name="benefits"></a>Avantages

Bien que Windows Containers puisse être déployé sur place Windows Server 2016 VMs, lorsque vous vous déployez à Azure, vous obtenez un moyen plus facile de démarrer, avec des VM Windows Server contenants prêts à l’emploi. Vous obtenez également un emplacement en ligne commun qui est accessible aux testeurs, et l’évolutivité automatique grâce à Azure ensembles de machines virtuelles.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Procédure pas à pas 4 : Déployez vos applications basées sur des conteneurs Windows dans Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilité technique de procédure pas à pas

La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :

[Déploiement des applications à l’ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Vue d'ensemble

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) est le moyen le plus rapide d’avoir un environnement de test/de mise en scène de conteneurs où vous pouvez déployer des instances uniques de conteneurs.

### <a name="goals"></a>Objectifs

Ce pas-là vous montre les principaux scénarios lors du déploiement de conteneurs Windows dans Azure Container Instances (ACI) et comment vous pouvez déployer eShopModernizing Apps dans ACI.

### <a name="scenarios"></a>Scénarios

Il peut y avoir des variations sur le déploiement des applications eShopModernizing dans ACI telles que le déploiement d’une seule ou l’autre des applications (application MVC, application WebForms ou service WCF). Dans le scénario ci-dessous, vous pouvez voir l’application ASP.NET MVC ainsi que le conteneur SQL Server qui sont tous deux déployés sous forme de conteneurs dans ACI (Azure Container Instances).

![Déploiement à l’ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a>Avantages

Azure Container Instances facilite la création et la gestion de conteneurs Docker dans Azure, sans avoir à approvisionner les machines virtuelles ou à adopter un service de niveau supérieur. Avec ACI, vous pouvez déployer directement un conteneur Windows dans Azure et l’exposer à Internet avec un nom de domaine entièrement qualifié (FQDN) en quelques secondes (à condition que vous ayez l’image De conteneur Windows prêt dans un registre Docker comme Docker Hub ou Azure Container Registry).

### <a name="considerations"></a>Considérations

Déployer des conteneurs Windows avec un cadre .NET complet / ASP.NET ou SQL Server dans Azure Container Instances (ACI) n’est pas aussi rapide que le déploiement à un hôte Docker régulier (comme un serveur Windows 2016 avec Des conteneurs Windows) parce que l’image Docker doit être téléchargé (tiré du registre Docker) à chaque fois et la taille de l’image conteneur SQL (201615.1 Go) et l’image de conteneur ASP.NET (13,9 Go) sont significativement grandes, mais il est beaucoup moins cher que de maintenir votre propre hôte docker (en ligne en ligne Windows Server 2016 avec Windows Containers VM en Azure) sans parler d’un orchestrateur entier comme Kubernetes en Azure (AKS) qui est, d’autre part, un excellent choix pour les déploiements de production.

En conclusion principale, l’utilisation d’Azure Container Instances est une option très convaincante pour les scénarios Dev/Test et pour les pipelines CI/CD.

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Procédure pas à pas 5 : Déployez vos applications basées sur les conteneurs Windows vers Kubernetes dans le service de conteneurs Azure

### <a name="technical-walkthrough-availability"></a>Disponibilité technique de procédure pas à pas

La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Vue d'ensemble

Une application basée sur Windows Containers devra rapidement utiliser des plates-formes, s’éloignant encore plus des VM IaaS. Cela est nécessaire pour atteindre facilement une grande évolutivité et une meilleure évolutivité automatisée, et pour une amélioration significative des déploiements automatisés et de la version. Vous pouvez atteindre ces objectifs en utilisant l’orchestrateur [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur windows Container à Kubernetes (également appelé *K8s*) dans Azure Container Service. Le déploiement à Kubernetes à partir de zéro est un processus en deux étapes :

1. Déployez un cluster Kubernetes au service de conteneurs Azure.

2. Déployez l’application et les ressources connexes au cluster Kubernetes.

### <a name="scenarios"></a>Scénarios

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénario A : Déploiement directement sur un cluster Kubernetes à partir d’un environnement de dev

![Déploiement directement dans un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

**Figure 5-7.** Déploiement directement dans un cluster Kubernetes à partir d’un environnement de développement

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénario B : Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services

![Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services](./media/image5-8.png)

**Figure 5-8.** Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services

### <a name="benefits"></a>Avantages

Le déploiement à un cluster à Kubernetes existe de nombreux avantages. Le plus grand avantage est que vous obtenez un environnement prêt à la production dans lequel vous pouvez échelle de l’application en fonction du nombre d’instances de conteneurs que vous souhaitez utiliser (évolutivité intérieure dans les nœuds existants), et basé sur le nombre de nœuds ou de VM dans le cluster (évolutivité globale du cluster).

Azure Container Service optimise les outils et technologies open source populaires spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité, à la fois pour vos conteneurs et pour votre configuration d’application. Vous sélectionnez la taille, le nombre d’hôtes et l’orchestrateur tools-Container Service gère tout le reste.

Avec Kubernetes, les développeurs peuvent passer de la réflexion sur les machines physiques et virtuelles à la planification d’une infrastructure centrée sur les conteneurs qui facilite les capacités suivantes, entre autres :

- Applications basées sur plusieurs conteneurs

- Réplique des instances de conteneurs et autoscalage horizontal

- Nommer et découvrir (par exemple, DNS interne)

- Équilibrer les charges

- Mises à jour de roulement

- Distribuer des secrets

- Vérifications de santé des demandes

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Procédure pas à pas 6 : Déployez vos applications basées sur les conteneurs Windows au service d’applications Azure pour les conteneurs

### <a name="technical-walkthrough-availability"></a>Disponibilité technique de procédure pas à pas

La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Vue d'ensemble

Une simple application conteneurisée utilisant des conteneurs Windows peut facilement être déployée sur Azure App Service for Containers. Il s’agit de l’approche recommandée pour la plupart des applications basées sur les conteneurs Windows.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur windows Container à Azure App Service for Containers à partir d’un registre (Docker Hub ou Azure Container Registry).

### <a name="scenario"></a>Scénario

![Déployer l’application Windows Container sur Azure App Service for Containers](./media/image5-11.png)

### <a name="benefits"></a>Avantages

Le déploiement au service d’applications Azure pour les conteneurs offre les avantages des conteneurs jumelés aux avantages PaaS du service d’application Azure. Le service d’application peut facilement être mis à l’échelle verticalement et horizontalement, et peut être configuré à l’échelle automatique pour répondre aux demandes changeantes. Les mises à jour peuvent être effectuées avec zéro temps d’arrêt et la configuration du déploiement continu à partir d’un registre est facilement configurée ainsi.

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en profondeur sur le wiki GitHub :<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Suivant précédent](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Next](conclusions.md) <!-- Next Chapter -->
