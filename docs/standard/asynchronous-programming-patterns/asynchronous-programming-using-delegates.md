---
title: Programmation asynchrone à l'aide de délégués
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121742"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="4bbc9-102">Programmation asynchrone à l'aide de délégués</span><span class="sxs-lookup"><span data-stu-id="4bbc9-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="4bbc9-103">Les délégués permettent d’appeler une méthode synchrone de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="4bbc9-104">Lorsque vous appelez un délégué de manière synchrone, la méthode `Invoke` appelle la méthode cible directement sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="4bbc9-105">Si la méthode `BeginInvoke` est appelée, le common language runtime (CLR) met en file d’attente la demande et retourne immédiatement à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="4bbc9-106">La méthode cible est appelée de façon asynchrone sur un thread du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="4bbc9-107">Le thread d’origine, qui a envoyé la demande, est libre de continuer à s’exécuter en parallèle avec la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="4bbc9-108">Si une méthode de rappel a été spécifiée dans l’appel à la méthode `BeginInvoke`, la méthode de rappel est appelée lorsque la méthode cible se termine.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="4bbc9-109">Dans la méthode de rappel, la méthode `EndInvoke` obtient la valeur de retour et d’éventuels paramètres d’entrée/sortie ou de sortie uniquement.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="4bbc9-110">Si aucune méthode de rappel n’est spécifiée lors de l’appel à `BeginInvoke`, `EndInvoke` peut être appelé depuis le thread qui a appelé `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4bbc9-111">Les compilateurs doivent émettre des classes déléguées avec les méthodes `Invoke`, `BeginInvoke` et `EndInvoke` à l’aide de la signature de délégué spécifiée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="4bbc9-112">Les méthodes `BeginInvoke` et `EndInvoke` doivent être décorées comme étant natives.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="4bbc9-113">Étant donné que ces méthodes sont marquées comme étant natives, le CLR fournit automatiquement l’implémentation au moment du chargement de la classe.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="4bbc9-114">Le chargeur garantit qu’elles ne sont pas remplacées.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bbc9-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4bbc9-115">In This Section</span></span>  
 [<span data-ttu-id="4bbc9-116">Appel de méthodes synchrones de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="4bbc9-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="4bbc9-117">Décrit l’utilisation de délégués pour effectuer des appels asynchrones à des méthodes ordinaires et fournit des exemples de code simples qui présentent les quatre façons d’attendre un appel asynchrone à retourner.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4bbc9-118">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="4bbc9-118">Related Sections</span></span>  
 [<span data-ttu-id="4bbc9-119">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="4bbc9-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="4bbc9-120">Décrit la programmation asynchrone avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4bbc9-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbc9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bbc9-121">See also</span></span>

- <xref:System.Delegate>
