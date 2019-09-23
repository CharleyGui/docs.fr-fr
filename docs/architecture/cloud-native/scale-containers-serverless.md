---
title: Mise à l’échelle des conteneurs et des applications sans serveur
description: Mise à l’échelle des applications Cloud natives avec le service Azure Kubernetes pour répondre à la demande des utilisateurs en augmentant les ressources des ordinateurs individuels ou en augmentant le nombre d’ordinateurs dans un cluster d’applications.
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184798"
---
# <a name="scaling-containers-and-serverless-applications"></a>Mise à l’échelle des conteneurs et des applications sans serveur

Il existe deux façons courantes de mettre à l’échelle une application : montée en puissance et montée en charge. Le premier fait référence à l’ajout de fonctionnalités à un seul hôte, tandis que ce dernier fait référence à l’ajout au nombre total d’hôtes. Une analogie courante à utiliser pour réfléchir à ce sujet est la façon de vous faire part de vos amis. S’il s’agit d’un seul ami, vous pouvez passer à votre voiture de course à deux sièges. Mais s’il s’agit de trois ou quatre, vous devrez peut-être utiliser l’un de vos SUVs ou un minivan, pour augmenter la capacité. Toutefois, lorsque votre nombre total atteint une douzaine ou plus, vous devez probablement prendre plusieurs véhicules (à moins qu’un bus ne le prenne), ce qui démontre le concept de montée en charge en ajoutant des instances supplémentaires (dans ce cas, davantage de véhicules). Voyons comment cela s’applique à nos applications.

## <a name="the-simple-solution-scaling-up"></a>Solution simple : montée en puissance

Le processus de mise à niveau des serveurs existants pour leur accorder davantage de ressources (processeur, mémoire, vitesse d’e/s disque, vitesse d’e/s réseau) est appelé *montée*en puissance. Dans les applications Cloud natives, la montée en puissance ne fait généralement pas référence à l’achat et à l’installation de matériel réel sur les machines physiques, si bien que le choix d’un plan plus performant dans une liste d’options disponibles. Les applications Cloud natives évoluent généralement en modifiant la taille de machine virtuelle (VM) utilisée pour héberger les nœuds individuels dans leur pool de nœuds Kubernetes. Les concepts de Kubernetes comme les nœuds, les clusters et les POD sont décrits plus en détail dans [la section suivante](leverage-containers-orchestrators.md). Azure prend en charge un large éventail de tailles de machines virtuelles exécutant [Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) et [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes). Pour mettre à l’échelle verticalement votre application, créez un nouveau pool de nœuds avec une taille de machine virtuelle de nœud plus grande, puis migrez les charges de travail vers le nouveau pool. Cela nécessite [plusieurs pools de nœuds pour votre cluster AKS](https://docs.microsoft.com/azure/aks/use-multiple-node-pools), une fonctionnalité actuellement en préversion. Les applications sans serveur sont mises à l’échelle en choisissant un [plan Premium](https://docs.microsoft.com/azure/azure-functions/functions-scale) et des tailles d’instance Premium, ou en choisissant un autre plan App service dédié.

## <a name="scaling-out-cloud-native-apps"></a>Montée en charge des applications Cloud natives

Les applications Cloud natives prennent en charge la montée en puissance parallèle en ajoutant des nœuds ou des Pod supplémentaires aux demandes de service. Cela peut être effectué manuellement en ajustant les paramètres de configuration de l’application (par exemple, la [mise à l’échelle d’un pool de nœuds](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) ou la *mise à l’échelle*automatique. La mise à l’échelle automatique ajuste les ressources utilisées par une application pour répondre à la demande, de la même manière qu’un thermostat répond à la température en faisant appel à des fins de chauffage ou de refroidissement supplémentaires. Lors de l’utilisation de la mise à l’échelle automatique, la mise à l’échelle manuelle est désactivée.

Les clusters AKS peuvent être mis à l’échelle de deux manières:

- La [mise](https://docs.microsoft.com/azure/aks/cluster-autoscaler) à l’échelle automatique du cluster surveille les gousses qui ne peuvent pas être planifiées sur les nœuds en raison de contraintes de ressources. Il ajoute des nœuds supplémentaires selon les besoins.
- Le module de mise à l’échelle automatique du **Pod horizontal** utilise le serveur de métriques dans un cluster Kubernetes pour surveiller les demandes de ressources des pod. Si un service a besoin de davantage de ressources, la mise à l’échelle automatique augmente le nombre de Pod.

La figure 3-13 montre la relation entre ces deux services de mise à l’échelle.

![Montée en charge d’un plan de App Service.](./media/aks-cluster-autoscaler.png)

**Figure 3-13**. Montée en charge d’un plan de App Service.

Ces services peuvent également réduire le nombre de blocs ou de nœuds en fonction des besoins. Ces deux services peuvent fonctionner ensemble et sont souvent déployés ensemble dans un cluster. Lorsqu’il est combiné, le module de mise à l’échelle automatique du Pod horizontal est axé sur l’exécution du nombre de gousses requis pour répondre à la demande de l’application. La mise à l’échelle automatique du cluster est axée sur l’exécution du nombre de nœuds requis pour prendre en charge les Pod planifiés.

### <a name="scaling-azure-functions"></a>Azure Functions de la mise à l’échelle

Azure Functions prend en charge automatiquement la montée en charge. Le plan de consommation par défaut ajoute (et supprime) des ressources de manière dynamique en fonction du nombre d’événements de déclenchement entrants. Vous êtes facturé uniquement pour les ressources de calcul utilisées lorsque vos fonctions sont exécutées en fonction du nombre d’exécutions, de la durée d’exécution et de la mémoire utilisés. À l’aide du plan Premium, vous bénéficiez de ces mêmes fonctionnalités, mais vous pouvez également contrôler les tailles d’instance utilisées, faire en sorte que les instances soient déjà préinitialisées (pour éviter les retards de démarrage à froid) et configurer des machines virtuelles dédiées sur lesquelles exécuter vos fonctions. Alors que la configuration par défaut doit fournir une solution économique et évolutive pour la plupart des applications, l’option Premium permet aux développeurs de bénéficier d’une plus grande flexibilité pour les exigences de Azure Functions personnalisées.

## <a name="references"></a>Références

- [AKS plusieurs pools de nœuds](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Mise à l’échelle automatique du cluster AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Tutoriel : Mettre à l’échelle des applications dans AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Mise à l’échelle et hébergement Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[Précédent](deploy-containers-azure.md)
>[Suivant](other-deployment-options.md)
