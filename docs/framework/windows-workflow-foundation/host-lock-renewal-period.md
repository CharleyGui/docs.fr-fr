---
title: Période de renouvellement du verrou de l'hôte
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 82073377353be6d4f8a7d0a343c31f2b49a2873f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268192"
---
# <a name="host-lock-renewal-period"></a>Période de renouvellement du verrou de l'hôte

La propriété **période de renouvellement du verrou** de l’hôte du magasin d’instances de workflow SQL vous permet de spécifier la période pendant laquelle l’hôte renouvelle son verrou sur une instance de Workflow. Le verrou reste valide pendant la période spécifiée pour la propriété Host Lock Renewal Period + 30 secondes. Si l'hôte ne renouvelle pas le verrou (en d'autres termes, s'il étend le bail) durant cette période, le verrou expire et le fournisseur de persistance déverrouille l'instance. La valeur de cette propriété est de type TimeSpan au format « hh : mm : SS ». La valeur minimale autorisée est "00:00:01" (1 seconde). La valeur par défaut de cette propriété est « 00:00:30 » (30 secondes).  
  
 Cette propriété est significative dans les scénarios où un hôte du service de workflow échoue avant d'avoir pu déverrouiller une instance de service du workflow qu'il possède. Dans ce scénario, le verrou de l'instance du service de workflow dans la base de données de persistance est supprimé par le fournisseur de persistance après l'expiration du verrou afin qu'un autre hôte du service de workflow qui s'exécute sur le même ordinateur ou sur un autre ordinateur dans une batterie de serveurs puisse acquérir le verrou et charger l'instance du service de workflow en mémoire pour reprendre son exécution à partir de son dernier état persistant.  
  
 Le fait de définir une valeur plus élevée pour cette propriété a pour effet de verrouiller les instances du service de workflow dans la base de données de persistance pendant plus longtemps et par conséquent de retarder la récupération de l'instance à partir du dernier point de persistance. Si vous définissez un intervalle court pour cette propriété, la nouvelle instance de l'hôte du service de workflow récupère rapidement l'instance du service de workflow ayant échoué, mais provoque une augmentation dans la charge de travail pour l'hôte du service de workflow et la base de données SQL Server.  
  
 Le magasin d’instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances dont les verrous sont périmés. Lorsqu'il trouve des instances dont les verrous sont périmés, il place les instances dans la table RunnableInstances afin qu'un hôte de workflow puisse récupérer et exécuter ces instances.
