---
title: Enregistrer les rappels pour les demandes d’annulation
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: f551055fc6e5e4565329201e9e0be6e4a83487a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826402"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="8b97b-102">Enregistrer les rappels pour les demandes d’annulation</span><span class="sxs-lookup"><span data-stu-id="8b97b-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="8b97b-103">Découvrez comment inscrire un délégué qui sera appelé quand une <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="8b97b-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="8b97b-104">La valeur passe de false à true lorsqu’un appel à <xref:System.Threading.CancellationTokenSource.Cancel%2A> sur l’objet qui a créé le jeton est effectué.</span><span class="sxs-lookup"><span data-stu-id="8b97b-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="8b97b-105">Utilisez cette technique pour annuler des opérations asynchrones qui ne prennent pas en charge l’infrastructure d’annulation unifiée en mode natif et pour débloquer des méthodes qui peuvent attendre la fin d’une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8b97b-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="8b97b-106">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b97b-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="8b97b-107">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="8b97b-107">This error is benign.</span></span> <span data-ttu-id="8b97b-108">Vous pouvez appuyer sur <kbd>F5</kbd> pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8b97b-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="8b97b-109">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="8b97b-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="8b97b-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b97b-110">Example</span></span>

<span data-ttu-id="8b97b-111">Dans l'exemple suivant, la méthode <xref:System.Net.WebClient.CancelAsync%2A> est enregistrée comme la méthode à appeler quand une annulation est demandée via le jeton d'annulation.</span><span class="sxs-lookup"><span data-stu-id="8b97b-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="8b97b-112">Si l'annulation a déjà été demandée quand le rappel est enregistré, le rappel sera malgré tout appelé.</span><span class="sxs-lookup"><span data-stu-id="8b97b-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="8b97b-113">Dans ce cas particulier, la méthode <xref:System.Net.WebClient.CancelAsync%2A> ne fera rien si aucune opération asynchrone n'est en cours. Il est donc sans risque d'appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="8b97b-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b97b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b97b-114">See also</span></span>

- [<span data-ttu-id="8b97b-115">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="8b97b-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
