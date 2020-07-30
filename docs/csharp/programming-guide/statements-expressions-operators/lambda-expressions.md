---
title: Expressions lambda - Guide de programmation C#
description: En savoir plus sur les expressions lambda. Il existe des lambdas d’expression qui ont une expression comme corps, ou des lambdas d’instruction qui ont un bloc d’instruction comme corps.
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 902a3f63967b371c940693464408ff39534917f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380707"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="35a5d-104">Expressions lambda (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="35a5d-104">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="35a5d-105">Une *expression lambda* est une expression de l’une des deux formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="35a5d-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="35a5d-106">[Expression lambda](#expression-lambdas) qui a une expression comme corps :</span><span class="sxs-lookup"><span data-stu-id="35a5d-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="35a5d-107">[Instruction lambda](#statement-lambdas) qui a un bloc d’instructions comme corps :</span><span class="sxs-lookup"><span data-stu-id="35a5d-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="35a5d-108">Utilisez l’[opérateur de déclaration lambda`=>`](../../language-reference/operators/lambda-operator.md) pour séparer la liste des paramètres de l’expression lambda de son corps.</span><span class="sxs-lookup"><span data-stu-id="35a5d-108">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="35a5d-109">Pour créer une expression lambda, vous spécifiez des paramètres d’entrée (le cas échéant) à gauche de l’opérateur lambda et une expression ou un bloc d’instructions de l’autre côté.</span><span class="sxs-lookup"><span data-stu-id="35a5d-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="35a5d-110">Toute expression lambda peut être convertie en type [délégué](../../language-reference/builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="35a5d-110">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="35a5d-111">Le type délégué vers lequel une expression lambda peut être convertie est défini par les types de ses paramètres et de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="35a5d-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="35a5d-112">Si une expression lambda ne retourne pas de valeur, elle peut être convertie en l’un des types délégués `Action` ; sinon, elle peut être convertie en l’un des types délégués `Func`.</span><span class="sxs-lookup"><span data-stu-id="35a5d-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="35a5d-113">Par exemple, une expression lambda qui a deux paramètres et qui ne retourne aucune valeur peut être convertie en un délégué <xref:System.Action%602>.</span><span class="sxs-lookup"><span data-stu-id="35a5d-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="35a5d-114">Une expression lambda qui a un paramètre et qui retourne une valeur peut être convertie en un délégué <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="35a5d-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="35a5d-115">Dans l’exemple suivant, l’expression lambda `x => x * x` , qui spécifie un paramètre nommé `x` et retourne la valeur du `x` carré, est assignée à une variable d’un type délégué :</span><span class="sxs-lookup"><span data-stu-id="35a5d-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="35a5d-116">Les expressions lambda d’expression peuvent également être converties en types d' [arborescences d’expression](../concepts/expression-trees/index.md) , comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="35a5d-116">Expression lambdas can also be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="35a5d-117">Vous pouvez utiliser des expressions lambda dans tout code qui requiert des instances de types délégués ou d’arborescences d’expressions, par exemple en tant qu’argument de la méthode <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> pour passer le code qui doit être exécuté en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="35a5d-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="35a5d-118">Vous pouvez également utiliser des expressions lambda quand vous écrivez [LINQ en C#](../../linq/index.md), comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="35a5d-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="35a5d-119">Lorsque la méthode <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> est appelée avec une syntaxe fondée sur une méthode dans la classe <xref:System.Linq.Enumerable?displayProperty=nameWithType> (par exemple, dans LINQ to Objects et LINQ to XML), le paramètre est un type délégué <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35a5d-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35a5d-120">Quand vous appelez la <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> méthode dans la <xref:System.Linq.Queryable?displayProperty=nameWithType> classe, par exemple dans LINQ to SQL, le type de paramètre est un type d’arborescence d’expression [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) .</span><span class="sxs-lookup"><span data-stu-id="35a5d-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="35a5d-121">Dans les deux cas, vous pouvez utiliser la même expression lambda pour spécifier la valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="35a5d-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="35a5d-122">Les deux appels `Select` semblent ainsi semblables alors qu’en fait le type des objets créés à partir des lambdas est différent.</span><span class="sxs-lookup"><span data-stu-id="35a5d-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="35a5d-123">Expressions lambdas</span><span class="sxs-lookup"><span data-stu-id="35a5d-123">Expression lambdas</span></span>

<span data-ttu-id="35a5d-124">Une expression lambda comportant une expression à droite de l’opérateur `=>` est appelée *expression lambda*.</span><span class="sxs-lookup"><span data-stu-id="35a5d-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="35a5d-125">Les expressions lambda d’expression sont largement utilisées dans la construction d' [arborescences d’expressions](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="35a5d-125">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="35a5d-126">Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :</span><span class="sxs-lookup"><span data-stu-id="35a5d-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="35a5d-127">Les parenthèses sont facultatives uniquement si le lambda comporte un paramètre d'entrée ; sinon, elles sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="35a5d-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="35a5d-128">Spécifiez des paramètres d'entrée de zéro avec des parenthèses vides :</span><span class="sxs-lookup"><span data-stu-id="35a5d-128">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="35a5d-129">Les paramètres d'entrée sont séparés par des virgules entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="35a5d-129">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="35a5d-130">Il est parfois impossible pour le compilateur de déduire les types d’entrée.</span><span class="sxs-lookup"><span data-stu-id="35a5d-130">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="35a5d-131">Vous pouvez spécifier les types explicitement comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="35a5d-131">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="35a5d-132">Les types de paramètres d’entrée doivent être tous explicites ou tous implicites ; sinon, une erreur de compilateur [CS0748](../../misc/cs0748.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="35a5d-132">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="35a5d-133">Le corps d’une expression lambda peut se composer d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="35a5d-133">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="35a5d-134">Cependant, si vous créez des arborescences d’expressions évaluées en dehors du contexte du common language runtime .NET, comme dans SQL Server, vous ne devez pas utiliser d’appels de méthode dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-134">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="35a5d-135">Les méthodes n'auront aucune signification en dehors du contexte du Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="35a5d-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="35a5d-136">Instructions lambda</span><span class="sxs-lookup"><span data-stu-id="35a5d-136">Statement lambdas</span></span>

<span data-ttu-id="35a5d-137">Une instruction lambda ressemble à une expression lambda, mais l'instruction ou les instructions sont mises entre accolades :</span><span class="sxs-lookup"><span data-stu-id="35a5d-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="35a5d-138">Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.</span><span class="sxs-lookup"><span data-stu-id="35a5d-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="35a5d-139">Les instructions lambda ne peuvent pas être utilisées pour créer des arborescences d'expression.</span><span class="sxs-lookup"><span data-stu-id="35a5d-139">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="35a5d-140">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="35a5d-140">Async lambdas</span></span>

<span data-ttu-id="35a5d-141">Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../../language-reference/keywords/async.md) et [await](../../language-reference/operators/await.md) .</span><span class="sxs-lookup"><span data-stu-id="35a5d-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="35a5d-142">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="35a5d-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="35a5d-143">Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone.</span><span class="sxs-lookup"><span data-stu-id="35a5d-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="35a5d-144">Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="35a5d-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="35a5d-145">Pour plus d’informations sur la création et l’utilisation des méthodes Async, consultez [programmation asynchrone avec Async et await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="35a5d-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="35a5d-146">Expressions lambda et tuples</span><span class="sxs-lookup"><span data-stu-id="35a5d-146">Lambda expressions and tuples</span></span>

<span data-ttu-id="35a5d-147">À compter de C# 7,0, le langage C# offre une prise en charge intégrée des [tuples](../../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="35a5d-147">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../language-reference/builtin-types/value-tuples.md).</span></span> <span data-ttu-id="35a5d-148">Vous pouvez fournir un tuple comme argument à une expression lambda, et votre expression lambda peut aussi retourner un tuple.</span><span class="sxs-lookup"><span data-stu-id="35a5d-148">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="35a5d-149">Dans certains cas, le compilateur C# utilise l’inférence de type pour déterminer les types des composants du tuple.</span><span class="sxs-lookup"><span data-stu-id="35a5d-149">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="35a5d-150">Vous définissez un tuple en plaçant entre des parenthèses une liste de ses composants avec des virgules comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="35a5d-150">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="35a5d-151">L’exemple suivant utilise un tuple à trois composants pour passer une séquence de nombres à une expression lambda, qui double chaque valeur et retourne un tuple à trois composants contenant le résultat des multiplications.</span><span class="sxs-lookup"><span data-stu-id="35a5d-151">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="35a5d-152">En règle générale, les champs d’un tuple sont nommés `Item1` , `Item2` , etc. Toutefois, vous pouvez définir un tuple avec des composants nommés, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="35a5d-152">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="35a5d-153">Pour plus d’informations sur les tuples C#, consultez [types de tuples](../../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="35a5d-153">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="35a5d-154">Lambdas avec les opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="35a5d-154">Lambdas with the standard query operators</span></span>

<span data-ttu-id="35a5d-155">LINQ to Objects, parmi d’autres implémentations, a un paramètre d’entrée dont le type fait partie de la famille <xref:System.Func%601> de délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="35a5d-155">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="35a5d-156">Ces délégués utilisent des paramètres de type pour définir le nombre et le type des paramètres d’entrée, ainsi que le type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="35a5d-156">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="35a5d-157">Les délégués`Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources.</span><span class="sxs-lookup"><span data-stu-id="35a5d-157">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="35a5d-158">Prenons par exemple le type délégué <xref:System.Func%602> :</span><span class="sxs-lookup"><span data-stu-id="35a5d-158">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="35a5d-159">Ce délégué peut être instancié comme une instance `Func<int, bool>`, où `int` est un paramètre d’entrée et `bool` la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="35a5d-159">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="35a5d-160">La valeur de retour est toujours spécifiée dans le dernier paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="35a5d-160">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="35a5d-161">Par exemple, `Func<int, string, bool>` définit un délégué avec deux paramètres d’entrée, `int` et `string`, et un type de retour `bool`.</span><span class="sxs-lookup"><span data-stu-id="35a5d-161">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="35a5d-162">Le délégué `Func` suivant, lorsqu’il est appelé, retourne une valeur booléenne indiquant si le paramètre d’entrée est égal à cinq :</span><span class="sxs-lookup"><span data-stu-id="35a5d-162">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="35a5d-163">Vous pouvez aussi fournir une expression lambda quand le type d’argument est <xref:System.Linq.Expressions.Expression%601>, par exemple, dans les opérateurs de requête standard définis dans le type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="35a5d-163">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="35a5d-164">Quand vous spécifiez un argument <xref:System.Linq.Expressions.Expression%601>, l’expression lambda est compilée en arborescence de l’expression.</span><span class="sxs-lookup"><span data-stu-id="35a5d-164">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="35a5d-165">L’exemple suivant utilise l’opérateur de requête standard <xref:System.Linq.Enumerable.Count%2A> :</span><span class="sxs-lookup"><span data-stu-id="35a5d-165">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="35a5d-166">Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="35a5d-166">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="35a5d-167">Cette expression lambda particulière compte les entiers (`n`) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.</span><span class="sxs-lookup"><span data-stu-id="35a5d-167">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="35a5d-168">L’exemple suivant produit une séquence qui contient tous les éléments du tableau `numbers` précédant le 9, car c’est le premier nombre de la séquence qui ne remplit pas la condition :</span><span class="sxs-lookup"><span data-stu-id="35a5d-168">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="35a5d-169">L’exemple suivant spécifie plusieurs paramètres d’entrée en les plaçant entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="35a5d-169">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="35a5d-170">La méthode retourne tous les éléments du tableau `numbers` jusqu’à ce qu’elle rencontre un nombre dont la valeur est inférieure à sa position ordinale dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="35a5d-170">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="35a5d-171">Inférence de type et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="35a5d-171">Type inference in lambda expressions</span></span>

<span data-ttu-id="35a5d-172">Il n’est généralement pas nécessaire, avec les expressions lambda, de spécifier un type pour les paramètres d’entrée, car le compilateur peut le déduire du corps de l’expression, des types de paramètres et d’autres facteurs, comme le décrit la spécification du langage C#.</span><span class="sxs-lookup"><span data-stu-id="35a5d-172">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="35a5d-173">Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source.</span><span class="sxs-lookup"><span data-stu-id="35a5d-173">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="35a5d-174">Si vous interrogez un `IEnumerable<Customer>`, le type de la variable d’entrée est inféré comme étant un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et à ses propriétés :</span><span class="sxs-lookup"><span data-stu-id="35a5d-174">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="35a5d-175">Voici les règles générales de l’inférence de type pour les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="35a5d-175">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="35a5d-176">Le lambda doit contenir le même nombre de paramètres que le type délégué.</span><span class="sxs-lookup"><span data-stu-id="35a5d-176">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="35a5d-177">Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="35a5d-177">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="35a5d-178">La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="35a5d-178">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="35a5d-179">Notez que les expressions lambda n’ont pas de type en elles-mêmes, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d’expression lambda ».</span><span class="sxs-lookup"><span data-stu-id="35a5d-179">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="35a5d-180">Toutefois, il est parfois commode de parler de manière informelle du « type » d’une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-180">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="35a5d-181">Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-181">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="35a5d-182">Capture des variables externes et de l’étendue variable dans les expressions lambda</span><span class="sxs-lookup"><span data-stu-id="35a5d-182">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="35a5d-183">Les expressions lambda peuvent faire référence à des *variables externes*.</span><span class="sxs-lookup"><span data-stu-id="35a5d-183">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="35a5d-184">Il s’agit de variables dans l’étendue de la méthode qui définit l’expression lambda, ou dans l’étendue du type qui contient l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-184">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="35a5d-185">Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="35a5d-185">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="35a5d-186">Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-186">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="35a5d-187">L'exemple suivant illustre ces règles :</span><span class="sxs-lookup"><span data-stu-id="35a5d-187">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="35a5d-188">Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="35a5d-188">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="35a5d-189">Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="35a5d-189">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="35a5d-190">Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="35a5d-190">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="35a5d-191">Une expression lambda ne peut pas capturer directement un paramètre [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md) dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="35a5d-191">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="35a5d-192">Une instruction [return](../../language-reference/keywords/return.md) dans une expression lambda ne provoque pas le retour de la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="35a5d-192">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="35a5d-193">Une expression lambda ne peut pas contenir d’instruction [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md) ou [continue](../../language-reference/keywords/continue.md) si la cible de cette instruction de saut se trouve en dehors du bloc de l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="35a5d-193">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="35a5d-194">Il est également incorrect d’avoir une instruction de saut en dehors du bloc de l’expression lambda si la cible se trouve à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="35a5d-194">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="35a5d-195">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="35a5d-195">C# language specification</span></span>

<span data-ttu-id="35a5d-196">Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="35a5d-196">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="35a5d-197">Chapitre proposé</span><span class="sxs-lookup"><span data-stu-id="35a5d-197">Featured book chapter</span></span>

<span data-ttu-id="35a5d-198">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="35a5d-198">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a5d-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35a5d-199">See also</span></span>

- [<span data-ttu-id="35a5d-200">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="35a5d-200">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35a5d-201">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="35a5d-201">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="35a5d-202">Arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="35a5d-202">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="35a5d-203">Fonctions locales et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="35a5d-203">Local functions vs. lambda expressions</span></span>](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="35a5d-204">Exemples Visual Studio 2008 C# (voir les fichiers d’exemples de requêtes LINQ et le programme XQuery)</span><span class="sxs-lookup"><span data-stu-id="35a5d-204">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="35a5d-205">Expressions lambda récursives</span><span class="sxs-lookup"><span data-stu-id="35a5d-205">Recursive lambda expressions</span></span>](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
