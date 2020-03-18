---
title: 'Comment : activer le mode de suivi des threads dans le verrouillage Spinlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138033"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Comment : activer le mode de suivi des threads dans le verrouillage Spinlock
<xref:System.Threading.SpinLock?displayProperty=nameWithType> est un verrou d’exclusion mutuelle de bas niveau que vous pouvez utiliser dans des scénarios avec des temps d’attente très courts. <xref:System.Threading.SpinLock> n’est pas réentrant. Quand un thread a accédé au verrou, il doit le quitter correctement avant de pouvoir y accéder de nouveau. En règle générale, toute nouvelle tentative d’accès au verrou risque de provoquer un interblocage, qui peut être très difficile à déboguer. En guide d’aide au développement, <xref:System.Threading.SpinLock?displayProperty=nameWithType> prend en charge un mode de suivi des threads qui lève une exception quand un thread tente d’accéder de nouveau à un verrou qu’il détient déjà. Cela vous permet de localiser plus facilement le point auquel un élément n’a pas correctement quitté le verrou. Vous pouvez activer le mode de suivi des threads en utilisant le constructeur <xref:System.Threading.SpinLock> qui accepte un paramètre d’entrée booléen et en passant un argument de `true`. Une fois les phases de développement et de test terminées, désactivez le mode de suivi des threads pour optimiser les performances.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant illustre le mode de suivi des threads. Les lignes qui quittent correctement le verrou sont commentées pour simuler une erreur de codage donnant lieu à l’un des résultats suivants :  
  
- Une exception est levée si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `true` (`True` en Visual Basic).  
  
- Un interblocage se produit si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `false` (`False` en Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Voir aussi

- [Spinlock](../../../docs/standard/threading/spinlock.md)
