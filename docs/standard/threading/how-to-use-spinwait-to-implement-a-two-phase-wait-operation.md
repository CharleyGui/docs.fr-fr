---
title: "Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137942"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="8f60e-102">Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases</span><span class="sxs-lookup"><span data-stu-id="8f60e-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="8f60e-103">L’exemple suivant montre comment utiliser un objet <xref:System.Threading.SpinWait?displayProperty=nameWithType> pour implémenter une opération d’attente en deux phases.</span><span class="sxs-lookup"><span data-stu-id="8f60e-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="8f60e-104">Durant la première phase, l’objet de synchronisation (`Latch`) tourne pendant quelques cycles, le temps de vérifier si le verrou est disponible.</span><span class="sxs-lookup"><span data-stu-id="8f60e-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="8f60e-105">Durant la deuxième phase, si le verrou est enfin disponible, la méthode `Wait` est retournée sans utiliser le <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> pour exécuter son attente. Dans le cas contraire, `Wait` exécute l’attente.</span><span class="sxs-lookup"><span data-stu-id="8f60e-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f60e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f60e-106">Example</span></span>  
 <span data-ttu-id="8f60e-107">Cet exemple montre une implémentation de base d’une primitive de synchronisation de verrou.</span><span class="sxs-lookup"><span data-stu-id="8f60e-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="8f60e-108">Vous pouvez utiliser cette structure de données quand les temps d’attente sont supposés être très courts.</span><span class="sxs-lookup"><span data-stu-id="8f60e-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="8f60e-109">L’exemple est uniquement fourni à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="8f60e-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="8f60e-110">Si vous avez besoin d’une fonctionnalité de type verrou dans votre programme, optez pour l’utilisation de <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f60e-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="8f60e-111">Le verrou utilise l’objet <xref:System.Threading.SpinWait> pour tourner sur place uniquement jusqu’à ce que le prochain appel à `SpinOnce` provoque la transmission de la tranche horaire du thread par le <xref:System.Threading.SpinWait>.</span><span class="sxs-lookup"><span data-stu-id="8f60e-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="8f60e-112">À ce stade, le verrou provoque son propre changement de contexte en appelant <xref:System.Threading.WaitHandle.WaitOne%2A> sur le <xref:System.Threading.ManualResetEvent> et en passant le reste de la valeur de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="8f60e-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="8f60e-113">La sortie de la journalisation indique la fréquence à laquelle le verrou a pu augmenter les performances en acquérant le verrou sans utiliser <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="8f60e-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f60e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f60e-114">See also</span></span>

- [<span data-ttu-id="8f60e-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="8f60e-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="8f60e-116">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="8f60e-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
