---
title: Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Recommandations sur l’hébergement Azure pour les applications web ASP.NET
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: a93009e66d63aa7d9c3b60951d43eafa3c351a63
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053261"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core

> « Les leaders métier ne passent plus par les départements informatiques pour obtenir des applications du cloud (également appelé SaaS) et les paient comme ils paient un abonnement à un magazine. Quand ils n’ont plus besoin du service, ils peuvent annuler l’abonnement sans se retrouver avec du matériel inutilisé dans un coin. »  
> _\- Daryl Plummer, analyste chez Gartner_

Quels que soient les besoins et l’architecture de votre application, Microsoft Azure peut la prendre en charge. Vos besoins d’hébergement peuvent être aussi simples que ceux d’un site web statique ou aussi complexes que ceux d’une application sophistiquée constituée de dizaines de services. Pour les applications ASP.NET Core monolithiques et les services qui les prennent en charge, il existe plusieurs configurations connues qui sont recommandées. Les suggestions présentées dans cet article sont regroupées en fonction du type de ressource à héberger, qu’il s’agisse d’applications complètes, de processus individuels ou de données.

## <a name="web-applications"></a>Applications Web

Les applications web peuvent être hébergées avec :

- App Service Web Apps

- Conteneurs

- Des machines virtuelles

Entre tous, App Service Web Apps constitue l’approche recommandée pour la plupart des scénarios. Pour les architectures de microservices, envisagez une approche basée sur les conteneurs. Si vous avez besoin de contrôler davantage les machines qui exécutent votre application, envisagez le service Machines virtuelles Azure.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps offre une plateforme entièrement managée, optimisée pour l’hébergement d’applications web. Il s’agit d’une offre de plateforme PaaS qui vous permet de vous concentrer sur votre logique métier, tandis qu’Azure fournit l’infrastructure nécessaire pour exécuter et mettre à l’échelle l’application. Voici quelques fonctionnalités clés d’App Service Web Apps :

- Optimisation de DevOps (intégration et livraison continues, environnements multiples, tests A/B, prise en charge des scripts).

- Échelle globale et haute disponibilité.

- Connexions aux plateformes SaaS et à vos données locales.

- Sécurité et conformité.

- Intégration Visual Studio.

- Prise en charge des conteneurs Linux et Windows via [Web App pour conteneurs](https://azure.microsoft.com/services/app-service/containers/).

Azure App Service est le meilleur choix pour la plupart des applications web. Le déploiement et la gestion sont intégrés à la plateforme, les sites peuvent évoluer rapidement pour gérer des charges de trafic élevées, et l’équilibrage de charge et le gestionnaire de trafic intégrés offrent une haute disponibilité. Vous pouvez déplacer facilement des sites existants vers Azure App Service avec un outil de migration en ligne, utiliser une application open source de la galerie d’applications web, ou créer un site en utilisant le framework et les outils de votre choix. La fonctionnalité WebJobs facilite l’ajout du traitement de travaux en arrière-plan à votre application web App Service.

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) gère votre environnement Kubernetes hébergé, ce qui vous permet de déployer et de gérer de manière simple et rapide les applications en conteneur sans pour autant maîtriser l’orchestration de conteneurs. Il élimine aussi les contraintes liées aux opérations et à la maintenance continues en provisionnant, en mettant à niveau et en mettant à l’échelle les ressources à la demande, sans déconnecter vos applications.

AKS réduit la complexité et les frais de fonctionnement liés à la gestion d’un cluster Kubernetes en déléguant une grande partie de cette responsabilité à Azure. En tant que service Kubernetes hébergé, Azure gère les tâches critiques à votre place, notamment l’analyse du fonctionnement et la maintenance. Par ailleurs, vous payez uniquement pour les nœuds d’agent de vos clusters, pas pour les maîtres. En tant que service Kubernetes géré, AKS fournit :

- Des mises à niveau de version et des mises à jour correctives Kubernetes automatisées.
- Une mise à l’échelle simplifiée des clusters.
- Un plan de contrôle hébergé avec auto-réparation (maîtres).
- Une réduction des coûts : vous payez uniquement pour les nœuds de pool d’agents qui s’exécutent.

La gestion des nœuds de votre cluster AKS étant assurée par Azure, vous n’avez plus besoin d’effectuer de nombreuses tâches manuelles, comme les mises à niveau de cluster. Comme Azure gère ces tâches de maintenance critiques à votre place, AKS ne fournit pas d’accès direct (comme avec SSH) au cluster.

### <a name="azure-virtual-machines"></a>Machines virtuelles Azure

Si vous avez une application existante qui nécessite des modifications substantielles pour s’exécuter dans App Service, vous pouvez choisir Machines virtuelles afin de simplifier la migration vers le cloud. Cependant, la configuration, la sécurisation et la gestion des machines virtuelles nécessitent beaucoup plus de temps et d’expertise en informatique comparé à Azure App Service. Si vous envisagez d’utiliser Machines virtuelles Azure, veillez à prendre en compte le travail continu de maintenance nécessaire pour appliquer les correctifs, mettre à jour et gérer votre environnement de machines virtuelles. Machines virtuelles Azure est une infrastructure IaaS, tandis qu’App Service est une plateforme Paas. Vous devez également déterminer si le déploiement de votre application comme conteneur Windows dans Web App pour conteneurs est une option viable pour votre scénario.

## <a name="logical-processes"></a>Processus logiques

Les processus logiques individuels qui peuvent être dissociés du reste de l’application peuvent être déployés indépendamment sur Azure Functions de manière « serveless ». Azure Functions vous permet de simplement écrire le code dont vous avez besoin pour un problème donné, sans se préoccuper de l’application ou de l’infrastructure pour l’exécuter. Vous pouvez choisir parmi une variété de langages de programmation, notamment C\#, F\#, Node.js, Python et PHP, ce qui vous permet de choisir le langage le plus productif pour la tâche à traiter. Comme la plupart des solutions cloud, vous payez seulement pour la durée de votre utilisation, et vous pouvez faire confiance à Azure Functions pour monter en puissance au fil des besoins.

## <a name="data"></a>Données

Azure propose un large éventail d’options de stockage des données, afin que votre application puisse utiliser le fournisseur de données approprié pour les données en question.

Pour les données transactionnelles relationnelles, les bases de données Azure SQL Database sont la meilleure option. Pour de hautes performances avec les données qui sont principalement en lecture, un cache Redis s’appuyant sur une base de données Azure SQL Database est une bonne solution.

Les données JSON non structurées peuvent être stockées de différentes façons : colonnes SQL Database, objets blob ou tables dans Stockage Azure, ou encore DocumentDB. Parmi ces possibilités, DocumentDB offre les meilleures fonctionnalités de requête et il s’agit de l’option recommandée pour de grandes quantités de documents JSON qui doivent prendre en charge les requêtes.

Les données basées sur des commandes ou des événements transitoires pour orchestrer le comportement des applications peuvent utiliser Azure Service Bus ou Stockage File d’attente Azure. Azure Service Bus offre davantage de souplesse et est le service recommandé pour les échanges complexes de messages au sein des applications et entre elles.

## <a name="architecture-recommendations"></a>Suggestions en matière d’architecture

Les exigences de votre application doivent dicter son architecture. Il existe de nombreux services Azure différents. Aussi, il est important de choisir le bon. Microsoft propose une galerie d’architectures de référence pour aider à identifier des architectures classiques optimisées pour les scénarios courants. Vous pouvez adopter une architecture de référence qui correspond de près aux exigences de votre application ou qui constitue au moins un point de départ.

La figure 11-2 montre un exemple d’architecture de référence. Ce diagramme décrit une approche recommandée pour l’architecture d’un site web de système de gestion de contenu Sitecore optimisé pour le marketing.

![](./media/image11-2.png)

**Figure 11-1.** Architecture de référence d’un site web de marketing Sitecore.

**Informations de référence : recommandations sur l’hébergement Azure**

- Architectures de solutions Azure\
  <https://azure.microsoft.com/solutions/architecture/>

- Guide du développeur Azure\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Vue d’ensemble de Web Apps\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Web App pour conteneurs\
  <https://azure.microsoft.com/services/app-service/containers/>

- Présentation d’Azure Kubernetes Service (AKS)\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Précédent](development-process-for-azure.md)
