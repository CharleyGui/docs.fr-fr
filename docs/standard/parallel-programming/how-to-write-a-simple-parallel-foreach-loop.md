---
title: Écrire un programme parallèle simple à l’aide de Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 02b94b673dc4468e68a1dadd83aab0e3bfcfaa16
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160298"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="a2cd7-102">Comment : écrire une boucle Parallel. ForEach simple</span><span class="sxs-lookup"><span data-stu-id="a2cd7-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="a2cd7-103">Cet exemple montre comment utiliser une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pour activer le parallélisme des données sur n’importe quelle source de données <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="a2cd7-104">Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="a2cd7-105">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="a2cd7-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="a2cd7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2cd7-106">Example</span></span>

<span data-ttu-id="a2cd7-107">Cet exemple part du principe que vous disposez de plusieurs fichiers .jpg dans un dossier *C:\Users\Public\Pictures\Sample Pictures*, et crée un sous-dossier nommé *Modified* (Modifié).</span><span class="sxs-lookup"><span data-stu-id="a2cd7-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="a2cd7-108">Lorsque vous exécutez l’exemple, il fait pivoter chaque image .jpg dans *Sample Pictures* (Exemples d’images) et les enregistre dans le sous-dossier *Modified*.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="a2cd7-109">Vous pouvez modifier les deux chemins d’accès en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="a2cd7-110">Une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> fonctionne comme une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="a2cd7-111">Les boucles partitionnent la collection source et planifient le travail sur plusieurs threads en fonction de l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="a2cd7-112">Plus il y a de processeurs sur le système, plus la méthode parallèle s’exécute rapidement.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="a2cd7-113">Pour certaines collections sources, une boucle séquentielle peut être plus rapide, selon la taille de la source et le type de travail exécuté par la boucle.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="a2cd7-114">Pour plus d’informations sur les performances, consultez [pièges potentiels dans le parallélisme des données et des tâches](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="a2cd7-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="a2cd7-115">Pour plus d’informations sur les boucles parallèles, consultez [Comment : écrire une boucle Parallel. for simple](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="a2cd7-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="a2cd7-116">Pour utiliser <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> avec une collection non générique, vous pouvez utiliser la méthode d’extension <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> pour convertir la collection en une collection générique, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a2cd7-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="a2cd7-117">Vous pouvez également utiliser PLINQ (Parallel LINQ) pour paralléliser le traitement des sources de données <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="a2cd7-118">PLINQ vous permet d’utiliser la syntaxe de requête déclarative pour exprimer le comportement de la boucle.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="a2cd7-119">Pour plus d’informations, consultez la page [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="a2cd7-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="a2cd7-120">Compiler et exécuter le code</span><span class="sxs-lookup"><span data-stu-id="a2cd7-120">Compile and run the code</span></span>

<span data-ttu-id="a2cd7-121">Vous pouvez compiler le code en tant qu’application de console pour .NET Framework ou en tant qu’application de console pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="a2cd7-122">Dans Visual Studio, il existe des modèles d’application de console Visual Basic et C# pour Windows Desktop et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="a2cd7-123">À partir de la ligne de commande, vous pouvez utiliser les commandes CLI .NET Core (par exemple, `dotnet new console` ou `dotnet new console -lang vb`), ou vous pouvez créer le fichier et utiliser le compilateur de ligne de commande pour une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-123">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="a2cd7-124">Pour un projet .NET Core, vous devez référencer le package NuGet **System.Drawing.Common**.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="a2cd7-125">Dans Visual Studio, utilisez le gestionnaire de package NuGet pour installer le package.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="a2cd7-126">Vous pouvez aussi ajouter une référence au package dans votre fichier \*.csproj ou \*.vbproj :</span><span class="sxs-lookup"><span data-stu-id="a2cd7-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="a2cd7-127">Pour exécuter une application de console .NET Core depuis la ligne de commande, utilisez `dotnet run` depuis le dossier qui contient votre application.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="a2cd7-128">Pour exécuter votre application de console depuis Visual Studio, appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="a2cd7-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2cd7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2cd7-129">See also</span></span>

- [<span data-ttu-id="a2cd7-130">Parallélisme de données</span><span class="sxs-lookup"><span data-stu-id="a2cd7-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="a2cd7-131">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="a2cd7-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="a2cd7-132">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a2cd7-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
