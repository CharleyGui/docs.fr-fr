---
title: Technologies Microsoft dans les applications optimisé pour le Cloud
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Technologies Microsoft dans les applications optimisé pour le Cloud
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758632"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologies Microsoft dans les applications optimisé pour le cloud

La liste suivante décrit les outils, les technologies et les solutions qui sont reconnues comme configuration requise pour les applications optimisé pour le Cloud. Vous pouvez adopter progressivement, ou de manière sélective aux éléments optimisé pour le Cloud selon vos priorités.

- **Infrastructure de cloud**: L’infrastructure qui fournit la plateforme de calcul, le système d’exploitation, le réseau et le stockage. Microsoft Azure est positionné à ce niveau.

- **Runtime**: Cette couche fournit l’environnement pour exécuter l’application. Si vous utilisez des conteneurs, cette couche est généralement basée sur [moteur Docker](https://docs.docker.com/engine/), en cours d’exécution sur les hôtes Linux ou sur des ordinateurs hôtes Windows. ([Windows conteneurs](https://docs.microsoft.com/virtualization/windowscontainers/about/) sont pris en charge depuis Windows Server 2016. Les conteneurs Windows est le meilleur choix pour les applications .NET Framework existantes qui s’exécutent sur Windows.)

- **Managed cloud**: Lorsque vous choisissez une option de cloud géré, vous pouvez éviter les dépenses et la complexité de gestion et de prise en charge les correctifs de système d’exploitation sous-jacent infrastructure, les machines virtuelles et de mise en réseau de configuration. Si vous choisissez de migrer à l’aide d’IaaS, vous êtes responsable de toutes ces tâches et pour les coûts associés. Une option cloud géré, vous permet de gérer uniquement les applications et les services que vous développez. Le fournisseur de services cloud gère habituellement tout le reste. Exemples de services de cloud géré dans Azure [base de données SQL Azure](https://azure.microsoft.com/services/sql-database), [Cache Redis Azure](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [stockage Azure](https://azure.microsoft.com/services/storage/), [Azure Database pour MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database pour PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)et gérés comme des services de calcul [mise à l’échelle de machine virtuelle définit](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure App Service](https://azure.microsoft.com/services/app-service/), et [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Développement d’applications**: Vous pouvez choisir parmi de nombreux langages lorsque vous générez des applications qui s’exécutent dans des conteneurs. Ce guide se concentre sur [.NET](https://www.microsoft.com/net), mais, vous pouvez développer des applications basées sur le conteneur à l’aide d’autres langages, tels que Node.js, Python, Spring/Java, vous pouvez aussi.

- **Analyse des données de télémétrie, journalisation et audit**: La possibilité pour la surveillez et auditez les applications et les conteneurs qui sont exécutent dans le cloud est essentielle pour n’importe quelle application optimisé pour le Cloud. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) et [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) sont les principaux outils de Microsoft qui fournissent une surveillance et d’audit pour les applications optimisé pour le Cloud.

- **Approvisionnement**: Outils d’automatisation vous permettent de configurer l’infrastructure et de déployer une application sur plusieurs environnements (production, test, de préproduction). Vous pouvez utiliser des outils tels que Chef et Puppet pour gérer la configuration d’une application et l’environnement. Cette couche peut également être implémentée à l’aide des approches plus simples et plus directes. Par exemple, vous pouvez déployer directement à l’aide d’interface de ligne de commande Azure (Azure CLI) des outils, puis utiliser le déploiement continu et mise en production des pipelines de gestion dans [Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Cycle de vie des applications**: [Les Services Azure DevOps](https://azure.microsoft.com/services/devops/) et autres outils, tels que Jenkins, sont des serveurs automation intégrées qui vous aident à mettre en œuvre les pipelines CI/CD, y compris la gestion de version.

Les sections suivantes de ce chapitre et les procédures pas à pas connexes, traitent spécifiquement de plus d’informations sur la couche d’exécution (conteneurs Windows). Le guide décrit les méthodes que vous pouvez déployer des machines virtuelles de conteneurs Windows sur Windows Server 2016 (et versions ultérieures) et Azure Container Instances. Il couvre également les plateformes PaaS plus avancés tels que Azure App Service et l’orchestrateur comme Azure Kubernetes Service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Les applications monolithiques *pouvez* être optimisé pour le Cloud

Il est important de souligner que les applications monolithiques (les applications qui ne sont pas basées sur des microservices) *pouvez* être optimisé pour le Cloud des applications. Vous pouvez créer et faire fonctionner des applications monolithiques qui tirent parti du cloud computing de modèle en utilisant une combinaison des conteneurs, la livraison continue et DevOps. Si une application monolithique existante est appropriée pour vos objectifs professionnels, vous pouvez il moderniser et le rendre optimisé pour le Cloud.

De même, si les applications monolithiques peuvent être optimisé pour le Cloud des applications, les architectures autres et plus complexes telles que des applications multicouches peuvent également être modernisées en tant qu’applications optimisé pour le Cloud.

>[!div class="step-by-step"]
>[Précédent](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[Suivant](what-about-cloud-native-applications.md)
