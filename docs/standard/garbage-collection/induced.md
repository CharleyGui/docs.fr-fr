---
title: Collections forcées
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120921"
---
# <a name="induced-collections"></a>Collections forcées
Dans la plupart des cas, le Garbage collector peut déterminer le meilleur moment pour exécuter une collection. En outre, vous devez lui permettre de s’exécuter de façon indépendante. Dans de rares cas, une collection forcée peut toutefois améliorer les performances de votre application. Vous pouvez alors induire le garbage collection à l’aide de la méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> pour forcer un garbage collection.  
  
 Utilisez la méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> quand la quantité de mémoire utilisée à un point spécifique dans le code de votre application diminue considérablement. Par exemple, si votre application utilise une boîte de dialogue complexe comportant plusieurs contrôles, l’appel de <xref:System.GC.Collect%2A> quand la boîte de dialogue est fermée peut améliorer les performances en libérant immédiatement la mémoire utilisée par la boîte de dialogue. Vérifiez que votre application n’induit pas trop fréquemment le garbage collection. En effet, les performances risquent d’être affectées si le Garbage collector tente de récupérer des objets à des moments inopportuns. Vous pouvez fournir une valeur d’énumération <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> à la méthode <xref:System.GC.Collect%2A> pour effectuer une collection uniquement lorsqu’elle est productive, comme décrit dans la section suivante.  
  
## <a name="gc-collection-mode"></a>Mode de collection GC  
 Vous pouvez utiliser l’une des surcharges de méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> qui inclut une valeur <xref:System.GCCollectionMode> pour spécifier le comportement d’une collection forcée, comme suit.  
  
|Valeur `GCCollectionMode`|Description|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Utilise le paramètre de garbage collection par défaut pour la version en cours d’exécution de .NET.|  
|<xref:System.GCCollectionMode.Forced>|Force l’exécution immédiate du garbage collection. Cela équivaut à appeler la surcharge <xref:System.GC.Collect?displayProperty=nameWithType>. Il en résulte une collection de blocage complète de toutes les générations.<br /><br /> Vous pouvez également compacter le tas d’objets volumineux en définissant la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> sur <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> avant de forcer un garbage collection de blocage complet immédiat.|  
|<xref:System.GCCollectionMode.Optimized>|Permet au Garbage collector de déterminer si le moment est opportun pour récupérer des objets.<br /><br /> Le Garbage collector peut déterminer qu’une collection n’est pas assez productive pour être effectuée. Dans ce cas, aucun objet n’est récupéré.|  
  
## <a name="background-or-blocking-collections"></a>Collections d’arrière-plan ou de blocage  
 Vous pouvez appeler la surcharge de méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> pour spécifier si une collection induite bloque ou non. Le type de collection effectué dépend d’une combinaison des paramètres `mode` et `blocking` de la méthode. `mode` est membre de l’énumération <xref:System.GCCollectionMode> et `blocking` est une valeur <xref:System.Boolean>. Le tableau suivant résume l’interaction des arguments `mode` et `blocking`.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> ou <xref:System.GCCollectionMode.Default>|Une collection de blocage est exécutée dès que possible. Si une collection d’arrière-plan est en cours et que la génération a la valeur 0 ou 1, la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> déclenche immédiatement une collection de blocage et retourne une valeur quand la collection est terminée. Si une collection d’arrière-plan est en cours et que le paramètre `generation` a la valeur 2, la méthode attend la fin de la collection d’arrière-plan, déclenche une collection de blocage de génération 2, puis retourne une valeur.|Une collection est exécutée dès que possible. La méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> demande une collection d'arrière-plan, mais cela n'est pas garanti ; selon les cas, une collection bloquante peut toujours être exécutée. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur.|  
|<xref:System.GCCollectionMode.Optimized>|Une collecte bloquante peut être exécutée, selon l'état du récupérateur de mémoire et du paramètre `generation`. Le Garbage collector tente de fournir des performances optimales.|Une collection de blocage peut être effectuée, en fonction de l’état du Garbage collector. La méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> demande une collection d'arrière-plan, mais cela n'est pas garanti ; selon les cas, une collection bloquante peut toujours être exécutée. Le Garbage collector tente de fournir des performances optimales. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur.|  
  
## <a name="see-also"></a>Voir aussi

- [Modes de latence](../../../docs/standard/garbage-collection/latency.md)
- [Garbage collection](../../../docs/standard/garbage-collection/index.md)
