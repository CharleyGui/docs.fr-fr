---
title: Expression Trees
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266415"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="220c9-102">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="220c9-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="220c9-103">Les arborescences d'expressions représentent du code dans une structure de données arborescente, où chaque nœud est une expression, par exemple un appel de méthode ou une opération binaire comme `x < y`.</span><span class="sxs-lookup"><span data-stu-id="220c9-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="220c9-104">Vous pouvez compiler et exécuter du code représenté par des arborescences d'expressions.</span><span class="sxs-lookup"><span data-stu-id="220c9-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="220c9-105">Ceci permet la modification dynamique du code exécutable, l'exécution de requêtes LINQ dans différentes bases de données et la création de requêtes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="220c9-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="220c9-106">Pour plus d’informations sur les arborescences d’expressions dans LINQ, consultez [Guide pratique pour utiliser des arborescences d’expressions pour générer des requêtes dynamiques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="220c9-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="220c9-107">Les arborescences d’expressions sont également utilisées dans l’environnement d’exécution de langage dynamique (DLR, Dynamic Language Runtime) pour fournir une interopérabilité entre les langages dynamiques et .NET Framework, ainsi que pour permettre aux writers de compilateur d’émettre des arborescences d’expressions au lieu d’utiliser le langage intermédiaire MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="220c9-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="220c9-108">Pour plus d’informations sur le DLR, consultez [Vue d’ensemble du Dynamic Language Runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="220c9-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="220c9-109">Le compilateur C# ou Visual Basic peut créer pour vous une arborescence d'expressions basée sur une expression lambda anonyme. Vous pouvez aussi créer manuellement des arborescences d'expressions en utilisant l'espace de noms <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="220c9-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="220c9-110">Création d’arborescences d’expressions à partir d’expressions lambda</span><span class="sxs-lookup"><span data-stu-id="220c9-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="220c9-111">Quand une expression lambda est affectée à une variable de type <xref:System.Linq.Expressions.Expression%601>, le compilateur produit du code pour générer une arborescence d'expressions qui représente l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="220c9-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="220c9-112">Le compilateur Visual Basic peut générer des arborescences d’expressions seulement à partir d’expressions lambda (ou de lambdas sur une seule ligne).</span><span class="sxs-lookup"><span data-stu-id="220c9-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="220c9-113">Ils ne peuvent pas analyser des lambdas d'instruction (ou lambdas multilignes).</span><span class="sxs-lookup"><span data-stu-id="220c9-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="220c9-114">Pour plus d’informations sur les expressions lambda en Visual Basic, consultez [Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="220c9-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="220c9-115">Les exemples de code suivants montrent comment le compilateur Visual Basic crée une arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="220c9-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="220c9-116">Création d’arborescences d’expressions à l’aide de l’API</span><span class="sxs-lookup"><span data-stu-id="220c9-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="220c9-117">Pour créer des arborescences d'expressions à l'aide de l'API, utilisez la classe <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="220c9-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="220c9-118">Cette classe contient des méthodes de fabrique statiques qui créent des nœuds d'arborescence d'expressions de types spécifiques, par exemple <xref:System.Linq.Expressions.ParameterExpression>, qui représente une variable ou un paramètre, ou <xref:System.Linq.Expressions.MethodCallExpression>, qui représente un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="220c9-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="220c9-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> et les autres types spécifiques à une expression sont également définis dans l'espace de noms <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="220c9-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="220c9-120">Ces types dérivent du type abstrait <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="220c9-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="220c9-121">L’exemple de code suivant montre comment créer une arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5` à l’aide de l’API.</span><span class="sxs-lookup"><span data-stu-id="220c9-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="220c9-122">Dans le .NET Framework 4 ou ultérieur, l’API des arborescences d’expressions prend également en charge les affectations et les expressions de flux de contrôle, comme les boucles, les blocs conditionnels et les blocs `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="220c9-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="220c9-123">À l’aide de l’API, vous pouvez créer des arborescences d’expressions qui sont plus complexes que celles qui peuvent être créées à partir d’expressions lambda par le compilateur Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="220c9-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="220c9-124">L’exemple suivant montre comment créer une arborescence d’expressions qui calcule la factorielle d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="220c9-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="220c9-125">Pour plus d’informations, consultez [Génération de méthodes dynamiques avec des arborescences d’expressions dans Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="220c9-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="220c9-126">Analyse des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="220c9-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="220c9-127">L’exemple de code suivant montre comment l’arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5` peut être décomposée selon ses différentes parties.</span><span class="sxs-lookup"><span data-stu-id="220c9-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="220c9-128">Immuabilité des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="220c9-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="220c9-129">Les arborescences d'expressions doivent être immuables.</span><span class="sxs-lookup"><span data-stu-id="220c9-129">Expression trees should be immutable.</span></span> <span data-ttu-id="220c9-130">Cela signifie que si vous voulez modifier une arborescence d'expressions, vous devez construire une nouvelle arborescence d'expressions en copiant l'arborescence existante et en y remplaçant les nœuds.</span><span class="sxs-lookup"><span data-stu-id="220c9-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="220c9-131">Vous pouvez utiliser un visiteur d’arborescence d’expressions pour parcourir l’arborescence d’expressions existante.</span><span class="sxs-lookup"><span data-stu-id="220c9-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="220c9-132">Pour plus d’informations, consultez [Guide pratique pour modifier des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="220c9-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="220c9-133">Compilation des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="220c9-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="220c9-134">Le type <xref:System.Linq.Expressions.Expression%601> fournit la méthode <xref:System.Linq.Expressions.Expression%601.Compile%2A> qui compile le code représenté par une arborescence d'expressions en un délégué exécutable.</span><span class="sxs-lookup"><span data-stu-id="220c9-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="220c9-135">L’exemple de code suivant montre comment compiler une arborescence d’expressions et exécuter le code résultant.</span><span class="sxs-lookup"><span data-stu-id="220c9-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="220c9-136">Pour plus d’informations, consultez [Guide pratique pour exécuter des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="220c9-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220c9-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="220c9-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="220c9-138">Guide pratique pour exécuter des arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="220c9-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="220c9-139">Guide pratique pour modifier des arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="220c9-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="220c9-140">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="220c9-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="220c9-141">Aperçu dynamique du temps d’exécution du langage</span><span class="sxs-lookup"><span data-stu-id="220c9-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="220c9-142">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="220c9-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
