---
title: Workflow DevOps pour les applications Docker avec les outils Microsoft
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft (workflow DevOps avec les outils Microsoft)
ms.date: 08/06/2020
ms.openlocfilehash: 30c5066fa90d8792d8eef8f760dc63c00ce32130
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915210"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Workflow DevOps pour les applications Docker avec les outils Microsoft

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server et Azure Monitor fournissent un écosystème complet pour le développement et les opérations informatiques. Votre équipe dispose de tous les outils nécessaires pour gérer des projets et générer, tester et déployer rapidement des applications en conteneur.*

Avec Visual Studio et Azure DevOps Services dans le cloud, et Team Foundation Server au niveau local, les équipes de développement peuvent efficacement générer, tester et publier des applications en conteneur ciblant Windows ou Linux.

Les outils Microsoft peuvent automatiser le pipeline pour des implémentations spécifiques d’applications en conteneur (Docker, .NET Core ou toute combinaison avec d’autres plateformes) : builds globales et intégration continue (CI), tests avec Azure DevOps ou Team Foundation Server, déploiement continu (CD) dans les environnements Docker (développement, préproduction, production) et transmission de données analytiques sur les services à l’équipe de développement par le biais d’Azure Monitor. Chaque validation de code peut lancer une build (CI) et déployer automatiquement les services sur des environnements en conteneur spécifiques (CD).

Les développeurs et testeurs peuvent provisionner facilement et rapidement des environnements de développement et de test basés sur Docker similaires à des environnements de production au moyen de modèles dans Microsoft Azure.

La difficulté du développement d’applications en conteneur augmente de façon régulière en fonction de la complexité et des besoins en matière de scalabilité de l’entreprise. Les applications basées sur des architectures de microservices constituent un bon exemple de cette complexité. Pour réussir dans un tel environnement, votre projet doit automatiser le cycle de vie dans sa totalité : non seulement la build et le déploiement, mais aussi la gestion des versions et la collecte des données de télémétrie. Azure DevOps Services et Azure offrent les fonctionnalités suivantes :

- Gestion du code source Azure DevOps Services/Team Foundation Server (basée sur Git ou Team Foundation Version Control), planification Agile (Agile, Scrum et CMMI sont pris en charge), intégration continue, gestion des versions et autres outils pour les équipes Agile.

- Azure DevOps Services et Team Foundation Server incluent un écosystème puissant et en constante évolution des premières et des extensions tierces avec lesquelles vous pouvez facilement construire un pipeline d’intégration continue, de build, de test, de remise et de gestion des versions pour les microservices.

- Exécution de tests automatisés dans le cadre de votre pipeline de build dans Azure DevOps Services.

- Azure DevOps Services peut renforcer le cycle de vie DevOps en effectuant des remises sur plusieurs environnements : non seulement les environnements de production, mais aussi à des fins de test (expérimentation A/B, [versions « canary »](https://martinfowler.com/bliki/CanaryRelease.html), etc.).

- Les organisations peuvent facilement provisionner des conteneurs Docker à partir d’images privées stockées dans Azure Container Registry, ainsi que toute dépendance vis-à-vis de composants Azure (Data, PaaS, etc.) à l’aide de modèles Azure Resource Manager accessibles avec des outils familiers.

>[!div class="step-by-step"]
>[Précédent](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md) 
> [Suivant](docker-application-outer-loop-devops-workflow.md)
