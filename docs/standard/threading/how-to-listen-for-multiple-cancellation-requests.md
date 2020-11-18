---
title: "Comment : écouter plusieurs demandes d'annulation"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: 37f42ad4de2d468cd14a916ab4e35e6577f8e375
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819771"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="3e318-102">Comment : écouter plusieurs demandes d'annulation</span><span class="sxs-lookup"><span data-stu-id="3e318-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="3e318-103">Cet exemple montre comment écouter simultanément deux jetons d’annulation afin de pouvoir annuler une opération si un des jetons le demande.</span><span class="sxs-lookup"><span data-stu-id="3e318-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e318-104">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e318-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="3e318-105">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="3e318-105">This error is benign.</span></span> <span data-ttu-id="3e318-106">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3e318-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="3e318-107">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="3e318-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e318-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e318-108">Example</span></span>  
 <span data-ttu-id="3e318-109">Dans l'exemple suivant, la méthode <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> permet de fusionner deux jetons en un seul.</span><span class="sxs-lookup"><span data-stu-id="3e318-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="3e318-110">Cela permet de transmettre le jeton à des méthodes qui n’acceptent qu’un seul jeton d’annulation comme argument.</span><span class="sxs-lookup"><span data-stu-id="3e318-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="3e318-111">L’exemple illustre un scénario courant dans lequel une méthode doit observer à la fois un jeton reçu depuis l’extérieur de la classe et un jeton généré à l’intérieur de la classe.</span><span class="sxs-lookup"><span data-stu-id="3e318-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="3e318-112">Lorsque le jeton lié lève une <xref:System.OperationCanceledException>, le jeton transmis à l’exception est le jeton lié, et non un des jetons prédécesseurs.</span><span class="sxs-lookup"><span data-stu-id="3e318-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="3e318-113">Pour déterminer quel jeton a été annulé, vérifiez directement l’état des jetons prédécesseurs.</span><span class="sxs-lookup"><span data-stu-id="3e318-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="3e318-114">Dans cet exemple, <xref:System.AggregateException> ne doit jamais être levée, mais elle est interceptée ici car, dans les scénarios réels, toutes les autres exceptions, hormis <xref:System.OperationCanceledException>, levées à partir du délégué de tâche sont encapsulées dans une <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="3e318-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e318-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e318-115">See also</span></span>

- [<span data-ttu-id="3e318-116">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="3e318-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
