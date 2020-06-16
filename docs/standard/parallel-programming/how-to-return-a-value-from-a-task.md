---
title: 'Procédure : retourner une valeur à partir d’une tâche'
description: Consultez Comment utiliser le type System. Threading. Tasks. Task <TResult> pour retourner une valeur à partir de la propriété Result dans .net.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767973"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="64206-103">Procédure : retourner une valeur à partir d’une tâche</span><span class="sxs-lookup"><span data-stu-id="64206-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="64206-104">Cet exemple montre comment utiliser le type <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pour retourner une valeur à partir de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="64206-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="64206-105">Il nécessite que le répertoire C:\Users\Public\Pictures\Sample Pictures\ existe et qu'il contienne des fichiers.</span><span class="sxs-lookup"><span data-stu-id="64206-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64206-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="64206-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="64206-107">La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> bloque le thread appelant jusqu'à ce que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="64206-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="64206-108">Pour savoir comment passer le résultat d’une <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> à une tâche de continuation, consultez [Chaînage des tâches à l’aide de tâches de continuation](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="64206-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64206-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64206-109">See also</span></span>

- [<span data-ttu-id="64206-110">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="64206-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="64206-111">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="64206-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
