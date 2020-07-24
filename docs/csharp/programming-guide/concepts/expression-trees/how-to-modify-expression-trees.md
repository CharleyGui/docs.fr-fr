---
title: Comment modifier les arborescences d’expressions (C#)
description: Découvrez comment modifier une arborescence d’expressions en créant une copie d’une arborescence d’expressions existante et en effectuant les modifications requises.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105609"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="4b797-103">Comment modifier les arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="4b797-103">How to modify expression trees (C#)</span></span>
<span data-ttu-id="4b797-104">Cette rubrique montre comment modifier une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="4b797-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="4b797-105">Les arborescences d’expressions sont immuables, ce qui signifie qu’elles ne peuvent pas être modifiées directement.</span><span class="sxs-lookup"><span data-stu-id="4b797-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="4b797-106">Pour changer une arborescence d’expressions, vous devez créer une copie d’une arborescence d’expressions existante et, quand vous créez la copie, apporter les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="4b797-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="4b797-107">Vous pouvez utiliser la classe <xref:System.Linq.Expressions.ExpressionVisitor> pour parcourir une arborescence d’expressions existante et copier chaque nœud visité.</span><span class="sxs-lookup"><span data-stu-id="4b797-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="4b797-108">Pour modifier une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="4b797-108">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="4b797-109">Créez un projet d' **application console** .</span><span class="sxs-lookup"><span data-stu-id="4b797-109">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="4b797-110">Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="4b797-110">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="4b797-111">Ajoutez la classe `AndAlsoModifier` à votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b797-111">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     <span data-ttu-id="4b797-112">Cette classe hérite de la classe `AND` et est spécialisée pour modifier les expressions qui représentent des opérations <xref:System.Linq.Expressions.ExpressionVisitor> conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="4b797-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="4b797-113">Elle convertit ces opérations d’un `AND` conditionnel en un `OR` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="4b797-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="4b797-114">Pour ce faire, la classe substitue la méthode <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> du type de base, car les expressions `AND` conditionnelles sont représentées sous forme d’expressions binaires.</span><span class="sxs-lookup"><span data-stu-id="4b797-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="4b797-115">Dans la méthode `VisitBinary`, si l’expression passée représente une opération `AND` conditionnelle, le code construit une nouvelle expression qui contient l’opérateur `OR` conditionnel au lieu de l’opérateur `AND` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="4b797-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="4b797-116">Si l’expression passée à `VisitBinary` ne représente pas une opération `AND` conditionnelle, la méthode emploie l’implémentation de classe de base.</span><span class="sxs-lookup"><span data-stu-id="4b797-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="4b797-117">Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expressions passées, mais les nœuds voient leurs sous-arborescences remplacées par les arborescences d’expressions produites de manière récursive par le visiteur.</span><span class="sxs-lookup"><span data-stu-id="4b797-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="4b797-118">Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="4b797-118">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="4b797-119">Ajoutez le code à la méthode `Main` dans le fichier Program.cs pour créer une arborescence d’expressions, et passez-le à la méthode qui le modifiera.</span><span class="sxs-lookup"><span data-stu-id="4b797-119">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     <span data-ttu-id="4b797-120">Le code crée une expression qui contient une opération `AND` conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="4b797-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="4b797-121">Il crée ensuite une instance de la classe `AndAlsoModifier` et passe l’expression à la méthode `Modify` de cette classe.</span><span class="sxs-lookup"><span data-stu-id="4b797-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="4b797-122">Les arborescences d’expressions d’origine et modifiée sont toutes deux générées pour montrer la modification.</span><span class="sxs-lookup"><span data-stu-id="4b797-122">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="4b797-123">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4b797-123">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b797-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b797-124">See also</span></span>

- [<span data-ttu-id="4b797-125">Comment exécuter des arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="4b797-125">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="4b797-126">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="4b797-126">Expression Trees (C#)</span></span>](./index.md)
