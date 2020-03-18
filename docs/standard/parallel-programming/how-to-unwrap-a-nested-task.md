---
title: 'Comment : désencapsuler une tâche imbriquée'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106908"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="82240-102">Comment : désencapsuler une tâche imbriquée</span><span class="sxs-lookup"><span data-stu-id="82240-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="82240-103">Vous pouvez retourner une tâche à partir d’une méthode, puis attendre ou poursuivre à partir de cette tâche, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="82240-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="82240-104">Dans l’exemple précédent, la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> est de type `string` (`String` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="82240-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="82240-105">Toutefois, dans certains cas, il se peut que vous souhaitiez créer une tâche dans une autre tâche, puis retourner la tâche imbriquée.</span><span class="sxs-lookup"><span data-stu-id="82240-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="82240-106">Dans ce cas, le `TResult` de la tâche englobante est lui-même une tâche.</span><span class="sxs-lookup"><span data-stu-id="82240-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="82240-107">Dans l’exemple suivant, la propriété Result est une `Task<Task<string>>` en C# ou `Task(Of Task(Of String))` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82240-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="82240-108">Bien qu’il soit possible d’écrire du code pour désencapsuler la tâche externe et extraire la tâche d’origine et sa propriété <xref:System.Threading.Tasks.Task%601.Result%2A>, ce code n’est pas facile à écrire, car vous devez gérer des exceptions et des demandes d’annulation.</span><span class="sxs-lookup"><span data-stu-id="82240-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="82240-109">Dans ce cas, nous vous recommandons d’utiliser l’une des méthodes d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="82240-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="82240-110">Les méthodes <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> peuvent être utilisées pour transformer toute `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` en Visual Basic) en `Task` ou `Task<TResult>` (`Task(Of TResult)` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="82240-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="82240-111">La nouvelle tâche représente entièrement la tâche imbriquée interne et inclut l’état d’annulation ainsi que toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="82240-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82240-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="82240-112">Example</span></span>  
 <span data-ttu-id="82240-113">L'exemple suivant décrit comment utiliser la méthode d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="82240-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="82240-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82240-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="82240-115">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="82240-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
