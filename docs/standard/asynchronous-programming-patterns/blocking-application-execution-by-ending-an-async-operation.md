---
title: Blocage de l'exécution d'applications en mettant fin à une opération asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: 74976176acc0fbb948c514358b7bd323cc20c134
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289952"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="bf3d6-102">Blocage de l'exécution d'applications en mettant fin à une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="bf3d6-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="bf3d6-103">Les applications qui ne peuvent pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que cette opération se termine.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="bf3d6-104">Pour bloquer le thread principal de votre application en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf3d6-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="bf3d6-105">Appelez la méthode End Operations **end**_NomOpération_ .</span><span class="sxs-lookup"><span data-stu-id="bf3d6-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="bf3d6-106">Cette approche est illustrée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="bf3d6-107">Utilisez la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> du <xref:System.IAsyncResult> retourné par la méthode **Begin**_NomOpération_ de l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="bf3d6-108">Vous trouverez un exemple illustrant cette approche sur la page [Bloquer l'exécution d'applications avec un AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="bf3d6-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="bf3d6-109">Les applications qui utilisent la méthode **End**_nom_opération_ pour se bloquer jusqu’à la fin d’une opération asynchrone appellent généralement la méthode **Begin**_nom_opération_, effectuent tout le travail réalisable sans les résultats de l’opération, puis appellent **End**_nom_opération_.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf3d6-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf3d6-110">Example</span></span>  
 <span data-ttu-id="bf3d6-111">L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour un ordinateur spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="bf3d6-112">Notez que `null` (`Nothing` en Visual Basic) est transmis aux paramètres <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` et `stateObject`, car ces arguments ne sont pas requis dans cette approche.</span><span class="sxs-lookup"><span data-stu-id="bf3d6-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bf3d6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf3d6-113">See also</span></span>

- [<span data-ttu-id="bf3d6-114">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-114">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="bf3d6-115">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="bf3d6-115">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
