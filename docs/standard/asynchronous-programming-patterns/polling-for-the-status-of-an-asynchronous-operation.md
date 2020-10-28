---
title: Interrogation de l'état d'une opération asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: c73ee50c67034feed07a4869deb0a32342bb45e5
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888735"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="b17ed-102">Interrogation de l'état d'une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="b17ed-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="b17ed-103">Les applications qui peuvent continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone ne doivent pas se bloquer en attendant que cette opération se termine.</span><span class="sxs-lookup"><span data-stu-id="b17ed-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="b17ed-104">Pour poursuivre l’exécution des instructions tout en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b17ed-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="b17ed-105">Utilisez la <xref:System.IAsyncResult.IsCompleted%2A> propriété du <xref:System.IAsyncResult> retourné par la méthode **Begin**_NomOpération_ de l’opération asynchrone pour déterminer si l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="b17ed-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="b17ed-106">Cette approche, nommée interrogation, est illustrée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b17ed-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="b17ed-107">Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="b17ed-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="b17ed-108">Vous trouverez un exemple illustrant cette approche sur la page [Utiliser un délégué AsyncCallback pour mettre fin à une opération asynchrone](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b17ed-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b17ed-109">Example</span></span>  
 <span data-ttu-id="b17ed-110">L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour un ordinateur spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b17ed-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="b17ed-111">Cet exemple démarre l’opération asynchrone, puis imprime des points (« . ») dans la console jusqu'à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="b17ed-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="b17ed-112">Notez que **null** ( **Nothing** en Visual Basic) est transmis aux paramètres <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> et <xref:System.Object>, car ces arguments ne sont pas requis dans cette approche.</span><span class="sxs-lookup"><span data-stu-id="b17ed-112">Note that **null** ( **Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b17ed-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b17ed-113">See also</span></span>

- [<span data-ttu-id="b17ed-114">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="b17ed-114">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="b17ed-115">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="b17ed-115">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
