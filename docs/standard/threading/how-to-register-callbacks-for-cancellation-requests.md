---
title: "Comment : enregistrer des rappels pour les demandes d'annulation"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279360"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="650da-102">Comment : enregistrer des rappels pour les demandes d'annulation</span><span class="sxs-lookup"><span data-stu-id="650da-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="650da-103">L'exemple suivant montre comment inscrire un délégué qui sera appelé quand une propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> aura la valeur true en raison d'un appel à <xref:System.Threading.CancellationTokenSource.Cancel%2A> sur l'objet qui a créé le jeton.</span><span class="sxs-lookup"><span data-stu-id="650da-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="650da-104">Utilisez cette technique pour l'annulation des opérations asynchrones qui ne prennent pas en charge l'infrastructure d'annulation unifiée en mode natif, ainsi que pour le déblocage des méthodes qui peuvent attendre la fin d'une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="650da-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="650da-105">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="650da-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="650da-106">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="650da-106">This error is benign.</span></span> <span data-ttu-id="650da-107">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="650da-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="650da-108">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="650da-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="650da-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="650da-109">Example</span></span>  
 <span data-ttu-id="650da-110">Dans l'exemple suivant, la méthode <xref:System.Net.WebClient.CancelAsync%2A> est enregistrée comme la méthode à appeler quand une annulation est demandée via le jeton d'annulation.</span><span class="sxs-lookup"><span data-stu-id="650da-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="650da-111">Si l'annulation a déjà été demandée quand le rappel est enregistré, le rappel sera malgré tout appelé.</span><span class="sxs-lookup"><span data-stu-id="650da-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="650da-112">Dans ce cas particulier, la méthode <xref:System.Net.WebClient.CancelAsync%2A> ne fera rien si aucune opération asynchrone n'est en cours. Il est donc sans risque d'appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="650da-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650da-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="650da-113">See also</span></span>

- [<span data-ttu-id="650da-114">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="650da-114">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
