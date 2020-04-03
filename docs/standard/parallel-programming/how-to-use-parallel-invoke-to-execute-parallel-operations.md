---
title: 'Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635802"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="a7582-102">Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles</span><span class="sxs-lookup"><span data-stu-id="a7582-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="a7582-103">Cet exemple indique comment paralléliser des opérations à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A> dans la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="a7582-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="a7582-104">Trois opérations sont effectuées sur la source de données partagée.</span><span class="sxs-lookup"><span data-stu-id="a7582-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="a7582-105">Les opérations peuvent être exécutées en parallèle d’une manière simple, car aucune d’entre elles ne modifie la source.</span><span class="sxs-lookup"><span data-stu-id="a7582-105">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="a7582-106">Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="a7582-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="a7582-107">Si vous n’êtes pas familier avec les expressions lambda dans C ou Visual Basic, voir [Lambda Expressions dans PLINQ et TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="a7582-107">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7582-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7582-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="a7582-109">Avec <xref:System.Threading.Tasks.Parallel.Invoke%2A>, vous exprimez simplement les actions que vous souhaitez exécuter simultanément, et le temps d’exécution gère tous les détails de planification de thread, y compris la mise à l’échelle automatiquement au nombre de cœurs sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="a7582-109">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="a7582-110">Cet exemple parallélise les opérations et non les données.</span><span class="sxs-lookup"><span data-stu-id="a7582-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="a7582-111">Vous pouvez également paralléliser les requêtes LINQ à l'aide de PLINQ et exécuter les requêtes séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="a7582-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="a7582-112">Vous pouvez aussi paralléliser les données à l'aide de PLINQ.</span><span class="sxs-lookup"><span data-stu-id="a7582-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="a7582-113">Une autre option consiste à paralléliser à la fois les requêtes et les tâches.</span><span class="sxs-lookup"><span data-stu-id="a7582-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="a7582-114">Bien que les frais généraux qui en résultent pourraient dégrader les performances sur les ordinateurs hôtes avec relativement peu de processeurs, il s’évolue mieux sur les ordinateurs avec de nombreux processeurs.</span><span class="sxs-lookup"><span data-stu-id="a7582-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="a7582-115">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="a7582-115">Compile the Code</span></span>

<span data-ttu-id="a7582-116">Copiez et collez l'exemple entier dans un projet Microsoft Visual Studio et appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="a7582-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7582-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7582-117">See also</span></span>

- [<span data-ttu-id="a7582-118">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="a7582-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="a7582-119">Comment : annuler une tâche et ses enfants</span><span class="sxs-lookup"><span data-stu-id="a7582-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="a7582-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a7582-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
