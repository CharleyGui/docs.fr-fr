---
title: Modes de latence
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 8833c88c3221c0a375011eb62dd712340f7e89cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120907"
---
# <a name="latency-modes"></a>Modes de latence
Pour récupérer des objets, le garbage collector doit arrêter tous les threads en cours d'exécution dans une application. Dans certaines situations, par exemple, quand une application récupère des données ou affiche du contenu, un garbage collection complet peut se produire à un moment critique et nuire aux performances. Vous pouvez ajuster le niveau d'intrusion du garbage collector en définissant la propriété <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> sur l'une des valeurs<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.  
  
 La latence fait référence à la durée pendant laquelle le garbage collector effectue une intrusion dans votre application. Pendant les périodes de faible latence, le garbage collector est moins intrusif quant à la récupération des objets. L'énumération <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> fournit deux paramètres de latence faible :  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> empêche les collections de génération 2 et effectue uniquement des collections de génération 0 et 1. Elle ne peut être utilisée que pour de courtes durées. Sur des périodes plus longues, si le système connaît une sollicitation de mémoire importante, le garbage collector déclenchera une collection, qui pourra brièvement suspendre l'application et interrompre une opération critique. Ce paramètre est disponible uniquement pour le garbage collection des stations de travail.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> empêche les collections de génération 2 de premier plan et effectue uniquement des collections de génération 0 et 1, ainsi que des collections de génération 2 d'arrière-plan. Il peut être utilisé pour de longues périodes et est disponible à la fois pour le garbage collection des stations de travail et des serveurs. Ce paramètre ne peut pas être utilisé si le [garbage collection simultané](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) est désactivé.  
  
 Pendant les périodes de faible latence, les collections de génération 2 sont empêchées, sauf dans les cas suivants :  
  
- Le système reçoit une notification de mémoire insuffisante du système d'exploitation.  
  
- Le code de votre application déclenche une collection en appelant la méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> et en spécifiant la valeur 2 pour le paramètre `generation`.  
  
 Le tableau suivant répertorie les scénarios d'application pour l'utilisation des valeurs <xref:System.Runtime.GCLatencyMode>.  
  
|Mode de latence|Scénarios d'application|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Pour les applications qui n'ont aucune interface utilisateur ou les opérations côté serveur.<br /><br /> Il s’agit du mode par défaut quand le [garbage collection simultané](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) est désactivé.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pour la plupart des applications qui ont une interface utilisateur.<br /><br /> Il s’agit du mode par défaut quand le [garbage collection simultané](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) est activé.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pour les applications qui ont des opérations de courte durée pour lesquelles le temps est important, et durant lesquelles les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications qui ont des fonctions de rendu d'animation ou d'acquisition de données.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pour les applications qui ont des opérations pour lesquelles le temps est important, pendant une durée définie mais potentiellement longue durant laquelle les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications nécessitant des temps de réponse rapides en raison du changement des données de marché pendant les heures de négociation.<br /><br /> Ce mode augmente davantage la taille du tas managé que les autres modes. Parce qu'il ne compacte pas le tas managé, une fragmentation plus importante est possible. Assurez-vous que suffisamment de mémoire est disponible.|  
  
## <a name="guidelines-for-using-low-latency"></a>Instructions sur l'utilisation de la faible latence  
 Quand vous utilisez le mode <xref:System.Runtime.GCLatencyMode.LowLatency>, respectez les consignes suivantes :  
  
- Choisissez une période aussi courte que possible pour la faible latence.  
  
- Évitez d'allouer de grandes quantités de mémoire pendant les périodes de faible latence. Vous pouvez recevoir des notifications de mémoire insuffisante, car le garbage collection récupère moins d'objets.  
  
- En mode de latence faible, réduisez le nombre d'allocations, notamment les allocations sur le tas des objets volumineux et les objets épinglés.  
  
- N'oubliez pas les threads qui peuvent être à l'origine d'allocations. Étant donné que le paramètre de propriété <xref:System.Runtime.GCSettings.LatencyMode%2A> s'étend à tout le processus, vous pouvez générer un <xref:System.OutOfMemoryException> sur n'importe quel thread à l'origine d'une allocation.  
  
- Encapsulez le code de latence faible dans les régions d'exécution limitée (pour plus d'informations, consultez [Régions d'exécution limitée](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- Vous pouvez forcer les collections de génération 2 pendant une période de latence basse en appelant la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.GC?displayProperty=nameWithType>
- [Collections forcées](../../../docs/standard/garbage-collection/induced.md)
- [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
