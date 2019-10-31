---
title: Utilisation d'un délégué AsyncCallback et objet d'état
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094603"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="7960b-102">Utilisation d'un délégué AsyncCallback et objet d'état</span><span class="sxs-lookup"><span data-stu-id="7960b-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="7960b-103">Quand vous utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread séparé, vous pouvez utiliser un objet d’état pour passer des informations entre les rappels et récupérer un résultat final.</span><span class="sxs-lookup"><span data-stu-id="7960b-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="7960b-104">Cette rubrique illustre cette pratique en développant l’exemple de la rubrique [Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7960b-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7960b-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="7960b-105">Example</span></span>  
 <span data-ttu-id="7960b-106">L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du DNS (Domain Name System) pour des ordinateurs spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7960b-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="7960b-107">Cet exemple définit et utilise la classe `HostRequest` pour stocker les informations d’état.</span><span class="sxs-lookup"><span data-stu-id="7960b-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="7960b-108">Un objet `HostRequest` est créé pour chaque nom d’ordinateur entré par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7960b-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="7960b-109">Cet objet est retourné à la méthode <xref:System.Net.Dns.BeginGetHostByName%2A>.</span><span class="sxs-lookup"><span data-stu-id="7960b-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="7960b-110">La méthode `ProcessDnsInformation` est appelée chaque fois qu’une requête est terminée.</span><span class="sxs-lookup"><span data-stu-id="7960b-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="7960b-111">L’objet `HostRequest` est récupéré à l’aide de la propriété <xref:System.IAsyncResult.AsyncState%2A>.</span><span class="sxs-lookup"><span data-stu-id="7960b-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="7960b-112">La méthode `ProcessDnsInformation` utilise l’objet `HostRequest` pour stocker l’entrée <xref:System.Net.IPHostEntry> retournée par la requête ou une exception <xref:System.Net.Sockets.SocketException> levée par la requête.</span><span class="sxs-lookup"><span data-stu-id="7960b-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="7960b-113">Quand toutes les requêtes sont terminées, l’application parcourt les objets `HostRequest` et affiche les informations DNS ou le message d’erreur <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="7960b-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7960b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7960b-114">See also</span></span>

- [<span data-ttu-id="7960b-115">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="7960b-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="7960b-116">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="7960b-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="7960b-117">Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="7960b-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
