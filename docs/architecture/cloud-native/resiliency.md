---
title: Résilience Cloud Native
description: Architecture des applications .NET natives Cloud pour Azure | Résilience native du Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184840"
---
# <a name="cloud-native-resiliency"></a>Résilience Cloud Native

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La résilience est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle. Il ne s’agit pas d’éviter les défaillances. Mais il s’agit d’accepter que l’échec soit inévitable dans les systèmes Cloud et de créer votre application pour y répondre. L’objectif final de la résilience est de ramener l’application à un état de fonctionnement complet après une défaillance.

Contrairement aux applications monolithiques traditionnelles, où tout s’exécute dans un processus unique, les systèmes natifs du Cloud intègrent l’architecture distribuée, comme illustré dans la figure 6-1 :

![Cloud distribué-environnement natif](./media/distributed-cloud-native-environment.png)

**Figure 6-1.** Cloud distribué-environnement natif

Dans la figure précédente, notez la manière dont chaque client, microservice et service de [sauvegarde](https://12factor.net/backing-services) Cloud s’exécute en tant que processus distinct, exécuté sur différents serveurs, communiquant toutes les communications via des appels basés sur le réseau.

Alors, que se passe-t-il ?

- [Latence réseau](https://www.techopedia.com/definition/8553/network-latency)inattendue.
- [Erreurs temporaires](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (erreurs de connectivité réseau temporaires).
- Blocage par une opération synchrone de longue durée.
- Processus hôte qui s’est bloqué et qui est en cours de redémarrage ou de déplacement.
- Microservice surchargé qui ne peut pas répondre pendant une brève période.
- Opération DevOps en cours, telle qu’une opération de mise à jour ou de mise à l’échelle.
- Une opération Orchestrator, telle que le déplacement d’un service d’un nœud à un autre.
- Défaillances matérielles du matériel de la marchandise.

Lors du déploiement de services distribués dans une infrastructure basée sur le Cloud, les facteurs de la liste précédente deviennent très réels et vous devez concevoir et développer de manière défensive pour les gérer.

Dans un système distribué à petite échelle, les défaillances sont moins fréquentes, mais quand un système est mis à l’échelle, vous pouvez vous attendre à rencontrer ces problèmes à un point où une défaillance partielle devient une opération normale.

Par conséquent, votre application et votre infrastructure doivent être résilientes. Dans les sections suivantes, nous allons explorer les techniques défensives que vous pouvez ajouter à votre application et les fonctionnalités de Cloud intégrées que vous pouvez exploiter pour aider à vérifier l’expérience de vos utilisateurs.

>[!div class="step-by-step"]
>[Précédent](azure-data-storage.md)
>[Suivant](application-resiliency-patterns.md)
