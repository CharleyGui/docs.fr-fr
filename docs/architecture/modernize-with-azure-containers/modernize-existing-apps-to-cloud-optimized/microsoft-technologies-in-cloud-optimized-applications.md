---
title: Technologies Microsoft dans les applications Cloud-Optimized
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Technologies Microsoft dans les applications Cloud-Optimized
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69578222"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologies Microsoft dans les applications optimisées pour le cloud

La liste suivante décrit les outils, les technologies et les solutions qui sont reconnus comme des exigences pour les applications Cloud-Optimized. Vous pouvez adopter des éléments optimisés pour le Cloud de manière sélective ou graduelle, en fonction de vos priorités.

- **Infrastructure cloud**: L’infrastructure qui fournit la plate-forme de calcul, le système d’exploitation, le réseau et le stockage. Microsoft Azure est positionné à ce niveau.

- **Runtime**: Cette couche fournit l’environnement pour l’application à exécuter. Si vous utilisez des conteneurs, cette couche est généralement basée sur [Docker Engine](https://docs.docker.com/engine/), en cours d’exécution soit sur les hôtes Linux ou sur les hôtes Windows. ([Les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) sont pris en charge à partir de Windows Server 2016. Windows Containers est le meilleur choix pour les applications cadres .NET existantes qui s’exécutent sur Windows.)

- **Cloud géré**: Lorsque vous choisissez une option cloud gérée, vous pouvez éviter les dépenses et la complexité de la gestion et du support de l’infrastructure sous-jacente, des machines virtuelles, des correctifs OS et de la configuration du réseautage. Si vous choisissez de migrer en utilisant IaaS, vous êtes responsable de toutes ces tâches, et des coûts associés. Dans une option cloud gérée, vous ne gérez que les applications et services que vous développez. Le fournisseur de services cloud gère généralement tout le reste. Parmi les exemples de services cloud gérés chez Azure, citons [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/), et managed compute services like [VM scale sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure App Service](https://azure.microsoft.com/services/app-service/), et [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Développement d’applications**: Vous pouvez choisir parmi de nombreuses langues lorsque vous créez des applications qui s’exécutent dans des conteneurs. Ce guide se concentre sur [.NET](https://www.microsoft.com/net), mais, vous pouvez développer des applications basées sur des conteneurs en utilisant d’autres langues, comme Node.js, Python, Printemps / Java, ou Go.

- **Surveillance, télémétrie, enregistrement et audit**: La capacité de surveiller et d’auditer les applications et les conteneurs qui fonctionnent dans le cloud est essentielle pour toute application optimisée pour le Cloud. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) et [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) sont les principaux outils Microsoft qui fournissent la surveillance et l’audit pour les applications Cloud-Optimized.

- **Provisionnement**: Les outils d’automatisation vous aident à fournir l’infrastructure et à déployer une application dans plusieurs environnements (production, test, mise en scène). Vous pouvez utiliser des outils comme Chef et Puppet pour gérer la configuration et l’environnement d’une application. Cette couche peut également être mise en œuvre en utilisant des approches plus simples et plus directes. Par exemple, vous pouvez vous déployer directement en utilisant l’outillage de l’interface de ligne de commande Azure (Azure CLI), puis utiliser les pipelines de déploiement et de gestion des versions continus dans [Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Cycle de vie des applications**: [Azure DevOps Services](https://azure.microsoft.com/services/devops/) et d’autres outils, comme Jenkins, sont des serveurs d’automatisation construits qui vous aident à mettre en œuvre des pipelines CI/CD, y compris la gestion des versions.

Les sections suivantes de ce chapitre, et les procédures à pas connexes, se concentrent spécifiquement sur les détails sur la couche de temps d’exécution (Windows Containers). Les conseils décrivent comment vous pouvez déployer des conteneurs Windows sur Windows Server 2016 (et les versions ultérieures) VMs et Azure Container Instances. Il couvre également des plates-formes PaaS plus avancées comme Azure App Service et orchestrateur comme Azure Kubernetes Service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Les applications monolithiques *peuvent* être optimisées en nuage

Il est important de souligner que les applications monolithiques (applications qui ne sont pas basées sur les microservices) *peuvent* être des applications optimisées pour le Cloud. Vous pouvez construire et exploiter des applications monolithiques qui tirent parti du modèle de cloud computing en utilisant une combinaison de conteneurs, de livraison continue et de DevOps. Si une application monolithique existante convient à vos objectifs d’affaires, vous pouvez la moderniser et la rendre optimisée pour le Cloud.

De même, si les applications monolithiques peuvent être des applications optimisées pour le Cloud, d’autres architectures plus complexes comme les applications N-Tier peuvent également être modernisées sous forme d’applications optimisées pour le Cloud.

>[!div class="step-by-step"]
>[Suivant précédent](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[Next](what-about-cloud-native-applications.md)
