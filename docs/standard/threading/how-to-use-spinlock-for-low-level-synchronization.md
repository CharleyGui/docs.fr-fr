---
title: Guide pratique pour utiliser le verrouillage SpinLock pour une synchronisation de bas niveau
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: 3fb19c2b36d97710685cac4ecd10f47a119814ce
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189184"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Guide pratique pour utiliser le verrouillage SpinLock pour une synchronisation de bas niveau

L'exemple suivant montre comment utiliser un verrouillage <xref:System.Threading.SpinLock>. Dans cet exemple, la section critique exécute une quantité minimale de travail, ce qui en fait un bon candidat pour un <xref:System.Threading.SpinLock>. Le fait d’augmenter un petit peu le volume de travail augmente le niveau de performance du <xref:System.Threading.SpinLock> par rapport à un verrouillage standard. Toutefois, à un moment, le verrouillage tournant devient plus coûteux qu’un verrouillage standard. Vous pouvez utiliser la fonctionnalité de profilage d'accès concurrentiel dans les outils de profilage pour voir quel type de verrouillage offre les meilleures performances pour votre programme. Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> peut être utile quand vous avez besoin d’un verrouillage de courte durée sur une ressource partagée. Dans ce cas, sur les ordinateurs multicœurs, le thread bloqué peut efficacement tourner pendant quelques cycles jusqu'à ce que le verrouillage soit libéré. En tournant, le thread ne se bloque pas. Ce processus est exigeant en ressources. <xref:System.Threading.SpinLock> cesse de tourner sous certaines conditions pour empêcher toute défaillance des processeurs logiques ou toute inversion des priorités sur les systèmes avec Hyper-Threading.  
  
 Cet exemple utilise la classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, qui exige la synchronisation utilisateur pour l’accès multithread. Une autre option consiste à utiliser <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> , qui ne requiert pas de verrous utilisateur.  
  
 Notez l’utilisation de `false` dans l’appel à <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> . Cela fournit les meilleures performances. Spécifiez `true` sur les architectures IA64 pour utiliser la barrière de mémoire, qui vide les mémoires tampons d’écriture pour vous assurer que le verrou est maintenant disponible pour la fermeture des autres threads.  
  
## <a name="see-also"></a>Voir aussi

- [Objets et fonctionnalités de Threading](threading-objects-and-features.md)
- [instruction lock (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [instruction SyncLock (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
