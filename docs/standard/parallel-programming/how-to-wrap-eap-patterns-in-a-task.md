---
title: "Comment : exposer des modèles EAP à l'aide d'une tâche"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: ac7436892c644340286bb4670bf75c9cd63a8ce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106818"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="9dd14-102">Comment : exposer des modèles EAP à l'aide d'une tâche</span><span class="sxs-lookup"><span data-stu-id="9dd14-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="9dd14-103">L’exemple suivant montre comment exposer une séquence arbitraire d’opérations EAP (modèle asynchrone basé sur des événements) comme une seule tâche à l’aide d’un <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="9dd14-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="9dd14-104">L’exemple montre également comment utiliser un <xref:System.Threading.CancellationToken> pour appeler les méthodes d’annulation intégrées sur les objets <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="9dd14-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd14-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9dd14-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="9dd14-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dd14-106">See also</span></span>

- [<span data-ttu-id="9dd14-107">Bibliothèque parallèle de tâches (TPL) et programmation asynchrone .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9dd14-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
