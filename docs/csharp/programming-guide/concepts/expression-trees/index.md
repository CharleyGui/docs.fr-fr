---
title: Arborescences d’expressions (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: c260e649e7bd285a6bd07b5a1cd7fc1a7f75b82a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241550"
---
# <a name="expression-trees-c"></a><span data-ttu-id="ec795-102">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="ec795-102">Expression Trees (C#)</span></span>
<span data-ttu-id="ec795-103">Les arborescences d'expressions représentent du code dans une structure de données arborescente, où chaque nœud est une expression, par exemple un appel de méthode ou une opération binaire comme `x < y`.</span><span class="sxs-lookup"><span data-stu-id="ec795-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="ec795-104">Vous pouvez compiler et exécuter du code représenté par des arborescences d'expressions.</span><span class="sxs-lookup"><span data-stu-id="ec795-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="ec795-105">Ceci permet la modification dynamique du code exécutable, l'exécution de requêtes LINQ dans différentes bases de données et la création de requêtes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="ec795-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="ec795-106">Pour plus d’informations sur les arborescences d’expressions dans LINQ, consultez [comment utiliser des arborescences d’expression pour générer des requêtes dynamiques (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ec795-106">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="ec795-107">Les arborescences d’expressions sont également utilisées dans le Dynamic Language Runtime (DLR) pour assurer l’interopérabilité entre les langages dynamiques et .NET, ainsi que pour permettre aux Writers de compilateur d’émettre des arborescences d’expressions au lieu du langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ec795-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and .NET and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="ec795-108">Pour plus d’informations sur le DLR, consultez [Vue d’ensemble du Dynamic Language Runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec795-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="ec795-109">Le compilateur C# ou Visual Basic peut créer pour vous une arborescence d'expressions basée sur une expression lambda anonyme. Vous pouvez aussi créer manuellement des arborescences d'expressions en utilisant l'espace de noms <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="ec795-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="ec795-110">Création d’arborescences d’expressions à partir d’expressions lambda</span><span class="sxs-lookup"><span data-stu-id="ec795-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="ec795-111">Quand une expression lambda est affectée à une variable de type <xref:System.Linq.Expressions.Expression%601>, le compilateur produit du code pour générer une arborescence d'expressions qui représente l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="ec795-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="ec795-112">Le compilateur C# peut générer des arborescences d’expressions seulement à partir d’expressions lambda (ou de lambdas sur une seule ligne).</span><span class="sxs-lookup"><span data-stu-id="ec795-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="ec795-113">Ils ne peuvent pas analyser des lambdas d'instruction (ou lambdas multilignes).</span><span class="sxs-lookup"><span data-stu-id="ec795-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="ec795-114">Pour plus d’informations sur les expressions lambda en C#, consultez [Expressions lambda](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ec795-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="ec795-115">Les exemples de code suivants montrent comment le compilateur C# crée une arborescence d’expressions qui représente l’expression lambda `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="ec795-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="ec795-116">Création d’arborescences d’expressions à l’aide de l’API</span><span class="sxs-lookup"><span data-stu-id="ec795-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="ec795-117">Pour créer des arborescences d'expressions à l'aide de l'API, utilisez la classe <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="ec795-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="ec795-118">Cette classe contient des méthodes de fabrique statiques qui créent des nœuds d'arborescence d'expressions de types spécifiques, par exemple <xref:System.Linq.Expressions.ParameterExpression>, qui représente une variable ou un paramètre, ou <xref:System.Linq.Expressions.MethodCallExpression>, qui représente un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="ec795-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="ec795-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> et les autres types spécifiques à une expression sont également définis dans l'espace de noms <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="ec795-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="ec795-120">Ces types dérivent du type abstrait <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="ec795-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="ec795-121">L’exemple de code suivant montre comment créer une arborescence d’expressions qui représente l’expression lambda `num => num < 5` à l’aide de l’API.</span><span class="sxs-lookup"><span data-stu-id="ec795-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="ec795-122">Dans le .NET Framework 4 ou ultérieur, l’API des arborescences d’expressions prend également en charge les affectations et les expressions de flux de contrôle, comme les boucles, les blocs conditionnels et les blocs `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="ec795-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="ec795-123">À l’aide de l’API, vous pouvez créer des arborescences d’expressions qui sont plus complexes que celles qui peuvent être créées à partir d’expressions lambda par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="ec795-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="ec795-124">L’exemple suivant montre comment créer une arborescence d’expressions qui calcule la factorielle d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="ec795-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="ec795-125">Pour plus d’informations, consultez [Génération de méthodes dynamiques avec des arborescences d’expressions dans Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="ec795-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="ec795-126">Analyse des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="ec795-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="ec795-127">L’exemple de code suivant montre comment l’arborescence d’expressions qui représente l’expression lambda `num => num < 5` peut être décomposée selon ses différentes parties.</span><span class="sxs-lookup"><span data-stu-id="ec795-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="ec795-128">Immuabilité des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="ec795-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="ec795-129">Les arborescences d'expressions doivent être immuables.</span><span class="sxs-lookup"><span data-stu-id="ec795-129">Expression trees should be immutable.</span></span> <span data-ttu-id="ec795-130">Cela signifie que si vous voulez modifier une arborescence d'expressions, vous devez construire une nouvelle arborescence d'expressions en copiant l'arborescence existante et en y remplaçant les nœuds.</span><span class="sxs-lookup"><span data-stu-id="ec795-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="ec795-131">Vous pouvez utiliser un visiteur d’arborescence d’expressions pour parcourir l’arborescence d’expressions existante.</span><span class="sxs-lookup"><span data-stu-id="ec795-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="ec795-132">Pour plus d’informations, consultez [Comment modifier les arborescences d’expressions (C#)](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="ec795-132">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="ec795-133">Compilation des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="ec795-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="ec795-134">Le type <xref:System.Linq.Expressions.Expression%601> fournit la méthode <xref:System.Linq.Expressions.Expression%601.Compile%2A> qui compile le code représenté par une arborescence d'expressions en un délégué exécutable.</span><span class="sxs-lookup"><span data-stu-id="ec795-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="ec795-135">L’exemple de code suivant montre comment compiler une arborescence d’expressions et exécuter le code résultant.</span><span class="sxs-lookup"><span data-stu-id="ec795-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="ec795-136">Pour plus d’informations, consultez [comment exécuter des arborescences d’expressions (C#)](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="ec795-136">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ec795-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec795-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="ec795-138">Comment exécuter des arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="ec795-138">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="ec795-139">Comment modifier les arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="ec795-139">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="ec795-140">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="ec795-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="ec795-141">Vue d’ensemble du Dynamic Language Runtime</span><span class="sxs-lookup"><span data-stu-id="ec795-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="ec795-142">Concepts de programmation (C#)</span><span class="sxs-lookup"><span data-stu-id="ec795-142">Programming Concepts (C#)</span></span>](../index.md)
