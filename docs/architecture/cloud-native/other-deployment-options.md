---
title: Autres options de déploiement de conteneur
description: Autres options de déploiement de conteneur à l’aide d’Azure
ms.date: 05/13/2020
ms.openlocfilehash: 2eac822b74af636e0ab0ed24b58eb7139526f4a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163620"
---
# <a name="other-container-deployment-options"></a>Autres options de déploiement de conteneur

À part le service Azure Kubernetes (AKS), vous pouvez également déployer des conteneurs sur Azure App Service pour les conteneurs et les Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Quand est-il logique d’effectuer le déploiement sur App Service pour les conteneurs ?

Les applications de production simples qui ne nécessitent pas d’orchestration sont bien adaptées à Azure App Service pour les conteneurs.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Comment effectuer un déploiement vers App Service pour les conteneurs

Pour déployer sur [Azure App service pour les conteneurs](https://azure.microsoft.com/services/app-service/containers/), vous avez besoin d’une instance Azure Container Registry (ACR) et des informations d’identification pour y accéder. Poussez votre image conteneur vers le référentiel ACR pour qu’elle puisse être extraite dans votre Azure App Service. Une fois l’opération terminée, vous pouvez configurer l’application pour un déploiement continu. Cela a pour effet de déployer automatiquement les mises à jour chaque fois que l’image change dans ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Quand est-il logique d’effectuer le déploiement sur Azure Container Instances ?

[Azure Container instances (ACI)](https://azure.microsoft.com/services/container-instances/) vous permet d’exécuter des conteneurs de l’ancrage dans un environnement Cloud géré sans serveur, sans avoir à configurer des machines virtuelles ou des clusters. Il s’agit d’une solution idéale pour les charges de travail à exécution rapide qui peuvent s’exécuter dans un conteneur isolé. Pensez à Analog pour les services simples, les scénarios de test, l’automatisation des tâches et les travaux de génération. ACI crée une instance de conteneur, exécute la tâche, puis la fait pivoter.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Comment déployer une application sur Azure Container Instances

Pour déployer sur [Azure Container instances (ACI)](/azure/container-instances/), vous avez besoin d’un Azure Container Registry (ACR) et des informations d’identification pour y accéder. Une fois que vous avez envoyé votre image conteneur vers le référentiel, elle est disponible pour une extraction dans ACI. Vous pouvez travailler avec ACI à l’aide de la Portail Azure ou de l’interface de ligne de commande. ACR offre une intégration étroite avec ACI. La figure 3-14 montre comment envoyer une image de conteneur individuelle à ACR.

![Azure Container Registry exécuter l’instance](./media/acr-runinstance-contextmenu.png)

**Figure 3-14**. Azure Container Registry exécuter l’instance

La création d’une instance dans ACI peut être effectuée rapidement. Spécifiez le registre d’images, les informations de groupe de ressources Azure, la quantité de mémoire à allouer et le port sur lequel écouter. Ce guide [de démarrage rapide montre comment déployer une instance de conteneur dans ACI à l’aide de la portail Azure](/azure/container-instances/container-instances-quickstart-portal).

Une fois le déploiement terminé, recherchez l’adresse IP du conteneur qui vient d’être déployé et communiquez avec celle-ci sur le port que vous avez spécifié.

Azure Container Instances offre le moyen le plus rapide d’exécuter des charges de travail de conteneur simples dans Azure. Vous n’avez pas besoin de configurer un app service, Orchestrator ou une machine virtuelle. Pour les scénarios où vous avez besoin d’une orchestration de conteneur complète, d’une détection de service, d’une mise à l’échelle automatique ou de mises à niveau coordonnées, nous vous recommandons le service Azure Kubernetes (AKS).

## <a name="references"></a>Références

- [Qu’est-ce que Kubernetes ?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Installation de Kubernetes avec Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube et bureau de l’ancrage](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools pour Docker](/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [Fonctionnement du démarrage à froid sans serveur](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Instances de Azure Functions préchauffées](/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Créer une fonction sur Linux en utilisant une image personnalisée](/azure/azure-functions/functions-create-function-linux-custom-image)
- [Exécuter Azure Functions dans un conteneur d’ancrage](https://markheath.net/post/azure-functions-docker)
- [Créer une fonction sur Linux en utilisant une image personnalisée](/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions avec la mise à l’échelle automatique pilotée par les événements Kubernetes](/azure/azure-functions/functions-kubernetes-keda)
- [Version de la Canaries](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces avec VS Code](/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces avec Visual Studio](/azure/dev-spaces/quickstart-netcore-visualstudio)
- [AKS plusieurs pools de nœuds](/azure/aks/use-multiple-node-pools)
- [Mise à l’échelle automatique du cluster AKS](/azure/aks/cluster-autoscaler)
- [Didacticiel : mettre à l’échelle des applications dans AKS](/azure/aks/tutorial-kubernetes-scale)
- [Échelle et hébergement dans Azure Functions](/azure/azure-functions/functions-scale)
- [Documentation Azure Container Instances](/azure/container-instances/)
- [Déployer une instance de conteneur à partir de ACR](/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Précédent](scale-containers-serverless.md) 
> [Suivant](communication-patterns.md)
