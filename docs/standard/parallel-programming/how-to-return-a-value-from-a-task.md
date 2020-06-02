---
title: 'Procédure : retourner une valeur à partir d’une tâche'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 144d004d697b84a011cedafc7d07b679ef8852c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288145"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="abe33-102">Procédure : retourner une valeur à partir d’une tâche</span><span class="sxs-lookup"><span data-stu-id="abe33-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="abe33-103">Cet exemple montre comment utiliser le type <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pour retourner une valeur à partir de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="abe33-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="abe33-104">Il nécessite que le répertoire C:\Users\Public\Pictures\Sample Pictures\ existe et qu'il contienne des fichiers.</span><span class="sxs-lookup"><span data-stu-id="abe33-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abe33-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="abe33-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="abe33-106">La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> bloque le thread appelant jusqu'à ce que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="abe33-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="abe33-107">Pour savoir comment passer le résultat d’une <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> à une tâche de continuation, consultez [Chaînage des tâches à l’aide de tâches de continuation](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="abe33-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe33-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abe33-108">See also</span></span>

- [<span data-ttu-id="abe33-109">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="abe33-109">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="abe33-110">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="abe33-110">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
