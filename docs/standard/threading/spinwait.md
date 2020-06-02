---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
ms.openlocfilehash: 8b98e7d8b8ea4578fb446a0587f9a46ba4271348
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291108"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> est un type de synchronisation léger que vous pouvez utiliser dans des scénarios de bas niveau pour éviter des changements de contexte onéreux et des transitions de noyau requises pour les événements de noyau. Sur les ordinateurs multicœurs, lorsqu’une ressource n’est pas censée être maintenue pendant de longues périodes, il peut être plus efficace pour un thread en attente de tourner en mode utilisateur pendant quelques douzaines ou centaines de cycles, puis de réessayer d’acquérir la ressource. Si la ressource est disponible après la rotation, vous aurez économisé plusieurs milliers de cycles. Si la ressource n’est toujours pas disponible, vous n’aurez utilisé que quelques cycles et pourrez toujours entrer une attente basée sur le noyau. Cette combinaison de rotation et d’attente est parfois appelée *une opération d’attente en deux phases*.  
  
 <xref:System.Threading.SpinWait> est conçu pour être utilisé conjointement avec les types .NET Framework qui incluent dans un wrapper les événements de noyau tels que <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> peut également être utilisé par lui-même pour la fonctionnalité de rotation de base dans un seul programme.  
  
 <xref:System.Threading.SpinWait> est plus qu’une simple boucle vide. Il est implémenté avec soin afin de fournir le comportement de rotation correct pour le cas général et initialise lui-même des changements de contexte s’il tourne assez longtemps (à peu près le temps nécessaire pour une transition de noyau). Par exemple, sur les ordinateurs à cœur unique, <xref:System.Threading.SpinWait> interrompt immédiatement la tranche horaire du thread , car la rotation bloque la progression sur tous les threads. <xref:System.Threading.SpinWait> cesse même temporairement l’exécution sur les ordinateurs multicœurs pour empêcher le thread en attente de bloquer des threads à priorité plus élevée ou le récupérateur de mémoire. Par conséquent, si vous utilisez un <xref:System.Threading.SpinWait> dans une opération d’attente en deux phases, nous vous recommandons d’appeler l’attente de noyau avant que le <xref:System.Threading.SpinWait> lui-même initie un changement de contexte. <xref:System.Threading.SpinWait> fournit la propriété <xref:System.Threading.SpinWait.NextSpinWillYield%2A>, que vous pouvez vérifier avant chaque appel à <xref:System.Threading.SpinWait.SpinOnce%2A>. Lorsque la propriété retourne `true`, initialisez votre propre opération d’attente. Pour un exemple, consultez le [Guide pratique d’utilisation de SpinWait pour implémenter une opération d’attente en deux phases](how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Si vous n’effectuez pas une opération d’attente en deux phases, mais uniquement des rotations jusqu'à ce qu’une condition soit remplie, vous pouvez activer <xref:System.Threading.SpinWait> pour effectuer des changements de contexte comme il convient dans l’environnement de système d’exploitation Windows. L’exemple de base suivant montre un <xref:System.Threading.SpinWait> dans une pile sans verrou. Si vous avez besoin d’une pile haute performance sécurisée au niveau des threads, envisagez d’utiliser <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread.SpinWait%2A>
- [Objets et fonctionnalités de Threading](threading-objects-and-features.md)
