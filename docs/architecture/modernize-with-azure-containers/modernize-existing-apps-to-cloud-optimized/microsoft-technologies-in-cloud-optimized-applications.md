---
title: Technologies Microsoft dans les applications optimisées pour le Cloud
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Technologies Microsoft dans les applications optimisées pour le Cloud
ms.date: 04/28/2018
ms.openlocfilehash: b257497835638dd65c894998e95bd7e9d784b7bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172012"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologies Microsoft dans les applications optimisées pour le Cloud

La liste suivante décrit les outils, les technologies et les solutions qui sont reconnus comme exigences pour les applications optimisées pour le Cloud. Vous pouvez adopter des éléments optimisés pour le Cloud de manière sélective ou progressive, en fonction de vos priorités.

- **Infrastructure cloud**: infrastructure qui fournit la plateforme de calcul, le système d’exploitation, le réseau et le stockage. Microsoft Azure est positionné à ce niveau.

- **Runtime**: cette couche fournit l’environnement pour l’exécution de l’application. Si vous utilisez des conteneurs, cette couche est généralement basée sur le moteur de l' [ancrage](https://docs.docker.com/engine/), en cours d’exécution sur les hôtes Linux ou sur les hôtes Windows. (Les[conteneurs Windows](/virtualization/windowscontainers/about/) sont pris en charge à partir de windows server 2016. Les conteneurs Windows constituent le meilleur choix pour les applications de .NET Framework existantes qui s’exécutent sur Windows.)

- **Cloud géré**: lorsque vous choisissez une option Cloud géré, vous pouvez éviter les dépenses et la complexité liées à la gestion et à la prise en charge de l’infrastructure sous-jacente, des machines virtuelles, des correctifs de système d’exploitation et de la configuration réseau. Si vous choisissez de migrer à l’aide d’IaaS, vous êtes responsable de toutes ces tâches et des coûts associés. Dans une option Cloud géré, vous gérez uniquement les applications et les services que vous développez. En général, le fournisseur de services Cloud gère tout le reste. Exemples de services Cloud gérés dans Azure : [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [cache redims Azure](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [stockage Azure](https://azure.microsoft.com/services/storage/), [Azure database pour MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database pour PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)et services de calcul gérés tels que les [groupes de machines virtuelles](https://azure.microsoft.com/services/virtual-machine-scale-sets/)identiques, [Azure App service](https://azure.microsoft.com/services/app-service/)et le [service Azure Kubernetes](https://azure.microsoft.com/services/container-service/).

- **Développement d’applications**: vous pouvez choisir parmi de nombreuses langues lorsque vous générez des applications qui s’exécutent dans des conteneurs. Ce guide se concentre sur [.net](https://dotnet.microsoft.com), mais vous pouvez développer des applications basées sur des conteneurs à l’aide d’autres langages, comme Node.js, Python, Spring/Java ou Go.

- **Surveillance, télémétrie, journalisation et audit**: la possibilité de surveiller et d’auditer les applications et les conteneurs qui s’exécutent dans le Cloud est essentielle pour n’importe quelle application optimisée pour le Cloud. [Azure application Insights](https://azure.microsoft.com/services/application-insights/) et [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) sont les principaux outils Microsoft qui fournissent des analyses et des audits pour les applications optimisées pour le Cloud.

- **Approvisionnement**: les outils d’automatisation vous aident à approvisionner l’infrastructure et à déployer une application dans plusieurs environnements (production, test, mise en lots). Vous pouvez utiliser des outils tels que chef et marionnette pour gérer la configuration et l’environnement d’une application. Cette couche peut également être implémentée à l’aide d’approches plus simples et plus directes. Par exemple, vous pouvez déployer directement à l’aide des outils de l’interface de ligne de commande (Azure CLI) Azure, puis utiliser les pipelines de déploiement continu et de gestion des versions dans [Azure DevOps services](https://azure.microsoft.com/services/devops/).

- **Cycle de vie**de l’Application : [Azure DevOps services](https://azure.microsoft.com/services/devops/) et d’autres outils, tels que Jenkins, sont des serveurs Automation intégrés qui vous aident à implémenter des pipelines ci/CD, y compris la gestion des versions.

Les sections suivantes de ce chapitre, ainsi que les procédures pas à pas associées, portent spécifiquement sur les détails de la couche Runtime (conteneurs Windows). L’aide décrit les manières de déployer des conteneurs Windows sur des machines virtuelles Windows Server 2016 (et versions ultérieures) et des Azure Container Instances. Il couvre également des plateformes PaaS plus avancées, telles que Azure App Service et Orchestrator, comme Azure Kubernetes service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Les applications monolithiques *peuvent* être optimisées pour le Cloud

Il est important de souligner que les applications monolithiques (les applications qui ne sont pas basées sur des microservices) *peuvent* être des applications optimisées pour le Cloud. Vous pouvez créer et utiliser des applications monolithiques qui tirent parti du modèle de cloud computing à l’aide d’une combinaison de conteneurs, d’une livraison continue et de DevOps. Si une application monolithique existante est adaptée à vos objectifs professionnels, vous pouvez la moderniser et la rendre optimisée pour le Cloud.

De même, si des applications monolithiques peuvent être des applications optimisées pour le Cloud, d’autres architectures plus complexes telles que des applications multiniveaux peuvent également être modernisées en tant qu’applications optimisées pour le Cloud.

>[!div class="step-by-step"]
>[Précédent](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md) 
> [Suivant](what-about-cloud-native-applications.md)
