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
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289913"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="15534-102">Appel de méthodes asynchrones à l'aide d'IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="15534-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="15534-103">Les types dans .NET Framework et les bibliothèques de classes tierces peuvent fournir des méthodes permettant à une application de poursuivre son exécution tout en effectuant des opérations asynchrones dans des threads autres que le thread d’application principal.</span><span class="sxs-lookup"><span data-stu-id="15534-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="15534-104">Les sections suivantes décrivent et fournissent des exemples de code qui montrent les différents moyens d’appeler des méthodes asynchrones qui utilisent le modèle de conception <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="15534-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="15534-105">[Blocage de l’exécution de l’application en mettant fin à une opération asynchrone](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="15534-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="15534-106">[Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md)</span><span class="sxs-lookup"><span data-stu-id="15534-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="15534-107">[Interrogation de l’état d’une opération asynchrone](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="15534-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="15534-108">[Utilisation d’un délégué AsyncCallback pour terminer une opération asynchrone](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="15534-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15534-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15534-109">See also</span></span>

- [<span data-ttu-id="15534-110">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="15534-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="15534-111">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="15534-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
