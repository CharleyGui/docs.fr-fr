---
title: Appel de méthodes asynchrones à l'aide d'IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f943633f554433d30598f11e8611d3e837d94280
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628830"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="6c1e5-102">Appel de méthodes asynchrones à l'aide d'IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="6c1e5-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="6c1e5-103">Les types dans .NET Framework et les bibliothèques de classes tierces peuvent fournir des méthodes permettant à une application de poursuivre son exécution tout en effectuant des opérations asynchrones dans des threads autres que le thread d’application principal.</span><span class="sxs-lookup"><span data-stu-id="6c1e5-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="6c1e5-104">Les sections suivantes décrivent et fournissent des exemples de code qui montrent les différents moyens d’appeler des méthodes asynchrones qui utilisent le modèle de conception <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="6c1e5-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="6c1e5-105">[Blocage de l'exécution d'applications en mettant fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6c1e5-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="6c1e5-106">[Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)</span><span class="sxs-lookup"><span data-stu-id="6c1e5-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="6c1e5-107">[Sondage de l'état d'une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6c1e5-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="6c1e5-108">[Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6c1e5-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1e5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c1e5-109">See also</span></span>

- [<span data-ttu-id="6c1e5-110">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="6c1e5-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="6c1e5-111">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="6c1e5-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
