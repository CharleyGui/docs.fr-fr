---
title: Résilience cloud native
description: Architecture des applications .NET natives Cloud pour Azure | Résilience native du Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781084"
---
# <a name="cloud-native-resiliency"></a>Résilience cloud native

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La résilience est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle. Il ne s’agit pas d’éviter les défaillances. Mais il s’agit d’accepter que l’échec soit inévitable dans les systèmes Cloud et de créer votre application pour y répondre. L’objectif final de la résilience est de ramener l’application à un état de fonctionnement complet après une défaillance.

Contrairement aux applications monolithiques traditionnelles, où tout s’exécute dans un processus unique, les systèmes natifs du Cloud intègrent l’architecture distribuée, comme illustré dans la figure 6-1 :

![Cloud distribué-environnement natif](./media/distributed-cloud-native-environment.png)

**Figure 6-1.** Cloud distribué-environnement natif

Dans la figure précédente, notez la manière dont chaque client, microservice et service de [sauvegarde](https://12factor.net/backing-services) Cloud s’exécute en tant que processus distinct, exécuté sur différents serveurs, communiquant toutes les communications via des appels basés sur le réseau.

Alors, que se passe-t-il ?

- [Latence réseau](https://www.techopedia.com/definition/8553/network-latency)inattendue.
- [Erreurs temporaires (erreurs](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) de connectivité réseau temporaires).
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
>[Précédent](elastic-search-in-azure.md)
>[Suivant](application-resiliency-patterns.md)
