---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser des Applications .NET existantes avec le Cloud Azure et les conteneurs Windows | Procédures pas à pas et technique obtenir vue d’ensemble de prise en main
ms.date: 04/28/2018
ms.openlocfilehash: 1ae6f3c1e739184356b97fa96e74bab402bf1d2a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832953"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Procédures pas à pas et vue d’ensemble technique pour le démarrage

Pour limiter la taille de ce livre électronique, documentation technique supplémentaire et les procédures pas à pas complète étaient mis à disposition dans un référentiel GitHub. La série en ligne des procédures pas à pas qui est décrite dans ce chapitre décrit la configuration pas à pas des environnements multiples qui reposent sur les conteneurs Windows et le déploiement sur Azure.

Les sections suivantes expliquent ce que chaque procédure pas à pas concerne, ses objectifs et la vision de haut niveau et fournit un diagramme des tâches qui sont impliqués. Vous pouvez obtenir les procédures pas à pas eux-mêmes dans le *eShopModernizing* applications wiki de référentiel GitHub à <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Liste de présentation technique

Les procédures de prise en main suivantes fournissent des conseils techniques cohérente et complète pour les exemples d’applications que vous pouvez de courbes d’élévation et shift en utilisant des conteneurs et ensuite déplacer à l’aide de plusieurs options de déploiement dans Azure.

Chacune des procédures suivantes utilise les nouveaux exemples eShopLegacy et eShopModernizing d’applications, qui sont disponibles sur GitHub à l’adresse <https://github.com/dotnet-architecture/eShopModernizing>.

- **Visite guidée d’eShop les applications héritées (applications de ligne de base à moderniser)**

- **Conteneurisez vos applications web ASP.NET existantes (Web Forms et MVC) avec les conteneurs Windows**

- **Conteneuriser vos services WCF existants (applications multicouches) avec les conteneurs Windows**

- **Déployer votre application basée sur des conteneurs sur Windows sur les machines virtuelles Azure**

- **Déployer vos applications de conteneurs Windows sur Kubernetes dans Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Procédure pas à pas 1 : Visite guidée des applications héritées eShop

### <a name="technical-walkthrough-availability"></a>Disponibilité de la procédure pas à pas techniques

La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :

[eShopModernizing wiki walkthroughs](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Vue d'ensemble

Dans cette procédure pas à pas, vous pouvez explorer l’implémentation initiale de trois exemples d’applications héritées. Les deux premiers exemples d’applications web ont une architecture monolithique et ont été créés à l’aide d’ASP.NET classique. Une application est basée sur ASP.NET 4.x MVC ; la deuxième application repose sur les Web Forms ASP.NET 4.x.
L’application de tiers est une application à 3 couches composée par une application WinForms de client et une côté serveur [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.

Toutes ces applications sont disponibles sur le [eShopModernizing GitHub référentiel](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Objectifs

L’objectif principal de cette procédure pas à pas consiste simplement à vous familiariser avec ces applications et avec leur code et la configuration. Vous pouvez configurer les applications afin qu’ils génèrent et utilisent des données fictives, sans l’aide de la base de données SQL, à des fins de test. Cette configuration facultative est basée sur l’injection de dépendance, d’une manière découplée.

### <a name="scenario-1-aspnet-web-apps"></a>Scénario 1 : Applications Web ASP.NET

La figure ci-dessous illustre un scénario simple des applications web ASP.NET hérités d’origine.

![Scénario d’architecture simple des applications web ASP.NET héritées d’origine](./media/image5-1.png)

À partir d’un point de vue commercial domaine, les deux applications offrent le même catalogue de fonctionnalités de gestion. Membres de l’équipe d’enterprise eShop peut utiliser l’application pour afficher et modifier le catalogue de produits.

La figure suivante montre les captures d’écran de l’application initiale.

![Applications ASP.NET MVC et Web Forms ASP.NET (technologies existantes/héritées)](./media/image5-2.png)

Dépendances dans ASP.NET 4.x ou une version antérieure (soit pour MVC ou Web Forms) signifie que ces applications ne s’exécute pas sur .NET Core, sauf si le code est entièrement réécrit à l’aide d’ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénario 2 : Service WCF et WinForms client application (application de niveau 3)

La figure ci-dessous illustre un scénario simple de l’application héritée à 3 couches d’origine.

![Scénario d’architecture simple de l’application à 3 couches héritée d’origine avec un service WCF et d’une application cliente de WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Avantages

Les avantages de cette procédure pas à pas sont simples : Simplement vous familiariser avec le code et les applications initiales.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub :

- [Visite guidée sur la ligne de base ASP.NET MVC et les applications Web Forms « héritées »](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Visite sur le service WCF de base et l’application « héritée » de WinForms (niveau 3)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Procédure pas à pas 2 : Conteneurisez vos applications .NET existantes avec les conteneurs Windows

### <a name="overview"></a>Vue d'ensemble

Utiliser les conteneurs Windows pour améliorer le déploiement des applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, à des environnements de test, de développement et de production.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est de vous montrer plusieurs options pour conteneuriser une application .NET Framework existante. Vous pouvez :

- Conteneurisez votre application à l’aide de [Visual Studio 2017 Tools pour Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versions ultérieures).

- Conteneurisez votre application en ajoutant manuellement un [Dockerfile](https://docs.docker.com/engine/reference/builder/), puis en utilisant le [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Conteneurisez votre application à l’aide de la [Img2Docker](https://github.com/docker/communitytools-image2docker-win) outil (outil open source à partir de Docker).

Cette procédure pas à pas se concentre sur Visual Studio 2017 Tools pour l’approche de Docker, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation des fichiers Dockerfile.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénario 1 : Applications web ASP.NET en conteneur

Figure ci-dessous illustre le scénario pour les applications d’applications en conteneur eShop web héritées.

![Diagramme d’architecture simplifiée en conteneur dans un environnement de développement des applications ASP.NET](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénario 2 : Service WCF en conteneur

La figure ci-dessous illustre le scénario pour une application à 3 niveaux avec un service WCF en conteneur.

![Diagramme d’architecture du service WCF en conteneur dans un environnement de développement de simplifié](./media/image5-3.5.png)

### <a name="benefits"></a>Avantages

Il existe des avantages à votre application monolithique en cours d’exécution dans un conteneur. Tout d’abord, vous créez une image pour l’application. À ce stade, chaque déploiement s’exécute dans le même environnement. Chaque conteneur utilise la même version du système d’exploitation, a la même version des dépendances installées, utilise la même version du .NET framework et est générée à l’aide du même processus. En fait, contrôler les dépendances de votre application à l’aide d’une image Docker. Les dépendances se déplacent avec l’application lorsque vous déployez les conteneurs.

Un autre avantage est que les développeurs peuvent exécuter l’application dans l’environnement cohérent qui est fournie par les conteneurs Windows. Les problèmes qui apparaissent uniquement dans certaines versions peuvent être détectés immédiatement, au lieu d’exposer dans un environnement intermédiaire ou de production. Différences dans les environnements de développement utilisés par les membres de l’équipe de développement ont moins d’importance lorsque les applications s’exécutent dans des conteneurs.

Applications en conteneur ont également une courbe de montée en puissance flatter. Applications en conteneur activent que vous disposiez de plusieurs instances d’application et service (basées sur les conteneurs) dans une machine virtuelle ou physique par rapport aux déploiements d’application normal par ordinateur. Cela se traduit par densité plus élevée et moins requis ressources, notamment lorsque vous utilisez des orchestrateurs tels que Kubernetes.

Mise en conteneur, dans les situations idéales, ne nécessite pas d’apporter des modifications au code d’application (C\#). Dans la plupart des scénarios, vous devez simplement les fichiers de métadonnées de déploiement Docker (fichiers Dockerfile et Docker Compose).

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub :

- [Comment conteneuriser les applications web de .NET Framework avec les conteneurs Windows et Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Ajout de prise en charge Docker à un service WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Procédure pas à pas 3 : Déployer votre application basée sur des conteneurs sur Windows sur les machines virtuelles Azure

### <a name="technical-walkthrough-availability"></a>Disponibilité de la procédure pas à pas techniques

La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing : <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Vue d'ensemble

Déploiement sur un hôte Docker sur un serveur Windows Server 2016 Virtual Machine (VM) dans Azure vous permet de définir rapidement des environnements de développement/test ou de préproduction. Il vous donne également un emplacement commun pour les testeurs ou aux utilisateurs professionnels valider l’application. Machines virtuelles peuvent également être Infrastructure valide comme un environnement de production du Service (IaaS).

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est de vous montrer les plusieurs alternatives que vous avez lorsque vous déployez les conteneurs Windows sur les machines virtuelles Azure qui sont basés sur Windows Server 2016 ou versions ultérieures.

### <a name="scenarios"></a>Scénarios

Plusieurs scénarios sont couverts dans cette procédure pas à pas.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénario a : Déployer sur une machine virtuelle Azure à partir d’un PC de développement via la connexion du moteur Docker

![Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion de moteur Docker](./media/image5-4.png)

**Figure 5-4.** Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion de moteur Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénario b : Déployer sur une machine virtuelle Azure via un Registre Docker

![Déployer sur une machine virtuelle Azure via un Registre Docker](./media/image5-5.png)

**Figure 5-5.** Déployer sur une machine virtuelle Azure via un Registre Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénario c : Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps

![Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps](./media/image5-6.png)

**Figure 5-6.** Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps

### <a name="azure-vms-for-windows-containers"></a>Machines virtuelles Azure pour les conteneurs Windows

Machines virtuelles Azure pour les conteneurs Windows sont des machines virtuelles basées sur Windows Server 2016, Windows 10 ou versions ultérieures, à la fois avec le moteur Docker configuré. Dans la plupart des cas, Windows Server 2016 est utilisé dans les machines virtuelles Azure.

Azure fournit actuellement une machine virtuelle nommée **Windows Server 2016 avec Containers**. Vous pouvez utiliser cette machine virtuelle pour tester la nouvelle fonctionnalité de conteneur Windows Server, avec Windows Server Core ou Windows Nano Server. Images de système d’exploitation de conteneur sont installés, et ensuite la machine virtuelle est prête à être utilisée avec Docker.

### <a name="benefits"></a>Avantages

Bien que les conteneurs Windows peuvent être déployées sur site Windows Server 2016 les machines virtuelles, lorsque vous déployez sur Azure, vous obtenez un moyen plus simple de prise en main, prêt à l’emploi des machines virtuelles conteneur serveur Windows. Vous obtenez également un emplacement en ligne commun qui est accessible à des testeurs et évolutivité automatique par le biais de machines virtuelles Azure identiques.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Procédure pas à pas 4 : Déployer vos applications de conteneurs Windows sur Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilité de la procédure pas à pas techniques

La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :

[Le déploiement des applications dans ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Vue d'ensemble

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) est le moyen le plus rapide dans un environnement de développement/test/préparation de conteneurs où vous pouvez déployer des instances uniques de conteneurs.

### <a name="goals"></a>Objectifs

Cette procédure pas à pas vous montre les principaux scénarios lors du déploiement de conteneurs de Windows sur Azure Container Instances (ACI) et comment vous pouvez déployer des applications d’eShopModernizing dans ACI.

### <a name="scenarios"></a>Scénarios

Il peut y avoir des variations sur le déploiement des applications eShopModernizing dans ACI telles que le déploiement d’un ou toutes les applications (application MVC, Web Forms application ou service WCF). Dans le scénario suivant, illustré ci-dessous, vous pouvez voir l’application MVC ASP.NET ainsi que le conteneur de SQL Server de ces deux valeurs déployés en tant que conteneurs dans ACI (Azure Container Instances).

![Déployer sur ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a>Avantages

Azure Container Instances rend plus facile créer et gérer des conteneurs Docker dans Azure, sans avoir à approvisionner des machines virtuelles ou à adopter un service de niveau supérieur. Avec ACI, vous pouvez directement déployer un conteneur Windows dans Azure et l’exposer sur internet avec un nom de domaine complet (FQDN) dans l’espace de quelques secondes (à condition que vous avez l’image de conteneur de Windows prêt dans un Registre Docker comme Docker Hub ou Azure Container Registre).

### <a name="considerations"></a>Éléments à prendre en considération

Le déploiement de conteneurs Windows avec le .NET Framework soit complet / ASP.NET ou SQL Server dans Azure Container Instances (ACI) n’est pas tout à fait aussi rapide que le déploiement sur un hôte Docker standard (par exemple, un serveur Windows Server 2016 avec les conteneurs Windows), car l’image Docker doit être téléchargés à chaque fois (extraites à partir du Registre Docker) et la taille de l’image de conteneur SQL (15.1 Go) et l’image de conteneur ASP.NET (13.9 Go) est importante, toutefois, il est beaucoup moins cher que la conservation de votre propre hôte docker (définitivement en ligne Windows Server 2016 avec la machine virtuelle de conteneurs Windows dans Azure) ne pas à mentionner un ensemble orchestrateur comme Kubernetes dans Azure (ACS) qui est, quant à eux, un excellent choix pour les déploiements de production.

En tant que principale conclusion, à l’aide d’Azure Container Instances est une option très intéressante pour les scénarios de développement/Test et pour les pipelines CI/CD.

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub :

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Procédure pas à pas 5 : Déployer vos applications de conteneurs Windows sur Kubernetes dans Azure Container Service

### <a name="technical-walkthrough-availability"></a>Disponibilité de la procédure pas à pas techniques

La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Vue d'ensemble

Une application qui repose sur les conteneurs Windows devra rapidement utilisent des plateformes, s’éloigner de davantage de machines virtuelles IaaS. Cela est nécessaire pour facilement atteindre une haute évolutivité et mieux automatisée l’évolutivité et pour une amélioration significative d’automatisé de déploiements et le contrôle de version. Vous pouvez atteindre ces objectifs à l’aide de l’orchestrateur [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas consiste à apprendre à déployer une application Windows conteneur sur Kubernetes (également appelé *K8s*) dans Azure Container Service. Déploiement sur Kubernetes à partir de zéro est un processus en deux étapes :

1. Déployer un cluster Kubernetes sur Azure Container Service.

2. Déployer l’application et les ressources associées au cluster Kubernetes.

### <a name="scenarios"></a>Scénarios

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénario a : Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement

![Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

**Figure 5-7.** Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénario b : Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps

![Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps](./media/image5-8.png)

**Figure 5-8.** Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps

### <a name="benefits"></a>Avantages

Il existe de nombreux avantages pour le déploiement sur un cluster dans Kubernetes. Le principal avantage est que vous obtenez un environnement prêt pour la production dans lequel vous pouvez faire évoluer l’application en fonction du nombre d’instances de conteneur vous souhaitez utiliser (interne-extensibilité dans les nœuds existants) et en fonction du nombre de machines virtuelles ou des nœuds dans le cluster ( évolutivité globale du cluster).

Azure Container Service optimise les technologies et outils open source populaires spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité, pour vos conteneurs et la configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes, et l’outils d’orchestrator-Container Service gère tout le reste.

Avec Kubernetes, les développeurs peuvent progresser de réfléchir aux ordinateurs physiques et virtuels, à la planification d’une infrastructure orientée conteneur qui facilite les fonctionnalités suivantes, entre autres :

- Applications basées sur plusieurs conteneurs

- Réplication des instances de conteneur et de mise à l’échelle horizontale

- D’affectation de noms et de la découverte (par exemple, DNS interne)

- L’équilibrage de charge

- Mises à jour propagées

- Distribution de clés secrètes

- Vérifications d’intégrité de l’application

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Procédure pas à pas 6 : Déployer vos applications de conteneurs Windows sur Azure App Service pour les conteneurs

### <a name="technical-walkthrough-availability"></a>Disponibilité de la procédure pas à pas techniques

La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Vue d'ensemble

Une simple application en conteneur à l’aide de conteneurs de Windows peut facilement être déployée sur Azure App Service pour les conteneurs. Il s’agit de l’approche recommandée pour la plupart des applications en conteneur de Windows.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur les conteneurs Windows sur Azure App Service pour les conteneurs à partir d’un Registre (Docker Hub ou Azure Container Registry).

### <a name="scenario"></a>Scénario

![Déployer l’application conteneur Windows sur Azure App Service pour les conteneurs](./media/image5-11.png)

### <a name="benefits"></a>Avantages

Déploiement sur Azure App Service pour les conteneurs offre les avantages des conteneurs associés avec les avantages de PaaS d’Azure App Service. Le service d’application peut facilement être mis à l’échelle verticalement et horizontalement et peut être configuré à l’échelle automatique pour répondre aux demandes changeantes. Mises à jour peuvent être effectuées sans temps d’arrêt et de configuration de déploiement continu à partir d’un Registre est facilement configurée.

## <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus approfondi sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Précédent](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [Suivant](conclusions.md)
