---
title: Mise à l'échelle de conteneurs et d’applications serverless
description: Mise à l’échelle d’applications Cloud natives avec le service Azure Kubernetes pour répondre à la demande de l’utilisateur.
ms.date: 05/13/2020
ms.openlocfilehash: edf56ba50ba391e06e588d682918cd473a2cf374
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165977"
---
# <a name="scaling-containers-and-serverless-applications"></a>Mise à l'échelle de conteneurs et d’applications serverless

Il existe deux façons de mettre à l’échelle une application. Le premier fait référence à l’ajout de capacité à une ressource unique, tandis que le second fait référence à l’ajout de ressources supplémentaires pour augmenter la capacité.

## <a name="the-simple-solution-scaling-up"></a>Solution simple : montée en puissance

La mise à niveau d’un serveur hôte existant avec augmentation du processeur, de la mémoire, de la vitesse d’e/s disque et de la vitesse d’e/s réseau est appelée *montée*en puissance. La montée en puissance d’une application Cloud Native implique de choisir des ressources plus performantes du fournisseur du Cloud. Par exemple, vous pouvez créer un pool de nœuds avec des machines virtuelles plus volumineuses dans votre cluster Kubernetes. Ensuite, migrez vos services en conteneur vers le nouveau pool.

Les applications sans serveur sont mises à l’échelle en choisissant le [plan fonctions Premium](/azure/azure-functions/functions-scale) ou tailles d’instance Premium à partir d’un plan App service dédié.

## <a name="scaling-out-cloud-native-apps"></a>Montée en charge des applications Cloud natives

Les applications Cloud natives subissent souvent des fluctuations importantes de la demande et requièrent une mise à l’échelle à l’avis d’un moment. Ils privilégient la montée en charge. La montée en charge est effectuée horizontalement en ajoutant des ordinateurs supplémentaires (appelés nœuds) ou des instances d’application à un cluster existant. Dans Kubernetes, vous pouvez mettre à l’échelle manuellement en ajustant les paramètres de configuration de l’application (par exemple, en [mettant à l’échelle un pool de nœuds](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) ou en passant par la mise à l’échelle automatique.

Les clusters AKS peuvent être mis à l’échelle de deux manières :

Tout d’abord, le module de mise à l’échelle automatique du [Pod horizontal](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) surveille la demande des ressources et met automatiquement à l’échelle vos réplicas Pod pour les satisfaire. Lorsque le trafic augmente, des réplicas supplémentaires sont automatiquement approvisionnés pour monter en charge vos services. De même, lorsque la demande diminue, elles sont supprimées pour mettre à l’échelle vos services. Vous définissez la mesure sur laquelle mettre à l’échelle, par exemple l’utilisation de l’UC. Vous pouvez également spécifier le nombre minimal et le nombre maximal de réplicas à exécuter. AKS surveille cette mesure et la met à l’échelle en conséquence.

Ensuite, la fonctionnalité de mise à l’échelle automatique du [cluster AKS](/azure/aks/cluster-autoscaler) vous permet de mettre automatiquement à l’échelle des nœuds de calcul dans un cluster Kubernetes pour répondre à la demande. Avec elle, vous pouvez ajouter automatiquement de nouvelles machines virtuelles au groupe de machines virtuelles identiques Azure sous-jacent chaque fois que la capacité de calcul est nécessaire. Elle supprime également les nœuds quand ils ne sont plus nécessaires.

La figure 3-13 montre la relation entre ces deux services de mise à l’échelle.

![Montée en charge d’un plan de App Service.](./media/aks-cluster-autoscaler.png)

**Figure 3-13**. Montée en charge d’un plan de App Service.

En travaillant ensemble, veillez à ce que le nombre optimal d’instances de conteneur et de nœuds de calcul prenne en charge la demande fluctuante. Le module de mise à l’échelle automatique du Pod horizontal optimise le nombre de gousses requis. La mise à l’échelle automatique du cluster optimise le nombre de nœuds requis.

### <a name="scaling-azure-functions"></a>Mise à l'échelle des fonctions Azure

Azure Functions montée en charge automatiquement à la demande. Les ressources du serveur sont allouées et supprimées dynamiquement en fonction du nombre d’événements déclenchés. Vous êtes facturé uniquement pour les ressources de calcul consommées lorsque vos fonctions sont exécutées. La facturation est basée sur le nombre d’exécutions, la durée d’exécution et la mémoire utilisée.

Bien que le plan de consommation par défaut offre une solution économique et évolutive pour la plupart des applications, l’option Premium permet aux développeurs de disposer d’une flexibilité pour les exigences de Azure Functions personnalisées. La mise à niveau vers le plan Premium permet de contrôler les tailles d’instance, les instances préchauffées (pour éviter les retards de démarrage à froid) et les machines virtuelles dédiées.

>[!div class="step-by-step"]
>[Précédent](deploy-containers-azure.md) 
> [Suivant](other-deployment-options.md)
