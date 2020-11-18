---
title: Annulation de threads de façon coopérative
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 9e9224e9dc9ac57defe75e916dd6b9844bba7f12
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826610"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="6118c-102">Annulation de threads de façon coopérative</span><span class="sxs-lookup"><span data-stu-id="6118c-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="6118c-103">Avant le .NET Framework 4, .NET n’offrait aucune méthode intégrée pour annuler un thread de manière coopérative après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="6118c-103">Prior to .NET Framework 4, .NET provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="6118c-104">Toutefois, à partir de .NET Framework 4, vous pouvez utiliser un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> pour annuler les threads, tout comme vous pouvez les utiliser pour annuler des <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objets ou des requêtes PLINQ.</span><span class="sxs-lookup"><span data-stu-id="6118c-104">However, starting with .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="6118c-105">Bien que la classe <xref:System.Threading.Thread?displayProperty=nameWithType> n’offre pas de prise en charge intégrée pour les jetons d’annulation, vous pouvez transmettre un jeton à une procédure de thread à l’aide du constructeur <xref:System.Threading.Thread> qui prend un délégué <xref:System.Threading.ParameterizedThreadStart>.</span><span class="sxs-lookup"><span data-stu-id="6118c-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="6118c-106">L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.</span><span class="sxs-lookup"><span data-stu-id="6118c-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="6118c-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6118c-107">See also</span></span>

- [<span data-ttu-id="6118c-108">Utilisation de threads et de threads</span><span class="sxs-lookup"><span data-stu-id="6118c-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
