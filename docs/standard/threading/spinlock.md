---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106172"
---
# <a name="spinlock"></a>SpinLock
La structure <xref:System.Threading.SpinLock> est une primitive de synchronisation de bas niveau à exclusion mutuelle qui tourne en attendant d’acquérir un verrou. Sur les ordinateurs multicœurs, lorsque les temps d’attente sont supposés être courts et que la contention est minimale, <xref:System.Threading.SpinLock> peut être plus performant que d’autres types de verrous. Toutefois, nous vous recommandons d’utiliser <xref:System.Threading.SpinLock> uniquement lorsque vous déterminez par profilage que la <xref:System.Threading.Monitor?displayProperty=nameWithType> méthode ou <xref:System.Threading.Interlocked> méthodes ralentissent considérablement les performances de votre programme.  
  
 <xref:System.Threading.SpinLock> maîtrise la tranche horaire du thread même si elle n’a pas encore acquis le verrou. Il procède ainsi pour éviter une inversion de priorité du thread et permettre au récupérateur de mémoire de progresser. Lorsque vous utilisez un <xref:System.Threading.SpinLock>, vérifiez qu’aucun thread ne peut contenir le verrou au-delà d’un intervalle de temps très court, et qu’aucun thread ne peut bloquer pendant qu’il détient le verrou.  
  
 Étant donné que le verrouillage SpinLock est un type valeur, vous devez le passer explicitement par référence si vous envisagez que les deux copies fassent référence au même verrou.  
  
 Pour plus d'informations sur l'utilisation de ce type, voir <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Pour voir un exemple, consultez [Guide pratique pour utiliser le verrouillage SpinLock pour une synchronisation de bas niveau](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>prend en charge un mode*de suivi des* *threads*-que vous pouvez utiliser pendant la phase de développement pour aider à suivre le thread qui tient le verrou à un moment précis. Le mode de suivi des threads est très utile pour le débogage, mais nous vous recommandons de le désactiver dans la version finale de votre programme, car il peut ralentir les performances. Pour plus d’informations, voir [Guide pratique pour activer le Mode de suivi des threads dans le verrouillage SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Voir aussi

- [Objets et caractéristiques de threading](../../../docs/standard/threading/threading-objects-and-features.md)
