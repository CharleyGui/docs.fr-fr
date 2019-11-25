---
title: 'Comment : modifier des arborescences d’expression'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353747"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="e6aba-102">How to: Modify Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6aba-102">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="e6aba-103">Cette rubrique montre comment modifier une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="e6aba-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e6aba-104">Les arborescences d’expressions sont immuables, ce qui signifie qu’elles ne peuvent pas être modifiées directement.</span><span class="sxs-lookup"><span data-stu-id="e6aba-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e6aba-105">Pour changer une arborescence d’expressions, vous devez créer une copie d’une arborescence d’expressions existante et, quand vous créez la copie, apporter les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e6aba-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e6aba-106">Vous pouvez utiliser la classe <xref:System.Linq.Expressions.ExpressionVisitor> pour parcourir une arborescence d’expressions existante et copier chaque nœud visité.</span><span class="sxs-lookup"><span data-stu-id="e6aba-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e6aba-107">Pour modifier une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="e6aba-107">To modify an expression tree</span></span>

1. <span data-ttu-id="e6aba-108">Créez un projet d’**Application console**.</span><span class="sxs-lookup"><span data-stu-id="e6aba-108">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="e6aba-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span><span class="sxs-lookup"><span data-stu-id="e6aba-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="e6aba-110">Ajoutez la classe `AndAlsoModifier` à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e6aba-110">Add the `AndAlsoModifier` class to your project.</span></span>

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    <span data-ttu-id="e6aba-111">Cette classe hérite de la classe `AND` et est spécialisée pour modifier les expressions qui représentent des opérations <xref:System.Linq.Expressions.ExpressionVisitor> conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="e6aba-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e6aba-112">Elle convertit ces opérations d’un `AND` conditionnel en un `OR` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="e6aba-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e6aba-113">Pour ce faire, la classe substitue la méthode <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> du type de base, car les expressions `AND` conditionnelles sont représentées sous forme d’expressions binaires.</span><span class="sxs-lookup"><span data-stu-id="e6aba-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e6aba-114">Dans la méthode `VisitBinary`, si l’expression passée représente une opération `AND` conditionnelle, le code construit une nouvelle expression qui contient l’opérateur `OR` conditionnel au lieu de l’opérateur `AND` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="e6aba-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e6aba-115">Si l’expression passée à `VisitBinary` ne représente pas une opération `AND` conditionnelle, la méthode emploie l’implémentation de classe de base.</span><span class="sxs-lookup"><span data-stu-id="e6aba-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e6aba-116">Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expressions passées, mais les nœuds voient leurs sous-arborescences remplacées par les arborescences d’expressions produites de manière récursive par le visiteur.</span><span class="sxs-lookup"><span data-stu-id="e6aba-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="e6aba-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span><span class="sxs-lookup"><span data-stu-id="e6aba-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="e6aba-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span><span class="sxs-lookup"><span data-stu-id="e6aba-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    <span data-ttu-id="e6aba-119">Le code crée une expression qui contient une opération `AND` conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="e6aba-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e6aba-120">Il crée ensuite une instance de la classe `AndAlsoModifier` et passe l’expression à la méthode `Modify` de cette classe.</span><span class="sxs-lookup"><span data-stu-id="e6aba-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e6aba-121">Les arborescences d’expressions d’origine et modifiée sont toutes deux générées pour montrer la modification.</span><span class="sxs-lookup"><span data-stu-id="e6aba-121">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="e6aba-122">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="e6aba-122">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6aba-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6aba-123">See also</span></span>

- [<span data-ttu-id="e6aba-124">How to: Execute Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6aba-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="e6aba-125">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6aba-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
