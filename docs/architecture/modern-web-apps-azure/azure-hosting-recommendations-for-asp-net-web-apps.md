---
title: Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Recommandations sur l’hébergement Azure pour les applications web ASP.NET
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
ms.openlocfilehash: c209a7fa9ce89e12466424f750d5583a59f8b980
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851716"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Recommandations sur l’hébergement Azure pour les applications web ASP.NET Core

> « Les leaders métier ne passent plus par les départements informatiques pour obtenir des applications du cloud (également appelées SaaS) et les paient comme ils paient un abonnement à un magazine. Quand ils n’ont plus besoin du service, ils peuvent annuler l’abonnement sans se retrouver avec du matériel inutilisé dans un coin. »  
> _\- Daryl Plummer, analyste Gartner_

Quels que soient les besoins et l’architecture de votre application, Microsoft Azure peut la prendre en charge. Vos besoins d’hébergement peuvent être aussi simples que ceux d’un site web statique ou aussi complexes que ceux d’une application sophistiquée constituée de dizaines de services. Pour les applications ASP.NET Core monolithiques et les services qui les prennent en charge, il existe plusieurs configurations connues qui sont recommandées. Les suggestions présentées dans cet article sont regroupées en fonction du type de ressource à héberger, qu’il s’agisse d’applications complètes, de processus individuels ou de données.

## <a name="web-applications"></a>Applications web

Les applications web peuvent être hébergées avec :

- App Service Web Apps

- Conteneurs (plusieurs options)

- Machines virtuelles (VM)

Entre tous, App Service Web Apps constitue l’approche recommandée pour la plupart des scénarios, y compris les applications conteneur simples. Pour les architectures de microservices, envisagez une approche basée sur les conteneurs. Si vous avez besoin de contrôler davantage les machines qui exécutent votre application, envisagez le service Machines virtuelles Azure.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps offre une plateforme entièrement managée, optimisée pour l’hébergement d’applications web. Il s’agit d’une offre de plateforme PaaS qui vous permet de vous concentrer sur votre logique métier, tandis qu’Azure fournit l’infrastructure nécessaire pour exécuter et mettre à l’échelle l’application. Voici quelques fonctionnalités clés d’App Service Web Apps :

- Optimisation de DevOps (intégration et livraison continues, environnements multiples, tests A/B, prise en charge des scripts).

- Échelle globale et haute disponibilité.

- Connexions aux plateformes SaaS et à vos données locales.

- Sécurité et conformité.

- Intégration Visual Studio.

Azure App Service est le meilleur choix pour la plupart des applications web. Le déploiement et la gestion sont intégrés à la plateforme, les sites peuvent rapidement gérer des volumes importants de trafic et le gestionnaire d'équilibrage de charge et de trafic assurent une haute disponibilité. Vous pouvez déplacer facilement des sites existants vers Azure App Service à l’aide d’un outil de migration en ligne. Vous pouvez utiliser une application open source à partir de la Galerie d’applications Web ou créer un nouveau site à l’aide de l’infrastructure et des outils de votre choix. La fonctionnalité WebJobs facilite l’ajout du traitement de travaux en arrière-plan à votre application web App Service. Si une application ASP.NET existante est hébergée en local à l’aide d’une base de données locale, il existe un chemin d’accès clair à migrer. Vous pouvez utiliser App Service application Web avec un Azure SQL Database (ou un accès sécurisé à votre serveur de base de données local, si vous le préférez).

![Stratégie de migration recommandée pour les applications .NET locales vers Azure App Service](./media/image1-6.png)

Dans la plupart des cas, le déplacement d’une application ASP.NET hébergée localement vers une application web App Service est un processus simple. Peu, voire aucune, modification de l’application proprement dite devraient être nécessaires, et elle peut rapidement commencer à tirer parti des nombreuses fonctionnalités offertes par Azure App Service Web Apps.

En plus des applications qui ne sont pas optimisées pour le cloud, Azure App Service Web Apps est une excellente solution pour de nombreuses applications monolithiques (non distribuées) simples, telles que de nombreuses applications ASP.NET Core. Avec cette approche, l’architecture est simple à comprendre et à gérer :

![Architecture Azure de base](./media/image1-5.png)

Un petit nombre de ressources dans un seul groupe de ressources suffit généralement pour gérer une telle application. Les applications qui sont généralement déployées en tant qu’unité unique, plutôt que celles constituées de nombreux processus distincts, sont de bonnes candidates pour cette [approche architecturale de base](/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). Bien que simple d’un point de vue architectural, cette approche permet quand même d’effectuer un scale up (plus de ressources par nœud) et un scale out (plus de nœuds hébergés) de l’application hébergée afin de répondre à toute augmentation de la demande. Avec la mise à l’échelle automatique, l’application peut être configurée pour ajuster automatiquement le nombre de nœuds qui l’hébergent en fonction de la demande et de la charge moyenne entre les nœuds.

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps for Containers

Outre la prise en charge de l’hébergement direct d’applications web, [App Service Web Apps for Containers](https://azure.microsoft.com/services/app-service/containers/) peut être utilisé pour exécuter des applications en conteneur sur Windows et Linux. À l’aide de ce service, vous pouvez facilement déployer et exécuter des applications en conteneur capables d’évoluer avec votre entreprise. Les applications disposent de toutes les fonctionnalités d’App Service Web Apps mentionnées plus haut. En outre, les Web Apps pour les conteneurs prennent en charge l’intégration continue et le déploiement de CD simplifiés avec le Hub, Azure Container Registry et GitHub. Vous pouvez utiliser Azure DevOps pour définir des pipelines de génération et de déploiement qui publient des modifications dans un registre. Ces modifications peuvent ensuite être testées dans un environnement intermédiaire et être déployées automatiquement en production à l’aide d’emplacements de déploiement, ce qui permet d’effectuer des mises à niveau sans temps d’arrêt. La restauration vers des versions précédentes est possible tout aussi facilement.

Dans certains scénarios, Web Apps pour les conteneurs est le plus judicieux. Si vous avez des applications que vous pouvez mettre en conteneur, que ce soit dans des conteneurs Windows ou Linux, vous pouvez les héberger facilement à l’aide de cet ensemble d’outils. Publiez simplement votre conteneur, puis configurez Web Apps pour que les conteneurs extraient la version la plus récente de cette image de votre registre de votre choix. Il s’agit d’une approche « lift and shift » de la migration à partir de modèles d’hébergement d’applications classiques vers un modèle optimisé pour le cloud.

![Migrer une application .NET locale en conteneur vers Azure Web Apps for Containers](./media/image1-8.png)

Cette approche fonctionne également bien si votre équipe de développement est capable de basculer vers un processus de développement basé sur conteneur. La « boucle interne » du développement d’applications avec conteneurs comprend la création de l’application avec des conteneurs. Les modifications apportées au code, ainsi qu’à la configuration du conteneur, sont envoyées au contrôle de code source, et une build automatisée est responsable de la publication des nouvelles images de conteneurs vers un registre tel que Docker Hub ou Azure Container Registry. Ces images sont ensuite utilisées comme base pour les tâches de développement supplémentaires, ainsi que pour les déploiements en production, comme indiqué dans le diagramme suivant :

![Flux de travail de cycle de vie DevOps Docker de bout en bout](./media/image1-7.png)

Le développement avec des conteneurs offre de nombreux avantages, notamment quand les conteneurs sont utilisés en production. La même configuration de conteneur est utilisée pour héberger l’application dans chaque environnement dans lequel elle s’exécute, depuis l’ordinateur de développement local pour créer et tester des systèmes en production. Cette approche réduit considérablement la probabilité de défauts résultant de différences dans la configuration de l’ordinateur ou les versions des logiciels. Les développeurs peuvent également utiliser les outils avec lesquels ils sont les plus productifs, y compris le système d’exploitation, puisque les conteneurs peuvent s’exécuter sur n’importe quel système d’exploitation. Dans certains cas, l’exécution sur un seul ordinateur de développement d’applications distribuées impliquant de nombreux conteneurs peut être très gourmande en ressources. Dans ce scénario, il peut être judicieux d’utiliser plutôt Kubernetes et Azure Dev Spaces, qui sont décrits dans la section suivante.

À mesure que les différentes parties des applications de grande taille sont divisées en leurs propres *microservices* plus petits et indépendants, vous pouvez recourir à des modèles de conception supplémentaires pour améliorer le comportement de l’application. Au lieu de travailler directement avec chacun des services, vous pouvez utiliser une *passerelle API* pour simplifier l’accès et découpler le client de son back-end. Disposer de back-ends de services distincts pour différents front-ends permet également aux services d’évoluer de concert avec leurs consommateurs. Les services communs sont accessibles par le biais d’un conteneur *sidecar* distinct, qui peut inclure des bibliothèques de connectivité client courantes avec le modèle *ambassadeur*.

![Exemple d’architecture de microservices avec plusieurs modèles de conception courants indiqués.](./media/image1-10.png)

[Apprenez-en davantage sur les modèles de conception à prendre en compte lors de la création de systèmes basés sur des microservices.](/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) gère votre environnement Kubernetes hébergé, accélérant et facilitant ainsi le déploiement et la gestion des applications conteneurisées sans expertise d’orchestration de conteneur. Cela élimine également le fardeau des opérations et de la maintenance en cours en approvisionnant, en mettant à niveau et en mettant à l’échelle les ressources à la demande, sans mettre vos applications hors connexion.

AKS permet de réduire la complexité et la surcharge opérationnelle de la gestion d’un cluster Kubernetes en déléguant une grande partie de cette responsabilité à Azure. En tant que service Kubernetes hébergé, Azure gère pour vous des tâches critiques telles que l’analyse de l'intégrité et la maintenance. Par ailleurs, vous payez uniquement pour les nœuds d’agent de vos clusters, pas pour les maîtres. En tant que service Kubernetes géré, AKS fournit :

- Des mises à niveau de version et des mises à jour correctives Kubernetes automatisées.
- Une mise à l’échelle simplifiée des clusters.
- Un plan de contrôle hébergé avec auto-réparation (maîtres).
- Une réduction des coûts : vous payez uniquement pour les nœuds de pool d’agents qui s’exécutent.

Comme Azure gère la gestion des nœuds de votre cluster AKS, vous n’avez plus besoin d'effectuer les tâches manuellement, notamment les mises à niveau du cluster. Comme Azure gère ces tâches de maintenance critiques à votre place, AKS ne fournit pas d’accès direct (comme avec SSH) au cluster.

Les équipes qui tirent parti d’AKS peuvent également tirer parti d’Azure Dev Spaces. Grâce à Azure Dev Spaces, les équipes peuvent se concentrer sur le développement et l’itération rapide de leur application de microservices en exploitant directement leur architecture complète de microservices ou une application en cours d’exécution dans AKS. Azure Dev Spaces permet également de mettre à jour de façon indépendante certaines parties de votre architecture de microservices, sans affecter le reste du cluster AKS ou d’autres développeurs.

![Exemple de flux de travail Azure Dev Spaces](./media/image1-9.gif)

Azure Dev Spaces :

- Limite le temps et les ressources nécessaires pour configurer l’ordinateur local.
- Permet aux équipes d’effectuer une itération plus rapidement.
- Réduire le nombre d’environnements d’intégration requis par une équipe
- Éliminez la nécessité de simuler certains services dans un système distribué lors du développement et du test

[En savoir plus sur Azure Dev Spaces](/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Machines virtuelles Azure

Si vous avez une application existante qui nécessite des modifications substantielles pour s’exécuter dans App Service, vous pouvez choisir Machines virtuelles afin de simplifier la migration vers le cloud. Cependant, la configuration, la sécurisation et la gestion des machines virtuelles nécessitent beaucoup plus de temps et d’expertise en informatique comparé à Azure App Service. Si vous envisagez d’utiliser Machines virtuelles Azure, veillez à prendre en compte le travail continu de maintenance nécessaire pour appliquer les correctifs, mettre à jour et gérer votre environnement de machines virtuelles. Machines virtuelles Azure est une infrastructure IaaS, tandis qu’App Service est une plateforme Paas. Vous devez également déterminer si le déploiement de votre application comme conteneur Windows dans Web App pour conteneurs est une option viable pour votre scénario.

## <a name="logical-processes"></a>Processus logiques

Les processus logiques individuels qui peuvent être dissociés du reste de l’application peuvent être déployés indépendamment sur Azure Functions de manière « serveless ». Azure Functions vous permet de simplement écrire le code dont vous avez besoin pour un problème donné, sans se préoccuper de l’application ou de l’infrastructure pour l’exécuter. Vous pouvez choisir parmi une variété de langages de programmation, notamment C\#, F\#, Node.js, Python et PHP, ce qui vous permet de choisir le langage le plus productif pour la tâche à traiter. Comme la plupart des solutions cloud, vous payez seulement pour la durée de votre utilisation, et vous pouvez faire confiance à Azure Functions pour monter en puissance au fil des besoins.

## <a name="data"></a>Données

Azure propose un large éventail d’options de stockage des données, afin que votre application puisse utiliser le fournisseur de données approprié pour les données en question.

Pour les données transactionnelles relationnelles, les bases de données Azure SQL Database sont la meilleure option. Pour de hautes performances avec les données qui sont principalement en lecture, un cache Redis s’appuyant sur une base de données Azure SQL Database est une bonne solution.

Les données JSON non structurées peuvent être stockées de différentes façons, de SQL Database des colonnes aux objets BLOB ou aux tables dans le stockage Azure, pour Azure Cosmos DB. Azure Cosmos DB offre les meilleures fonctionnalités d’interrogation et est l’option recommandée pour un grand nombre de documents JSON qui doivent prendre en charge l’interrogation.

Les données basées sur des commandes ou des événements transitoires pour orchestrer le comportement des applications peuvent utiliser Azure Service Bus ou Stockage File d’attente Azure. Azure Service Bus offre plus de souplesse et est le service recommandé pour la messagerie non triviale au sein et entre les applications.

## <a name="architecture-recommendations"></a>Suggestions en matière d’architecture

Les exigences de votre application doivent dicter son architecture. Il existe de nombreux services Azure différents. Aussi, il est important de choisir le bon. Microsoft propose une galerie d’architectures de référence pour aider à identifier des architectures classiques optimisées pour les scénarios courants. Vous pouvez adopter une architecture de référence qui correspond de près aux exigences de votre application ou qui constitue au moins un point de départ.

La figure 11-1 illustre un exemple d’architecture de référence. Ce diagramme décrit une approche recommandée pour l’architecture d’un site web de système de gestion de contenu Sitecore optimisé pour le marketing.

![Figure 11-1](./media/image11-2.png)

**Figure 11-1.** Architecture de référence d’un site web de marketing Sitecore.

**Références : recommandations relatives à l’hébergement Azure**

- Architectures de solutions Azure\
  <https://azure.microsoft.com/solutions/architecture/>

- Architecture d’application web Azure de base\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Modèles de conception pour microservices\
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
