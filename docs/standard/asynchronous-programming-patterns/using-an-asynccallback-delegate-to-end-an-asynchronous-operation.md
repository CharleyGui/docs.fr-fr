---
title: Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130921"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="2ea7f-102">Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="2ea7f-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="2ea7f-103">Les applications qui peuvent continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone ne doivent pas se bloquer en attendant que cette opération se termine.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="2ea7f-104">Pour poursuivre l’exécution des instructions tout en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ea7f-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="2ea7f-105">Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="2ea7f-106">Cette approche est illustrée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="2ea7f-107">Utilisez <xref:System.IAsyncResult.IsCompleted%2A> la propriété <xref:System.IAsyncResult> de la méthode **Begin**_OperationName_ de l’opération asynchrone pour déterminer si l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="2ea7f-108">Vous trouverez un exemple illustrant cette approche sur la page [Demander l’état d’une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2ea7f-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea7f-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea7f-109">Example</span></span>  
 <span data-ttu-id="2ea7f-110">L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour des ordinateurs spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="2ea7f-111">Cet exemple crée un délégué <xref:System.AsyncCallback> qui référence la méthode `ProcessDnsInformation`,</span><span class="sxs-lookup"><span data-stu-id="2ea7f-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="2ea7f-112">appelée une fois par demande asynchrone d’informations DNS.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="2ea7f-113">Vous remarquerez que l’hôte spécifié par l’utilisateur est transmis au paramètre <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="2ea7f-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="2ea7f-114">Vous trouverez un exemple illustrant la définition et l’utilisation d’un objet d’état plus complexe sur la page [Utiliser un délégué AsyncCallback et un objet d’état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="2ea7f-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2ea7f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea7f-115">See also</span></span>

- [<span data-ttu-id="2ea7f-116">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="2ea7f-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="2ea7f-117">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="2ea7f-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="2ea7f-118">Appel de méthodes asynchrones à l'aide d'IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2ea7f-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="2ea7f-119">Utilisation d'un délégué AsyncCallback et objet d'état</span><span class="sxs-lookup"><span data-stu-id="2ea7f-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
