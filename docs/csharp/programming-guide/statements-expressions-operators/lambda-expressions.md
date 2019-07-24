---
title: Expressions lambda - Guide de programmation C#
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 546feb6f3c4515ceecdb5b5afa14c0fc99ab7020
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363912"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="3165f-102">Expressions lambda (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3165f-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="3165f-103">Une *expression lambda* est un bloc de code (une expression ou un bloc d’instructions) qui est traité comme un objet.</span><span class="sxs-lookup"><span data-stu-id="3165f-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="3165f-104">Elle peut être passée comme argument à des méthodes, et peut aussi être retournée par des appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="3165f-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="3165f-105">Les expressions lambda sont largement utilisées pour :</span><span class="sxs-lookup"><span data-stu-id="3165f-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="3165f-106">Passer le code à exécuter à des méthodes asynchrones, comme <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3165f-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="3165f-107">Écrire des [expressions de requête LINQ](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="3165f-108">Créer des [arborescences d’expressions](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="3165f-109">Les expressions lambda sont du code qui peut être représenté comme un délégué, ou comme une arborescence d’expressions qui est compilée en délégué.</span><span class="sxs-lookup"><span data-stu-id="3165f-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="3165f-110">Le type délégué spécifique d’une expression lambda dépend de ses paramètres et de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="3165f-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="3165f-111">Les expressions lambda qui ne retournent pas de valeur correspondent à un délégué `Action` spécifique, en fonction du nombre de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="3165f-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="3165f-112">Les expressions lambda qui retournent une valeur correspondent à un délégué `Func` spécifique, en fonction du nombre de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="3165f-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="3165f-113">Par exemple, une expression lambda qui a deux paramètres, mais qui ne retourne aucune valeur correspond à un délégué <xref:System.Action%602>.</span><span class="sxs-lookup"><span data-stu-id="3165f-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="3165f-114">Une expression lambda qui a un paramètre et qui retourne une valeur correspond à un délégué <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="3165f-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="3165f-115">Une expression lambda utilise `=>`, l’[opérateur de déclaration lambda](../../language-reference/operators/lambda-operator.md), pour séparer la liste des paramètres de l’expression lambda de son code exécutable.</span><span class="sxs-lookup"><span data-stu-id="3165f-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="3165f-116">Pour créer une expression lambda, vous spécifiez des paramètres d’entrée (le cas échéant) du côté gauche de l’opérateur lambda, et vous placez l’expression ou le bloc d’instructions de l’autre côté.</span><span class="sxs-lookup"><span data-stu-id="3165f-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="3165f-117">Par exemple, l’expression lambda d’une seule ligne `x => x * x` spécifie un paramètre nommé `x` et retourne la valeur `x` élevée au carré.</span><span class="sxs-lookup"><span data-stu-id="3165f-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="3165f-118">Vous pouvez assigner cette expression à un type délégué, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3165f-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="3165f-119">Il est également possible d’affecter une expression lambda à un type d’arborescence d’expression :</span><span class="sxs-lookup"><span data-stu-id="3165f-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="3165f-120">Vous pouvez aussi le passer directement comme argument de méthode :</span><span class="sxs-lookup"><span data-stu-id="3165f-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="3165f-121">Lorsque la méthode <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> est appelée avec une syntaxe fondée sur une méthode dans la classe <xref:System.Linq.Enumerable?displayProperty=nameWithType> (comme dans LINQ to Objects et LINQ to XML), le paramètre est un type délégué <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3165f-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3165f-122">Une expression lambda est la méthode la plus commode pour créer ce délégué.</span><span class="sxs-lookup"><span data-stu-id="3165f-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="3165f-123">Si la méthode <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> est appelée dans la classe <xref:System.Linq.Queryable?displayProperty=nameWithType> (comme dans LINQ to SQL), le paramètre est un type d’arborescence d’expression [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="3165f-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="3165f-124">Une expression lambda est simplement une méthode très concise pour construire cette arborescence de l'expression.</span><span class="sxs-lookup"><span data-stu-id="3165f-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="3165f-125">Les lambdas font apparaître les appels `Select` comme semblables bien qu'en fait, le type d'objet créé à partir du lambda soit différent.</span><span class="sxs-lookup"><span data-stu-id="3165f-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="3165f-126">Expressions lambdas</span><span class="sxs-lookup"><span data-stu-id="3165f-126">Expression lambdas</span></span>

<span data-ttu-id="3165f-127">Une expression lambda comportant une expression à droite de l’opérateur `=>` est appelée *expression lambda*.</span><span class="sxs-lookup"><span data-stu-id="3165f-127">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="3165f-128">Les expressions lambda sont utilisées en grand nombre dans la construction d’[arborescences d’expressions](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-128">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="3165f-129">Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :</span><span class="sxs-lookup"><span data-stu-id="3165f-129">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="3165f-130">Les parenthèses sont facultatives uniquement si le lambda comporte un paramètre d'entrée ; sinon, elles sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="3165f-130">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="3165f-131">Utilisez des parenthèses vides s'il n'y a aucun paramètre d'entrée :</span><span class="sxs-lookup"><span data-stu-id="3165f-131">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="3165f-132">Les paramètres d'entrée sont séparés par des virgules entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="3165f-132">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="3165f-133">Il est parfois impossible pour le compilateur de déduire les types d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3165f-133">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="3165f-134">Vous pouvez spécifier les types explicitement comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3165f-134">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="3165f-135">Les types de paramètres d’entrée doivent être tous explicites ou tous implicites ; sinon, une erreur de compilateur [CS0748](../../misc/cs0748.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="3165f-135">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="3165f-136">Le corps d’une expression lambda peut se composer d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3165f-136">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="3165f-137">Cependant, si vous créez des arborescences d’expressions évaluées en dehors du contexte du common language runtime .NET, comme dans SQL Server, vous ne devez pas utiliser d’appels de méthode dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-137">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="3165f-138">Les méthodes n'auront aucune signification en dehors du contexte du Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="3165f-138">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="3165f-139">Instructions lambda</span><span class="sxs-lookup"><span data-stu-id="3165f-139">Statement lambdas</span></span>

<span data-ttu-id="3165f-140">Une instruction lambda ressemble à une expression lambda, mais l'instruction ou les instructions sont mises entre accolades :</span><span class="sxs-lookup"><span data-stu-id="3165f-140">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="3165f-141">Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.</span><span class="sxs-lookup"><span data-stu-id="3165f-141">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="3165f-142">Les instructions lambda ne peuvent pas être utilisées pour créer des arborescences d'expression.</span><span class="sxs-lookup"><span data-stu-id="3165f-142">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="3165f-143">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="3165f-143">Async lambdas</span></span>

<span data-ttu-id="3165f-144">Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../../language-reference/keywords/async.md) et [await](../../language-reference/keywords/await.md) .</span><span class="sxs-lookup"><span data-stu-id="3165f-144">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="3165f-145">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="3165f-145">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="3165f-146">Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3165f-146">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="3165f-147">Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3165f-147">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="3165f-148">Pour plus d’informations sur la création et l’utilisation des méthodes asyncrones, consultez [Programmation asynchrone avec async et await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-148">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="3165f-149">Expressions lambda et tuples</span><span class="sxs-lookup"><span data-stu-id="3165f-149">Lambda expressions and tuples</span></span>

<span data-ttu-id="3165f-150">À compter de sa version 7.0, le langage C# offre une prise en charge intégrée des [tuples](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-150">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="3165f-151">Vous pouvez fournir un tuple comme argument à une expression lambda, et votre expression lambda peut aussi retourner un tuple.</span><span class="sxs-lookup"><span data-stu-id="3165f-151">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="3165f-152">Dans certains cas, le compilateur C# utilise l’inférence de type pour déterminer les types des composants du tuple.</span><span class="sxs-lookup"><span data-stu-id="3165f-152">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="3165f-153">Vous définissez un tuple en plaçant entre des parenthèses une liste de ses composants avec des virgules comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="3165f-153">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="3165f-154">L’exemple suivant utilise un tuple à trois composants pour passer une séquence de nombres à une expression lambda, qui double chaque valeur et retourne un tuple à trois composants contenant le résultat des multiplications.</span><span class="sxs-lookup"><span data-stu-id="3165f-154">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="3165f-155">En général, les champs d’un tuple sont nommés `Item1`, `Item2`, etc. Vous pouvez cependant définir un tuple avec des composants nommés, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3165f-155">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="3165f-156">Pour plus d’informations sur les tuples C#, voir [Types tuples C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-156">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="3165f-157">Lambdas avec les opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="3165f-157">Lambdas with the standard query operators</span></span>

<span data-ttu-id="3165f-158">LINQ to Objects, parmi d’autres implémentations, a un paramètre d’entrée dont le type fait partie de la famille <xref:System.Func%601> de délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="3165f-158">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="3165f-159">Ces délégués utilisent des paramètres de type pour définir le nombre et le type des paramètres d’entrée, ainsi que le type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="3165f-159">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="3165f-160">Les délégués`Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources.</span><span class="sxs-lookup"><span data-stu-id="3165f-160">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="3165f-161">Prenons par exemple le type délégué <xref:System.Func%602> :</span><span class="sxs-lookup"><span data-stu-id="3165f-161">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="3165f-162">Ce délégué peut être instancié comme une instance `Func<int, bool>`, où `int` est un paramètre d’entrée et `bool` la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="3165f-162">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="3165f-163">La valeur de retour est toujours spécifiée dans le dernier paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="3165f-163">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="3165f-164">Par exemple, `Func<int, string, bool>` définit un délégué avec deux paramètres d’entrée, `int` et `string`, et un type de retour `bool`.</span><span class="sxs-lookup"><span data-stu-id="3165f-164">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="3165f-165">Le délégué `Func` suivant, lorsqu’il est appelé, retourne une valeur booléenne indiquant si le paramètre d’entrée est égal à cinq :</span><span class="sxs-lookup"><span data-stu-id="3165f-165">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="3165f-166">Vous pouvez aussi fournir une expression lambda quand le type d’argument est <xref:System.Linq.Expressions.Expression%601>, par exemple, dans les opérateurs de requête standard définis dans le type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="3165f-166">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="3165f-167">Quand vous spécifiez un argument <xref:System.Linq.Expressions.Expression%601>, l’expression lambda est compilée en arborescence de l’expression.</span><span class="sxs-lookup"><span data-stu-id="3165f-167">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="3165f-168">L’exemple suivant utilise l’opérateur de requête standard <xref:System.Linq.Enumerable.Count%2A> :</span><span class="sxs-lookup"><span data-stu-id="3165f-168">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="3165f-169">Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="3165f-169">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="3165f-170">Cette expression lambda particulière compte les entiers (`n`) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.</span><span class="sxs-lookup"><span data-stu-id="3165f-170">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="3165f-171">L’exemple suivant produit une séquence qui contient tous les éléments du tableau `numbers` précédant le 9, car c’est le premier nombre de la séquence qui ne remplit pas la condition :</span><span class="sxs-lookup"><span data-stu-id="3165f-171">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="3165f-172">L’exemple suivant spécifie plusieurs paramètres d’entrée en les plaçant entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="3165f-172">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="3165f-173">La méthode retourne tous les éléments du tableau `numbers` jusqu’à ce qu’elle rencontre un nombre dont la valeur est inférieure à sa position ordinale dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="3165f-173">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="3165f-174">Inférence de type et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="3165f-174">Type inference in lambda expressions</span></span>

<span data-ttu-id="3165f-175">Il n’est généralement pas nécessaire, avec les expressions lambda, de spécifier un type pour les paramètres d’entrée, car le compilateur peut le déduire du corps de l’expression, des types de paramètres et d’autres facteurs, comme le décrit la spécification du langage C#.</span><span class="sxs-lookup"><span data-stu-id="3165f-175">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="3165f-176">Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source.</span><span class="sxs-lookup"><span data-stu-id="3165f-176">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="3165f-177">Si vous interrogez un `IEnumerable<Customer>`, le type de la variable d’entrée est inféré comme étant un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et à ses propriétés :</span><span class="sxs-lookup"><span data-stu-id="3165f-177">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="3165f-178">Voici les règles générales de l’inférence de type pour les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="3165f-178">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="3165f-179">Le lambda doit contenir le même nombre de paramètres que le type délégué.</span><span class="sxs-lookup"><span data-stu-id="3165f-179">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="3165f-180">Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="3165f-180">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="3165f-181">La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="3165f-181">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="3165f-182">Notez que les expressions lambda n’ont pas de type en elles-mêmes, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d’expression lambda ».</span><span class="sxs-lookup"><span data-stu-id="3165f-182">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="3165f-183">Toutefois, il est parfois commode de parler de manière informelle du « type » d’une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-183">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="3165f-184">Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-184">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="3165f-185">Capture des variables externes et de l’étendue variable dans les expressions lambda</span><span class="sxs-lookup"><span data-stu-id="3165f-185">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="3165f-186">Les expressions lambda peuvent faire référence à des *variables externes*.</span><span class="sxs-lookup"><span data-stu-id="3165f-186">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="3165f-187">Il s’agit de variables dans l’étendue de la méthode qui définit l’expression lambda, ou dans l’étendue du type qui contient l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-187">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="3165f-188">Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="3165f-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="3165f-189">Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="3165f-190">L'exemple suivant illustre ces règles :</span><span class="sxs-lookup"><span data-stu-id="3165f-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="3165f-191">Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="3165f-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="3165f-192">Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3165f-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="3165f-193">Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="3165f-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="3165f-194">Une expression lambda ne peut pas capturer directement un paramètre [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md) dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="3165f-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="3165f-195">Une instruction [return](../../language-reference/keywords/return.md) dans une expression lambda ne provoque pas le retour de la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="3165f-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="3165f-196">Une expression lambda ne peut pas contenir d’instruction [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md) ou [continue](../../language-reference/keywords/continue.md) si la cible de cette instruction de saut se trouve en dehors du bloc de l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="3165f-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="3165f-197">Il est également incorrect d’avoir une instruction de saut en dehors du bloc de l’expression lambda si la cible se trouve à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="3165f-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3165f-198">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3165f-198">C# language specification</span></span>

<span data-ttu-id="3165f-199">Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3165f-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="3165f-200">Chapitre proposé</span><span class="sxs-lookup"><span data-stu-id="3165f-200">Featured book chapter</span></span>

<span data-ttu-id="3165f-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="3165f-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3165f-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3165f-202">See also</span></span>

- [<span data-ttu-id="3165f-203">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3165f-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3165f-204">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="3165f-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="3165f-205">Arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3165f-205">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="3165f-206">Comparaison entre les fonctions locales et les expressions lambda</span><span class="sxs-lookup"><span data-stu-id="3165f-206">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="3165f-207">Expressions lambda implicitement typées</span><span class="sxs-lookup"><span data-stu-id="3165f-207">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="3165f-208">Exemples Visual Studio 2008 C# (voir les fichiers d’exemples de requêtes LINQ et le programme XQuery)</span><span class="sxs-lookup"><span data-stu-id="3165f-208">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="3165f-209">Expressions lambda récursives</span><span class="sxs-lookup"><span data-stu-id="3165f-209">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
