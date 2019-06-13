---
title: Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Recommandations sur l’hébergement Azure pour les applications web ASP.NET
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758666"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core

> « Line-of-business leaders partout sont en ignorant les services informatiques pour obtenir des applications à partir du cloud (également appelé SaaS) et payer pour elles comme ils paient un abonnement au magazine. Quand ils n’ont plus besoin du service, ils peuvent annuler l’abonnement sans se retrouver avec du matériel inutilisé dans un coin. »  
> _\- Daryl Plummer, analyste chez Gartner_

Tout ce qui doit et l’architecture de votre application, Microsoft Azure peut prennent en charge. Vos besoins d’hébergement peuvent être aussi simples qu’un site Web statique ou une application sophistiquée constituée de dizaines de services. Pour les applications ASP.NET Core monolithiques et les services qui les prennent en charge, il existe plusieurs configurations connues qui sont recommandées. Les suggestions présentées dans cet article sont regroupées en fonction du type de ressource à héberger, qu’il s’agisse d’applications complètes, de processus individuels ou de données.

## <a name="web-applications"></a>Applications Web

Les applications web peuvent être hébergées avec :

- App Service Web Apps

- Conteneurs (plusieurs options)

- Des machines virtuelles

Parmi ceux-ci, App Service Web Apps est l’approche recommandée pour la plupart des scénarios, y compris des applications conteneur simples. Pour les architectures de microservices, envisagez une approche basée sur les conteneurs. Si vous avez besoin de contrôler davantage les machines qui exécutent votre application, envisagez le service Machines virtuelles Azure.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps offre une plateforme entièrement managée, optimisée pour l’hébergement d’applications web. Il s’agit d’une offre de plateforme PaaS qui vous permet de vous concentrer sur votre logique métier, tandis qu’Azure fournit l’infrastructure nécessaire pour exécuter et mettre à l’échelle l’application. Voici quelques fonctionnalités clés d’App Service Web Apps :

- Optimisation de DevOps (intégration et livraison continues, environnements multiples, tests A/B, prise en charge des scripts).

- Échelle globale et haute disponibilité.

- Connexions aux plateformes SaaS et à vos données locales.

- Sécurité et conformité.

- Intégration Visual Studio.

Azure App Service est le meilleur choix pour la plupart des applications web. Le déploiement et la gestion sont intégrés à la plateforme, les sites peuvent évoluer rapidement pour gérer des charges de trafic élevées, et l’équilibrage de charge et le gestionnaire de trafic intégrés offrent une haute disponibilité. Vous pouvez déplacer facilement des sites existants vers Azure App Service avec un outil de migration en ligne, utiliser une application open source de la galerie d’applications web, ou créer un site en utilisant le framework et les outils de votre choix. La fonctionnalité WebJobs facilite l’ajout du traitement de travaux en arrière-plan à votre application web App Service. Si vous disposez d’une application ASP.NET hébergée en local à l’aide d’une base de données locale, il existe un chemin clair pour migrer l’application vers une application App Service Web avec une base de données SQL Azure (ou un accès sécurisé à votre serveur de base de données sur site, si vous préférez).

![Stratégie de migration recommandée pour les applications .NET sur Azure App Service sur site](./media/image1-6.png)

Dans la plupart des cas, le déplacement d’une application ASP.NET hébergée localement à une application Web App Service est un processus simple. Peu ou aucune modification doit être requise de l’application elle-même, et il peut rapidement commencer à tirer parti des nombreuses fonctionnalités qui offrent Azure App Service Web Apps.

En plus des applications qui ne sont pas optimisées pour le cloud, Azure App Service Web Apps sont une excellente solution pour nombreux simples (non distribué) applications monolithiques, telles que de nombreuses applications ASP.NET Core. Dans cette approche, l’architecture est simple à comprendre et à gérer et de base :

![Architecture Azure de base](./media/image1-5.png)

Un petit nombre de ressources dans un seul groupe de ressources est généralement suffisant pour gérer une telle application. Les applications qui sont généralement déployées comme une unité unique, plutôt que ces applications sont constituées de nombreux processus distincts, sont de bons candidats pour ce [base approche architecturale](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). Bien que simple point de vue architectural, cette approche autorise toujours l’application hébergée à l’échelle à la fois des (plus de ressources par nœud) et out (plus hébergés nœuds) pour répondre à toute augmentation de la demande. Avec la mise à l’échelle, l’application peut être configurée pour ajuster automatiquement le nombre de nœuds qui héberge l’application en fonction de la demande et la charge moyenne entre les nœuds.

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps for Containers

Outre la prise en charge pour l’hébergement d’applications web directement, [App Service Web Apps for Containers](https://azure.microsoft.com/services/app-service/containers/) peut être utilisé pour exécuter des applications en conteneur sur Windows et Linux. À l’aide de ce service, vous pouvez facilement déployer et exécuter des applications en conteneur capable d’évoluer avec votre entreprise. Les applications ont toutes les fonctionnalités d’App Service Web Apps répertoriés ci-dessus. En outre, les applications Web pour la prise en charge des conteneurs rationalisé CI/CD avec Docker Hub, Azure Container Registry et GitHub. Vous pouvez utiliser Azure DevOps pour définir les pipelines de build et de déploiement qui publient des modifications à un Registre. Ces modifications peuvent ensuite être testées dans un environnement intermédiaire et être automatiquement déployées en production à l’aide d’emplacements de déploiement, ce qui permet des mises à niveau sans interruption de service. Restauration dans les versions précédentes est possible aussi facilement.

Il existe quelques scénarios où les applications Web pour conteneurs les plus pertinentes. Si vous avez des applications existantes, vous pouvez mettre en conteneur, que ce soit dans les conteneurs Windows ou Linux, vous pouvez héberger facilement à l’aide de cet ensemble d’outils. Il vous suffit de publier votre conteneur, puis configurez Web Apps for Containers à extraire la dernière version de cette image de votre Registre de choix. C’est une approche « lift and shift » à la migration à partir de modèles à un modèle optimisé pour le cloud d’hébergement d’application classique.

![Migration d’une application .NET en conteneur en local à Azure Web Apps for Containers](./media/image1-8.png)

Cette approche fonctionne également bien si votre équipe de développement est en mesure de déplacer vers un processus de développement basé sur le conteneur. La « boucle intérieure » de développement d’applications avec des conteneurs inclut la création de l’application avec des conteneurs. Les modifications apportées au code, ainsi que la configuration du conteneur sont envoyées au contrôle de code source, et une build automatisée est responsable de la publication de nouvelles images de conteneur à un Registre tel que Docker Hub ou Azure Container Registry. Ces images sont ensuite utilisés comme base pour le développement supplémentaire, ainsi que pour les déploiements en production, comme indiqué dans le diagramme suivant :

![Cycle de vie du flux de travail DevOps Docker de bout en bout](./media/image1-7.png)

Développement avec des conteneurs offre de nombreux avantages, notamment lorsque les conteneurs sont utilisés en production. La même configuration du conteneur est utilisée pour héberger l’application dans chaque environnement dans lequel elle s’exécute, à partir de l’ordinateur de développement local pour générer et tester des systèmes de production. Cela réduit considérablement la probabilité d’erreurs résultant de différences dans la configuration de l’ordinateur ou les versions logicielles. Les développeurs peuvent utiliser également les outils ils sont plus productifs avec, notamment le système d’exploitation, dans la mesure où les conteneurs peuvent s’exécuter sur n’importe quel système d’exploitation. Dans certains cas, les applications distribuées impliquant de nombreux conteneurs peuvent être très gourmandes en ressources pour s’exécuter sur un seul ordinateur de développement. Dans ce scénario, il peut être judicieux pour mettre à niveau à l’aide de Kubernetes et les espaces de développement Azure, décrite dans la section suivante.

Comme les parties d’applications de grande taille sont divisés en leurs propres plus petit, indépendants *microservices*, modèles de conception supplémentaires peuvent être utilisés pour améliorer le comportement de l’application. Au lieu de travailler directement avec les services individuels, un *passerelle API* peut simplifier l’accès et pour découpler le client à partir de son serveur principal. Disposer d’un service distinct back-end pour les serveurs frontaux différents permet également aux services d’évoluer de concert avec leurs clients. Services communs sont accessibles via un distinct *side-car* conteneur, ce qui peut inclure les bibliothèques de connectivité client courantes à l’aide de la *Ambassadeur* modèle.

![Microservices exemple d’architecture avec plusieurs modèles de conception courants indiqués.](./media/image1-10.png)

[En savoir plus sur les modèles de conception à prendre en compte lors de la création de systèmes basés sur des microservices.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) gère votre environnement Kubernetes hébergé, ce qui vous permet de déployer et de gérer de manière simple et rapide les applications en conteneur sans pour autant maîtriser l’orchestration de conteneurs. Il élimine aussi les contraintes liées aux opérations et à la maintenance continues en provisionnant, en mettant à niveau et en mettant à l’échelle les ressources à la demande, sans déconnecter vos applications.

AKS réduit la complexité et les frais de fonctionnement liés à la gestion d’un cluster Kubernetes en déléguant une grande partie de cette responsabilité à Azure. En tant que service Kubernetes hébergé, Azure gère les tâches critiques à votre place, notamment l’analyse du fonctionnement et la maintenance. Par ailleurs, vous payez uniquement pour les nœuds d’agent de vos clusters, pas pour les maîtres. En tant que service Kubernetes géré, AKS fournit :

- Des mises à niveau de version et des mises à jour correctives Kubernetes automatisées.
- Une mise à l’échelle simplifiée des clusters.
- Un plan de contrôle hébergé avec auto-réparation (maîtres).
- Une réduction des coûts : vous payez uniquement pour les nœuds de pool d’agents qui s’exécutent.

La gestion des nœuds de votre cluster AKS étant assurée par Azure, vous n’avez plus besoin d’effectuer de nombreuses tâches manuelles, comme les mises à niveau de cluster. Comme Azure gère ces tâches de maintenance critiques à votre place, AKS ne fournit pas d’accès direct (comme avec SSH) au cluster.

Les équipes qui tirent parti de AKS peuvent également tirer parti d’Azure Dev espaces. Les espaces de développement Azure permettent aux équipes de se concentrer sur le développement et une itération rapide de leur application de microservice en permettant aux équipes de travailler directement avec leur architecture de microservices entière ou une application en cours d’exécution dans ACS. Les espaces de développement Azure fournit également un moyen pour mettre à jour indépendamment les parties de votre architecture de microservices de manière isolée sans affecter le reste du cluster AKS ou d’autres développeurs.

![Exemple de flux de travail des espaces de développement Azure](./media/image1-9.gif)

Espaces de développement Azure :

- Réduisez les exigences de temps et de ressources de configuration ordinateur local
- Autoriser les équipes effectuer une itération plus rapidement
- Réduire le nombre d’environnements d’intégration requis par l’équipe
- Remove devons simuler certains services dans un système distribué lors du développement/test

[En savoir plus sur les espaces de développement Azure](https://docs.microsoft.com/azure/dev-spaces/about)

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

- Architecture\ d’Application Web Azure de base
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Modèles de conception pour Microservices\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

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
