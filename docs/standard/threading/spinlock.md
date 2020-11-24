---
title: SpinLock
ms.date: 03/30/2017
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: adb80ffb1917ea725c458dbe3c37f3d364276fb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674292"
---
# <a name="spinlock"></a>SpinLock

La structure <xref:System.Threading.SpinLock> est une primitive de synchronisation de bas niveau à exclusion mutuelle qui tourne en attendant d’acquérir un verrou. Sur les ordinateurs multicœurs, lorsque les temps d’attente sont supposés être courts et que la contention est minimale, <xref:System.Threading.SpinLock> peut être plus performant que d’autres types de verrous. Toutefois, nous vous recommandons d’utiliser <xref:System.Threading.SpinLock> uniquement lorsque vous déterminez par profilage que la <xref:System.Threading.Monitor?displayProperty=nameWithType> méthode ou <xref:System.Threading.Interlocked> méthodes ralentissent considérablement les performances de votre programme.  
  
 <xref:System.Threading.SpinLock> maîtrise la tranche horaire du thread même si elle n’a pas encore acquis le verrou. Il procède ainsi pour éviter une inversion de priorité du thread et permettre au récupérateur de mémoire de progresser. Lorsque vous utilisez un <xref:System.Threading.SpinLock>, vérifiez qu’aucun thread ne peut contenir le verrou au-delà d’un intervalle de temps très court, et qu’aucun thread ne peut bloquer pendant qu’il détient le verrou.  
  
 Étant donné que le verrouillage SpinLock est un type valeur, vous devez le passer explicitement par référence si vous envisagez que les deux copies fassent référence au même verrou.  
  
 Pour plus d'informations sur l'utilisation de ce type, voir <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Pour voir un exemple, consultez [Guide pratique pour utiliser le verrouillage SpinLock pour une synchronisation de bas niveau](how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>prend en *thread* charge un mode de - *suivi des* threads que vous pouvez utiliser pendant la phase de développement pour faciliter le suivi du thread qui détient le verrou à un moment donné. Le mode de suivi des threads est très utile pour le débogage, mais nous vous recommandons de le désactiver dans la version finale de votre programme, car il peut ralentir les performances. Pour plus d’informations, voir [Guide pratique pour activer le Mode de suivi des threads dans le verrouillage SpinLock](how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
