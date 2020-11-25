---
title: 'Procédure : inclure dans un wrapper des modèles EAP dans une tâche'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 667de563a53695f7b8f4782a2bdd5b753673b4e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728210"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="c44a0-102">Procédure : inclure dans un wrapper des modèles EAP dans une tâche</span><span class="sxs-lookup"><span data-stu-id="c44a0-102">How to: Wrap EAP Patterns in a Task</span></span>

<span data-ttu-id="c44a0-103">L’exemple suivant montre comment exposer une séquence arbitraire d’opérations EAP (modèle asynchrone basé sur des événements) comme une seule tâche à l’aide d’un <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="c44a0-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="c44a0-104">L’exemple montre également comment utiliser un <xref:System.Threading.CancellationToken> pour appeler les méthodes d’annulation intégrées sur les objets <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="c44a0-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c44a0-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c44a0-105">Example</span></span>  

 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="c44a0-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c44a0-106">See also</span></span>

- [<span data-ttu-id="c44a0-107">TPL et programmation asynchrone .NET traditionnelle</span><span class="sxs-lookup"><span data-stu-id="c44a0-107">TPL and Traditional .NET Asynchronous Programming</span></span>](tpl-and-traditional-async-programming.md)
