---
title: Gérer des environnements de production Docker
description: Découvrez les points clés de la gestion d’un environnement de production basé sur un conteneur.
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834506"
---
# <a name="manage-production-docker-environments"></a>Gérer des environnements de production Docker

La gestion et l’orchestration d’un cluster constituent le processus consistant à contrôler un groupe d’hôtes. Ce processus peut impliquer l’ajout et la suppression d’hôtes dans un cluster, l’obtention d’informations sur l’état actuel des hôtes et des conteneurs et le démarrage et l’arrêt de processus. La gestion et l’orchestration d’un cluster sont étroitement liées à la planification, car le planificateur doit avoir accès à chaque hôte du cluster pour planifier les services. Pour cette raison, le même outil est souvent utilisé pour ces deux tâches.

## <a name="container-service-and-management-tools"></a>Container Service et outils de gestion

Container Service assure le déploiement rapide des principales solutions de mise en cluster et d’orchestration de containers open source. Il tire parti des images Docker pour garantir la portabilité complète de vos conteneurs d’application. À l’aide de Container Service, vous pouvez déployer des clusters Docker Swarm et DC/OS (technologie Mesosphere et Apache Mesos) à l’aide de modèles Azure Resource Manager ou du portail Azure afin de pouvoir faire évoluer ces applications dans des proportions allant jusqu’à des milliers, voire des dizaines de milliers, de conteneurs.

Vous déployez ces clusters à l’aide d’Azure Virtual Machine Scale Sets, et les clusters tirent parti des offres de stockage et de mise en réseau Azure. Pour accéder à Container Service, vous devez disposer d’un abonnement Azure. Avec Container Service, vous pouvez bénéficier des fonctionnalités de niveau entreprise d’Azure, tout en conservant la portabilité des applications, notamment au niveau des couches d’orchestration.

Le tableau 6-1 indique les outils de gestion courants ainsi que les orchestrateurs, planificateurs et plateforme de clustering correspondants.

**Tableau 6-1**. Outils de gestion Docker

| Outils de gestion | Description | Orchestrateurs correspondants |
|------------------|-------------|-----------------------|
| [Azure Monitor pour conteneurs](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Outil de gestion Kubernetes dédié à Azure | Azure Kubernetes Services (AKS) |
| [Interface utilisateur web de Kubernetes (tableau de bord)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Outil de gestion Kubernetes, qui peut superviser et gérer un cluster Kubernetes local | Azure Kubernetes Service (AKS)<br/>Kubernetes local |
| [Portail Azure pour Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Version en ligne et de poste de travail pour la gestion des clusters Service Fabric dans les clouds Azure, locaux, de développement local et autres | Azure Service Fabric |
| [Supervision des conteneurs (Azure Monitor)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Solution générale de gestion et de supervision de conteneurs. Peut gérer des clusters Kubernetes par le biais d’[Azure Monitor pour conteneurs](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS et autres. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Une autre option pour la gestion et le déploiement de cluster est Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) est une plateforme de microservices Microsoft qui inclut l’orchestration des conteneurs ainsi que des modèles de programmation permettant aux développeurs de générer des applications de microservices hautement scalables. Service Fabric prend en charge Docker dans les conteneurs Linux et Windows et peut s’exécuter sur les serveurs Windows et Linux.

Service Fabric outils d’administration sont les suivants :

- [Portail Azure pour Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) : permet d’effectuer les opérations liées à un cluster (création/mise à jour/suppression) ou de configurer son infrastructure (machines virtuelles, équilibreur de charge, réseau, etc.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) est un outil multiplateforme de poste de travail et d’interface utilisateur web spécialisé qui fournit des insights et certaines opérations sur le cluster Service Fabric, du point de vue des nœuds, des machines virtuelles, de l’application et des services.

>[!div class="step-by-step"]
>[Précédent](run-microservices-based-applications-in-production.md)
>[Suivant](monitor-containerized-application-services.md)
