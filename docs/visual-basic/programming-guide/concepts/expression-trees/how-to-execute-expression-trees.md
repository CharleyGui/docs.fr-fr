---
title: 'Comment : exécuter des arborescences d’expression'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 7b7b08ea1a7a1310b1d98876be96f1fa28ecba91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375328"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="7c3b3-102">Guide pratique pour exécuter des arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c3b3-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="7c3b3-103">Cette rubrique montre comment exécuter une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="7c3b3-104">L’exécution d’une arborescence d’expressions peut retourner une valeur, ou elle peut simplement effectuer une action telle que l’appel d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="7c3b3-105">Seules les arborescences d’expressions qui représentent des expressions lambda peuvent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="7c3b3-106">Les arborescences d’expressions qui représentent des expressions lambda peuvent être de type <xref:System.Linq.Expressions.LambdaExpression> ou <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="7c3b3-107">Pour exécuter ces arborescences d’expressions, appelez la méthode <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> pour créer un délégué exécutable, puis appelez le délégué.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c3b3-108">Si le type du délégué n’est pas connu, autrement dit si l’expression lambda est de type <xref:System.Linq.Expressions.LambdaExpression> et non <xref:System.Linq.Expressions.Expression%601>, vous devez appeler la méthode <xref:System.Delegate.DynamicInvoke%2A> sur le délégué au lieu de l’appeler directement.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="7c3b3-109">Si une arborescence d’expressions ne représente pas une expression lambda, vous pouvez créer une expression lambda ayant l’arborescence d’expressions d’origine comme corps, en appelant la méthode <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="7c3b3-110">Ensuite, vous pouvez exécuter l’expression lambda comme décrit plus haut dans cette section.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3b3-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c3b3-111">Example</span></span>  
 <span data-ttu-id="7c3b3-112">L’exemple de code suivant montre comment exécuter une arborescence d’expressions qui représente l’élévation d’un nombre à une puissance en créant une expression lambda et en l’exécutant.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="7c3b3-113">Le résultat, qui représente le nombre élevé à la puissance, est affiché.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="7c3b3-114">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="7c3b3-114">Compile the code</span></span>  
  
- <span data-ttu-id="7c3b3-115">Incluez l’espace de noms System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="7c3b3-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c3b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c3b3-116">See also</span></span>

- [<span data-ttu-id="7c3b3-117">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c3b3-117">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="7c3b3-118">Guide pratique pour modifier des arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c3b3-118">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
