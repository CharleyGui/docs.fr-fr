---
title: Autres options de déploiement de conteneur
description: Autres options de déploiement de conteneur à l’aide d’Azure
ms.date: 06/30/2019
ms.openlocfilehash: 1fcb57eedec8c9f5574fffcf409b316332032062
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214448"
---
# <a name="other-container-deployment-options"></a>Autres options de déploiement de conteneur

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

En plus du déploiement sur AKS, vous pouvez également déployer des conteneurs sur Azure App Service pour les conteneurs et les Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Quand est-il logique d’effectuer le déploiement sur App Service pour les conteneurs ?

Les applications de production simples qui ne nécessitent pas d’orchestration sont bien adaptées à Azure App Service pour les conteneurs.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Comment effectuer un déploiement vers App Service pour les conteneurs

Pour effectuer un déploiement sur [Azure App service pour les conteneurs](https://azure.microsoft.com/services/app-service/containers/), vous devez avoir configuré un Azure Container Registry (ACR) et des informations d’identification pour y accéder. Poussez le conteneur que vous souhaitez héberger dans le registre afin qu’il soit disponible pour l’extraction de votre Azure App Service. Une fois créé, vous pouvez configurer l’application pour un déploiement continu, qui déploie automatiquement les mises à jour de l’application chaque fois que vous mettez à jour son image correspondante dans ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Quand est-il logique d’effectuer le déploiement sur Azure Container Instances ?

Azure Container Instances sont utilisés de manière optimale pour les scénarios de test. Ils offrent un moyen rapide et simple de déployer une application sur une instance de conteneur hébergée dans le Cloud. Utilisez-les pour tester ou démo des applications lorsque vous n’avez pas besoin de la mise à l’échelle et des fonctionnalités d’orchestration offertes par Azure Kubernetes service.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Comment déployer une application sur Azure Container Instances

Pour déployer sur [Azure Container instances (ACI)](https://docs.microsoft.com/azure/container-instances/), vous devez avoir configuré un Azure Container Registry (ACR) et des informations d’identification pour y accéder. Vous devez également avoir préalablement envoyé votre image de conteneur dans le registre, afin qu’elle soit disponible pour une extraction dans ACI. Vous pouvez travailler avec ACI à l’aide de la Azure CLI ou via le portail. Les registres de conteneurs Azure facilitent le déploiement d’instances de conteneur individuelles dans ACI directement à partir du Registre, comme illustré dans la figure 3-14.

![Azure Container Registry exécuter l’instance](./media/acr-runinstance-contextmenu.png)

**Figure 3-14**. Azure Container Registry exécuter l’instance

La création d’une instance de conteneur à partir du Registre nécessite simplement que vous spécifiiez les paramètres Azure habituels (nom, abonnement, groupe de ressources et emplacement), la quantité de mémoire à allouer au conteneur et le port sur lequel il doit écouter. Ce guide [de démarrage rapide montre comment déployer une instance de conteneur dans ACI à l’aide de la portail Azure](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Une fois le déploiement terminé, recherchez l’adresse IP du conteneur qui vient d’être déployé et communiquez avec celle-ci sur le port que vous avez spécifié.

Azure Container Instances offre le moyen le plus rapide et le plus simple d’exécuter un conteneur dans Azure. Il n’est pas nécessaire de configurer un service d’application ou un orchestrateur, ni de gérer des machines virtuelles. Toutefois, en raison de sa simplicité, ACI doit principalement être utilisé à des fins de test. Si votre application nécessite une extensibilité automatique, plusieurs conteneurs configurés pour fonctionner ensemble, ou des fonctionnalités complexes supplémentaires, d’autres services Azure adaptés sont disponibles pour héberger votre application.

## <a name="references"></a>Références

- [Documentation Azure Container Instances](https://docs.microsoft.com/azure/container-instances/)
- [Déployer une instance de conteneur à partir de ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Précédent](scale-containers-serverless.md)
>[Suivant](communication-patterns.md)
