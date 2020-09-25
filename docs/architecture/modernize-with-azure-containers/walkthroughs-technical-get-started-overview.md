---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Procédures pas à pas et présentation technique de la prise en main
ms.date: 04/28/2018
ms.openlocfilehash: 98d33b13d2b28bfe1c35894df45e525cff0520c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172142"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Procédures pas à pas et vue d’ensemble technique pour le démarrage

Pour limiter la taille de ce livre électronique, des documents techniques supplémentaires et des procédures pas à pas complètes ont été mis à disposition dans un référentiel GitHub. La série de procédures pas à pas en ligne qui sont décrites dans ce chapitre décrit la configuration étape par étape des environnements multiples basés sur des conteneurs Windows et le déploiement sur Azure.

Les sections suivantes expliquent ce que fait chaque procédure pas à pas, ses objectifs et sa vision de haut niveau, et fournit un diagramme des tâches impliquées. Vous pouvez vous procurer les procédures pas-à-pas dans le wiki *eShopModernizing* Apps GitHub référentiel à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/wiki> .

## <a name="technical-walkthrough-list"></a>Liste des procédures pas à pas

Les procédures pas à pas suivantes de prise en main fournissent des conseils techniques cohérents et complets pour les exemples d’applications que vous pouvez passer en utilisant des conteneurs, puis vous déplacer en utilisant plusieurs choix de déploiement dans Azure.

Chacune des procédures pas à pas suivantes utilise les nouveaux exemples d’applications eShopLegacy et eShopModernizing, qui sont disponibles sur GitHub à l’adresse <https://github.com/dotnet-architecture/eShopModernizing> .

- **Visite guidée des applications héritées eShop (applications de référence à moderniser)**

- **Créer un conteneur pour vos applications Web ASP.NET existantes (WebForms & MVC) avec des conteneurs Windows**

- **Emconteneurr vos services WCF existants (applications multiniveaux) avec des conteneurs Windows**

- **Déployer votre application basée sur des conteneurs Windows sur des machines virtuelles Azure**

- **Déployez vos applications basées sur des conteneurs Windows sur Kubernetes dans Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Procédure pas à pas 1 : présentation des applications héritées eShop

### <a name="technical-walkthrough-availability"></a>Disponibilité des procédures techniques

La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :

[procédures pas à pas du wiki eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Vue d’ensemble

Dans cette procédure pas à pas, vous pouvez explorer l’implémentation initiale de trois exemples d’applications héritées. Les deux premiers exemples d’applications Web ont une architecture monolithique et ont été créés à l’aide de ASP.NET classiques. Une application est basée sur ASP.NET 4. x MVC ; la seconde application est basée sur ASP.NET 4. x Web Forms.
La troisième application est une application à trois niveaux composée par une application WinForms client et un service de Windows Communication Foundation côté serveur [(WCF)](../../framework/wcf/whats-wcf.md) .

Toutes ces applications sont disponibles sur le [EShopModernizing GitHub référentiel](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Objectifs

L’objectif principal de cette procédure pas à pas est simplement de se familiariser avec ces applications et avec leur code et leur configuration. Vous pouvez configurer les applications afin qu’elles génèrent et utilisent des données fictives, sans utiliser la base de données SQL, à des fins de test. Cette configuration facultative est basée sur l’injection de dépendances, de façon découplée.

### <a name="scenario-1-aspnet-web-apps"></a>Scénario 1 : applications Web ASP.NET

La figure ci-dessous illustre le scénario simple des applications Web ASP.NET héritées d’origine.

![Scénario d’architecture simple des applications Web ASP.NET héritées d’origine](./media/image5-1.png)

Du point de vue d’un domaine d’entreprise, les deux applications offrent les mêmes fonctionnalités de gestion de catalogue. Les membres de l’équipe eShop Enterprise utilisent l’application pour afficher et modifier le catalogue de produits.

La figure suivante montre les captures d’écran initiales de l’application.

![Applications ASP.NET MVC et ASP.NET Web Forms (technologies existantes/héritées)](./media/image5-2.png)

Les dépendances dans ASP.NET 4. x ou les versions antérieures (pour MVC ou pour Web Forms) signifient que ces applications ne s’exécutent pas sur .NET Core, sauf si le code est entièrement réécrit à l’aide de ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénario 2 : service WCF et application cliente WinForms (application à 3 niveaux)

La figure ci-dessous illustre le scénario simple de l’application héritée à 3 couches d’origine.

![Scénario d’architecture simple de l’application à 3 niveaux héritée d’origine avec un service WCF et une application cliente WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Avantages

Les avantages de cette procédure pas à pas sont simples : Familiarisez-vous avec le code et les applications initiales.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub :

- [Présentation de la base de référence ASP.NET MVC et Web Forms les applications « héritées »](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Visite guidée du service WCF de base et de l’application WinForms (3 niveaux) « hérité »](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Procédure pas à pas 2 : mise en conteneur de vos applications .NET existantes avec des conteneurs Windows

### <a name="overview"></a>Vue d’ensemble

Utilisez des conteneurs Windows pour améliorer le déploiement d’applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, dans des environnements de production, de développement et de test.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est de vous montrer plusieurs options pour la mise en conteneur d’une application .NET Framework existante. Vous pouvez :

- Conversez votre application à l’aide des [outils Visual studio 2017 pour l’ancrage](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual studio 2017 ou versions ultérieures).

- Conversez votre application en ajoutant manuellement un [fichier dockerfile](https://docs.docker.com/engine/reference/builder/), puis en utilisant l' [interface de commande](https://docs.docker.com/engine/reference/commandline/cli/)de l’ancrage.

- Conversez votre application à l’aide de l’outil [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (outil open source de l’ancrage).

Cette procédure pas à pas se concentre sur l’approche outils Visual Studio 2017 pour l’ancrage, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation de fichiers dockerfile.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénario 1 : applications Web ASP.NET en conteneur

La figure ci-dessous illustre le scénario pour les applications Web Apps héritées eShop en conteneur.

![Diagramme d’architecture simplifié des applications ASP.NET en conteneur dans un environnement de développement](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénario 2 : service WCF en conteneur

La figure ci-dessous illustre le scénario d’une application à 3 niveaux avec un service WCF en conteneur.

![Diagramme d’architecture simplifié du service WCF en conteneur dans un environnement de développement](./media/image5-3.5.png)

### <a name="benefits"></a>Avantages

L’exécution de votre application monolithique dans un conteneur présente des avantages. Tout d’abord, vous créez une image pour l’application. À partir de là, chaque déploiement s’exécute dans le même environnement. Chaque conteneur utilise la même version du système d’exploitation, a la même version des dépendances installée, utilise la même version du .NET Framework et est généré à l’aide du même processus. Fondamentalement, vous contrôlez les dépendances de votre application à l’aide d’une image d’ancrage. Les dépendances se déplacent avec l’application lorsque vous déployez les conteneurs.

Un autre avantage est que les développeurs peuvent exécuter l’application dans l’environnement cohérent fourni par les conteneurs Windows. Les problèmes qui apparaissent uniquement avec certaines versions peuvent être détectés immédiatement, au lieu de s’afficher dans un environnement intermédiaire ou de production. Les différences dans les environnements de développement utilisés par les membres de l’équipe de développement sont moins importantes quand les applications s’exécutent dans des conteneurs.

Les applications en conteneur ont également une courbe de montée en puissance parallèle. Les applications en conteneur vous permettent d’avoir plus d’instances d’application et de service (basées sur des conteneurs) sur une machine virtuelle ou un ordinateur physique par rapport aux déploiements d’applications standard par ordinateur. Cela se traduit par une densité plus élevée et moins de ressources requises, en particulier quand vous utilisez des orchestrateurs comme Kubernetes.

Dans les situations idéales, le conteneur ne nécessite pas d’apporter des modifications au code de l’application (C \# ). Dans la plupart des scénarios, vous avez simplement besoin des fichiers de métadonnées de déploiement de l’arrimeur (fichiers dockerfile et Docker Compose).

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub :

- [Comment converser le .NET Framework des applications Web avec des conteneurs et un dockers Windows](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Ajout de la prise en charge de l’ancrage à un service WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Procédure pas à pas 3 : déployer votre application basée sur des conteneurs Windows sur des machines virtuelles Azure

### <a name="technical-walkthrough-availability"></a>Disponibilité des procédures techniques

La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel : <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Vue d’ensemble

Le déploiement sur un ordinateur hôte de station d’accueil sur une machine virtuelle Windows Server 2016 dans Azure vous permet de configurer rapidement des environnements de développement, de test et de mise en lots. Il permet également aux testeurs ou aux utilisateurs professionnels de valider l’application. Les machines virtuelles peuvent également être des environnements de production IaaS (infrastructure as a service) valides.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est de vous montrer les différentes possibilités dont vous disposez lorsque vous déployez des conteneurs Windows sur des machines virtuelles Azure basées sur Windows Server 2016 ou versions ultérieures.

### <a name="scenarios"></a>Scénarios

Plusieurs scénarios sont traités dans cette procédure pas à pas.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénario A : déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage

![Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage](./media/image5-4.png)

**Figure 5-4.** Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénario B : déployer sur une machine virtuelle Azure par le biais d’un registre Dockr

![Déployer sur une machine virtuelle Azure par le biais d’un registre Dockr](./media/image5-5.png)

**Figure 5-5.** Déployer sur une machine virtuelle Azure par le biais d’un registre Dockr

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénario C : déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services

![Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services](./media/image5-6.png)

**Figure 5-6.** Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Machines virtuelles Azure pour les conteneurs Windows

Les machines virtuelles Azure pour les conteneurs Windows sont des machines virtuelles basées sur Windows Server 2016, Windows 10 ou versions ultérieures, avec le moteur d’ancrage configuré. Dans la plupart des cas, Windows Server 2016 est utilisé dans les machines virtuelles Azure.

Azure fournit actuellement une machine virtuelle nommée **Windows Server 2016 avec des conteneurs**. Vous pouvez utiliser cette machine virtuelle pour essayer la nouvelle fonctionnalité de conteneur Windows Server, avec Windows Server Core ou Windows nano Server. Les images du système d’exploitation du conteneur sont installées, puis la machine virtuelle est prête à être utilisée avec l’ancrage.

### <a name="benefits"></a>Avantages

Bien que les conteneurs Windows puissent être déployés sur des machines virtuelles Windows Server 2016 locales, lorsque vous déployez sur Azure, vous disposez d’un moyen plus simple de commencer, avec des machines virtuelles de conteneur Windows Server prêtes à l’emploi. Vous disposez également d’un emplacement en ligne commun qui est accessible aux testeurs et de l’extensibilité automatique par le biais de groupes de machines virtuelles identiques Azure.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Procédure pas à pas 4 : déployer vos applications basées sur des conteneurs Windows sur Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilité des procédures techniques

La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :

[Déploiement des applications sur ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Vue d’ensemble

[Azure Container instances (ACI)](/azure/container-instances/) est le moyen le plus rapide de disposer d’un environnement de développement/test/intermédiaire de conteneurs dans lequel vous pouvez déployer des instances uniques de conteneurs.

### <a name="goals"></a>Objectifs

Cette procédure pas à pas vous montre les principaux scénarios de déploiement de conteneurs Windows vers Azure Container Instances (ACI) et la façon dont vous pouvez déployer des applications eShopModernizing dans ACI.

### <a name="scenarios"></a>Scénarios

Il peut y avoir des variantes relatives au déploiement des applications eShopModernizing dans ACI, telles que le déploiement d’une seule ou de toutes les applications (application MVC, application WebForms ou service WCF). Dans le scénario suivant illustré ci-dessous, vous pouvez voir l’application MVC ASP.NET plus le conteneur SQL Server les deux étant déployés en tant que conteneurs dans ACI (Azure Container Instances).

![Déployer dans ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a>Avantages

Azure Container Instances facilite la création et la gestion de conteneurs Docker dans Azure, sans avoir à approvisionner les machines virtuelles ou à adopter un service de niveau supérieur. Avec ACI, vous pouvez déployer directement un conteneur Windows dans Azure et l’exposer à Internet avec un nom de domaine complet (FQDN) en quelques secondes (à condition que l’image de conteneur Windows soit prête dans un registre de station d’accueil, tel que Dockr Hub ou Azure Container Registry).

### <a name="considerations"></a>Considérations

Le déploiement de conteneurs Windows avec l’ensemble des .NET Framework/ASP.NET ou des SQL Server dans Azure Container Instances (ACI) n’est pas aussi rapide que le déploiement sur un hôte de l’arrimeur standard (comme un ordinateur Windows Server 2016 avec des conteneurs Windows), car l’image de l’arrimeur doit être téléchargée (extraite du registre de l’arrimeur) à chaque fois et la taille de la l’image de conteneur SQL (15,1 Go) et l’image de conteneur ASP.NET (13,9 Go) sont considérablement volumineuses, mais elles sont beaucoup moins chères que la maintenance de votre propre hôte de station d’accueil (Windows Server 2016 en ligne de façon permanente avec les conteneurs Windows dans Azure), ce qui signifie que en revanche, un bon choix pour les déploiements de production.

En guise de conclusion principale, l’utilisation de Azure Container Instances est une option très intéressante pour les scénarios de développement/test et pour les pipelines CI/CD.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub :

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Procédure pas à pas 5 : déployer vos applications basées sur des conteneurs Windows sur Kubernetes dans Azure Container Service

### <a name="technical-walkthrough-availability"></a>Disponibilité des procédures techniques

La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Vue d’ensemble

Une application basée sur des conteneurs Windows devra rapidement utiliser des plateformes, en se déplaçant encore plus loin des machines virtuelles IaaS. Cela est nécessaire pour obtenir facilement une évolutivité élevée et une plus grande évolutivité automatisée, et pour une amélioration significative des déploiements et du contrôle de version automatisés. Vous pouvez atteindre ces objectifs à l’aide d’Orchestrator [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur un conteneur Windows dans Kubernetes (également appelé *K8s*) dans Azure Container service. Le déploiement de Kubernetes à partir de zéro est un processus en deux étapes :

1. Déployez un cluster Kubernetes sur Azure Container Service.

2. Déployez l’application et les ressources associées sur le cluster Kubernetes.

### <a name="scenarios"></a>Scénarios

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénario A : déployer directement sur un cluster Kubernetes à partir d’un environnement de développement

![Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

**Figure 5-7.** Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénario B : déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services

![Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services](./media/image5-8.png)

**Figure 5-8.** Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services

### <a name="benefits"></a>Avantages

Le déploiement sur un cluster dans Kubernetes présente de nombreux avantages. L’avantage le plus important est que vous disposez d’un environnement prêt pour la production dans lequel vous pouvez monter en charge l’application en fonction du nombre d’instances de conteneur que vous souhaitez utiliser (extensibilité interne dans les nœuds existants) et en fonction du nombre de nœuds ou de machines virtuelles du cluster (extensibilité globale du cluster).

Azure Container Service optimise les outils et technologies Open source populaires spécifiquement pour Azure. Vous bénéficiez d’une solution ouverte qui offre la portabilité, à la fois pour vos conteneurs et pour la configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes et Orchestrator Tools-Container service gère tout le reste.

Avec Kubernetes, les développeurs peuvent progresser de la réflexion sur les machines physiques et virtuelles, à la planification d’une infrastructure centrée sur les conteneurs qui facilite les fonctionnalités suivantes, entre autres :

- Applications basées sur plusieurs conteneurs

- Réplication des instances de conteneur et de la mise à l’échelle automatique horizontale

- Attribution de noms et détection (par exemple, DNS interne)

- Équilibrage des charges

- Mises à jour propagées

- Distribution de secrets

- Vérifications de l’intégrité des applications

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Procédure pas à pas 6 : déployer vos applications basées sur des conteneurs Windows vers Azure App Service pour les conteneurs

### <a name="technical-walkthrough-availability"></a>Disponibilité des procédures techniques

La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Vue d’ensemble

Une application en conteneur simple utilisant des conteneurs Windows peut facilement être déployée pour Azure App Service pour les conteneurs. Il s’agit de l’approche recommandée pour la plupart des applications basées sur des conteneurs Windows.

### <a name="goals"></a>Objectifs

L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur un conteneur Windows pour Azure App Service pour les conteneurs à partir d’un registre (Hub ou Azure Container Registry).

### <a name="scenario"></a>Scénario

![Déployer une application basée sur un conteneur Windows pour Azure App Service pour les conteneurs](./media/image5-11.png)

### <a name="benefits"></a>Avantages

Le déploiement sur Azure App Service pour les conteneurs offre les avantages des conteneurs associés aux avantages PaaS de Azure App Service. App service peut facilement être mis à l’échelle verticalement et horizontalement, et peut être configuré pour être mis à l’échelle automatiquement pour répondre aux demandes fluctuantes. Les mises à jour peuvent être effectuées sans temps d’arrêt et la configuration d’un déploiement continu à partir d’un registre est facilement configurée.

### <a name="next-steps"></a>Étapes suivantes

Explorez ce contenu plus en détail sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Précédent](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md) 
>  [Suivant](conclusions.md) <!-- Next Chapter -->
