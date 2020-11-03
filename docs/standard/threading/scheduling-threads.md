---
title: Planification de threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: 806d6620fd236c69a4f461f1e30f68a3fefc9b17
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188950"
---
# <a name="scheduling-threads"></a>Planification de threads

Chaque thread se voit attribuer une priorité. Les threads créés dans le Common Language Runtime se voient initialement attribuer la priorité <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Les threads créés en dehors du runtime conservent la priorité qu’ils avaient avant d’entrer dans l’environnement géré. Vous pouvez obtenir ou définir la priorité de n’importe quel thread avec la propriété <xref:System.Threading.Thread.Priority?displayProperty=nameWithType>.  
  
 Les threads sont planifiés pour être exécutés selon leur priorité. Même si les threads s’exécutent dans le runtime, tous les threads se voient attribuer des tranches horaires de processeur par le système d’exploitation. Les détails de l’algorithme de planification utilisés pour déterminer l’ordre d’exécution des threads varient selon chaque système d’exploitation. Sous certains systèmes d’exploitation, le thread avec la priorité la plus élevée (parmi les threads qui peuvent être exécutés) est toujours planifié pour s’exécuter en premier. Si plusieurs threads de même priorité sont disponibles, le planificateur parcourt les threads affichant cette priorité et attribue à chacun d’eux une tranche horaire fixe dans laquelle ils peuvent s’exécuter. Tant qu’un thread avec une priorité plus élevée est disponible pour être exécuté, les threads de priorité inférieure ne sont pas exécutés. Lorsqu’il n’y a plus aucun thread exécutable avec une priorité donnée, le planificateur passe à la priorité inférieure suivante et planifie l’exécution des threads avec cette priorité. Si un thread de priorité supérieure est exécutable, le thread de priorité inférieure est devancé pour permettre au thread de priorité plus élevé de s’exécuter de nouveau. Par ailleurs, le système d’exploitation peut également ajuster dynamiquement les priorités des threads lorsque l’interface utilisateur d’une application est déplacée du premier plan à l’arrière-plan. D’autres systèmes d’exploitation peuvent opter pour un autre algorithme de planification.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de threads et de threads](using-threads-and-threading.md)
- [Threading managé et non managé dans Windows](managed-and-unmanaged-threading-in-windows.md)
