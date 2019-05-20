---
title: 'Procédure : Activer le mode de suivi des threads dans le verrouillage SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 111ab87ca419217f425eb5d4bc9b52f5f30f0237
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644843"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="c4890-102">Procédure : Activer le mode de suivi des threads dans le verrouillage SpinLock</span><span class="sxs-lookup"><span data-stu-id="c4890-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="c4890-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> est un verrou d’exclusion mutuelle de bas niveau que vous pouvez utiliser dans des scénarios avec des temps d’attente très courts.</span><span class="sxs-lookup"><span data-stu-id="c4890-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="c4890-104"><xref:System.Threading.SpinLock> n’est pas réentrant.</span><span class="sxs-lookup"><span data-stu-id="c4890-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="c4890-105">Quand un thread a accédé au verrou, il doit le quitter correctement avant de pouvoir y accéder de nouveau.</span><span class="sxs-lookup"><span data-stu-id="c4890-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="c4890-106">En règle générale, toute nouvelle tentative d’accès au verrou risque de provoquer un interblocage, qui peut être très difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="c4890-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="c4890-107">En guide d’aide au développement, <xref:System.Threading.SpinLock?displayProperty=nameWithType> prend en charge un mode de suivi des threads qui lève une exception quand un thread tente d’accéder de nouveau à un verrou qu’il détient déjà.</span><span class="sxs-lookup"><span data-stu-id="c4890-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="c4890-108">Cela vous permet de localiser plus facilement le point auquel un élément n’a pas correctement quitté le verrou.</span><span class="sxs-lookup"><span data-stu-id="c4890-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="c4890-109">Vous pouvez activer le mode de suivi des threads en utilisant le constructeur <xref:System.Threading.SpinLock> qui accepte un paramètre d’entrée booléen et en passant un argument de `true`.</span><span class="sxs-lookup"><span data-stu-id="c4890-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="c4890-110">Une fois les phases de développement et de test terminées, désactivez le mode de suivi des threads pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="c4890-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4890-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4890-111">Example</span></span>  
 <span data-ttu-id="c4890-112">L’exemple suivant illustre le mode de suivi des threads.</span><span class="sxs-lookup"><span data-stu-id="c4890-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="c4890-113">Les lignes qui quittent correctement le verrou sont commentées pour simuler une erreur de codage donnant lieu à l’un des résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="c4890-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="c4890-114">Une exception est levée si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `true` (`True` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c4890-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="c4890-115">Un interblocage se produit si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `false` (`False` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c4890-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="c4890-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4890-116">See also</span></span>

- [<span data-ttu-id="c4890-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="c4890-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
