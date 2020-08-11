---
title: Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 469c164630e1dab84b3d54c16c43d031ebf560ed
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063768"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="35750-102">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="35750-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="35750-103">La bibliothèque parallèle de tâches (TPL) contient de nombreuses méthodes qui utilisent l’une des familles <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> de délégués comme paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="35750-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="35750-104">Vous utilisez ces délégués pour transmettre votre logique de programme personnalisée à la boucle, la tâche ou la requête parallèle.</span><span class="sxs-lookup"><span data-stu-id="35750-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="35750-105">Les exemples de code de la bibliothèque parallèle de tâches, ainsi que PLINQ, utilisent des expressions lambda pour créer des instances de ces délégués comme blocs de code inline.</span><span class="sxs-lookup"><span data-stu-id="35750-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="35750-106">Cette rubrique est une brève présentation de Func et Action et vous montre comment utiliser des expressions lambda dans la bibliothèque parallèle de tâches et PLINQ.</span><span class="sxs-lookup"><span data-stu-id="35750-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="35750-107">Pour plus d’informations sur les délégués en général, consultez [délégués](../../csharp/programming-guide/delegates/index.md) et [délégués](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="35750-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="35750-108">Pour plus d’informations sur les expressions lambda en C# et Visual Basic, consultez [Expressions lambda](../../csharp/language-reference/operators/lambda-expressions.md) et [Expressions lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="35750-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/language-reference/operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="35750-109">Func (délégué)</span><span class="sxs-lookup"><span data-stu-id="35750-109">Func Delegate</span></span>

<span data-ttu-id="35750-110">Un délégué `Func` encapsule une méthode qui renvoie une valeur.</span><span class="sxs-lookup"><span data-stu-id="35750-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="35750-111">Dans une `Func` signature, le dernier paramètre de type, ou le plus à droite, spécifie toujours le type de retour.</span><span class="sxs-lookup"><span data-stu-id="35750-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="35750-112">L’une des causes courantes d’erreurs de compilation consiste à tenter de transmettre deux paramètres d’entrée à un <xref:System.Func%602?displayProperty=nameWithType>. En fait, ce type ne prend qu’un paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="35750-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="35750-113">.Net définit 17 versions de `Func` : <xref:System.Func%601?displayProperty=nameWithType> , <xref:System.Func%602?displayProperty=nameWithType> , <xref:System.Func%603?displayProperty=nameWithType> , et ainsi de suite <xref:System.Func%6017?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="35750-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="35750-114">Action (délégué)</span><span class="sxs-lookup"><span data-stu-id="35750-114">Action Delegate</span></span>

<span data-ttu-id="35750-115">Un <xref:System.Action?displayProperty=nameWithType> délégué encapsule une méthode (Sub dans Visual Basic) qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="35750-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="35750-116">Dans une `Action` signature de type, les paramètres de type représentent uniquement des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="35750-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="35750-117">À l’instar de `Func` , .net définit 17 versions de `Action` , à partir d’une version qui n’a pas de paramètres de type jusqu’à une version avec 16 paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="35750-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="35750-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="35750-118">Example</span></span>

<span data-ttu-id="35750-119">L’exemple suivant pour la méthode <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> montre comment exprimer les délégués Func et Action à l’aide d’expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="35750-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="35750-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35750-120">See also</span></span>

- [<span data-ttu-id="35750-121">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="35750-121">Parallel Programming</span></span>](index.md)
