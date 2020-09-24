---
title: Résilience cloud native
description: Architecture des applications .NET natives Cloud pour Azure | Résilience native du Cloud
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163555"
---
# <a name="cloud-native-resiliency"></a>Résilience cloud native

La résilience est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle. Il ne s’agit pas d’éviter les défaillances, mais d’accepter les défaillances et de créer vos services Cloud natifs pour y répondre. Vous souhaitez revenir à un état de fonctionnement complet le plus rapidement possible.

Contrairement aux applications monolithiques traditionnelles, où tout fonctionne ensemble dans un processus unique, les systèmes Cloud natifs adoptent une architecture distribuée, comme illustré dans la figure 6-1 :

![Cloud distribué-environnement natif](./media/distributed-cloud-native-environment.png)

**Figure 6-1.** Cloud distribué-environnement natif

Dans la figure précédente, chaque microservice et [service de sauvegarde](https://12factor.net/backing-services) basé sur le Cloud s’exécutent dans un processus distinct, sur l’infrastructure de serveur, communiquant via des appels basés sur le réseau.

Dans cet environnement, un service doit être sensible à de nombreux défis :

- Latence réseau inattendue : durée d’une demande de service pour le déplacement vers le récepteur et l’inverse.

- Erreurs [temporaires](/azure/architecture/best-practices/transient-faults) -erreurs de connectivité réseau à courte durée de vie.

- Blocage par une opération synchrone de longue durée.

- Processus hôte qui s’est bloqué et qui est en cours de redémarrage ou de déplacement.

- Microservice surchargé qui ne peut pas répondre pendant une brève période.

- Une opération Orchestrator in-Flight, telle qu’une mise à niveau propagée ou le déplacement d’un service d’un nœud à un autre.

- Défaillances matérielles.

Les plateformes Cloud peuvent détecter et atténuer un grand nombre de ces problèmes d’infrastructure. Il peut redémarrer, monter en charge et même redistribuer votre service vers un autre nœud.  Toutefois, pour tirer pleinement parti de cette protection intégrée, vous devez concevoir vos services pour y réagir et prospérer dans cet environnement dynamique.

Dans les sections suivantes, nous allons explorer les techniques défensives que votre service et vos ressources cloud gérées peuvent exploiter pour réduire les temps d’arrêt et les interruptions.

>[!div class="step-by-step"]
>[Précédent](elastic-search-in-azure.md) 
> [Suivant](application-resiliency-patterns.md)
