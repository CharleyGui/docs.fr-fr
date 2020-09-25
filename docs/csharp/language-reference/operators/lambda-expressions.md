---
title: Expressions lambda-référence C#
description: En savoir plus sur les expressions lambda. Il existe des lambdas d’expression qui ont une expression comme corps, ou des lambdas d’instruction qui ont un bloc d’instruction comme corps.
ms.date: 09/25/2020
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: a3a753ccea45193c57f31453d7318c14f4898864
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247707"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="6dc1c-104">Expressions lambda (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6dc1c-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="6dc1c-105">Une *expression lambda* est une expression de l’une des deux formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="6dc1c-106">[Expression lambda](#expression-lambdas) qui a une expression comme corps :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="6dc1c-107">[Instruction lambda](#statement-lambdas) qui a un bloc d’instructions comme corps :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="6dc1c-108">Utilisez l’[opérateur de déclaration lambda`=>`](lambda-operator.md) pour séparer la liste des paramètres de l’expression lambda de son corps.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-108">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="6dc1c-109">Pour créer une expression lambda, vous spécifiez des paramètres d’entrée (le cas échéant) à gauche de l’opérateur lambda et une expression ou un bloc d’instructions de l’autre côté.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="6dc1c-110">Toute expression lambda peut être convertie en type [délégué](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-110">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="6dc1c-111">Le type délégué vers lequel une expression lambda peut être convertie est défini par les types de ses paramètres et de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="6dc1c-112">Si une expression lambda ne retourne pas de valeur, elle peut être convertie en l’un des types délégués `Action` ; sinon, elle peut être convertie en l’un des types délégués `Func`.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="6dc1c-113">Par exemple, une expression lambda qui a deux paramètres et qui ne retourne aucune valeur peut être convertie en un délégué <xref:System.Action%602>.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="6dc1c-114">Une expression lambda qui a un paramètre et qui retourne une valeur peut être convertie en un délégué <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="6dc1c-115">Dans l’exemple suivant, l’expression lambda `x => x * x` , qui spécifie un paramètre nommé `x` et retourne la valeur du `x` carré, est assignée à une variable d’un type délégué :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="6dc1c-116">Les expressions lambda d’expression peuvent également être converties en types d' [arborescences d’expression](../../programming-guide/concepts/expression-trees/index.md) , comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-116">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="6dc1c-117">Vous pouvez utiliser des expressions lambda dans tout code qui requiert des instances de types délégués ou d’arborescences d’expressions, par exemple en tant qu’argument de la méthode <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> pour passer le code qui doit être exécuté en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="6dc1c-118">Vous pouvez également utiliser des expressions lambda quand vous écrivez [LINQ en C#](../../linq/index.md), comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="6dc1c-119">Lorsque la méthode <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> est appelée avec une syntaxe fondée sur une méthode dans la classe <xref:System.Linq.Enumerable?displayProperty=nameWithType> (par exemple, dans LINQ to Objects et LINQ to XML), le paramètre est un type délégué <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6dc1c-120">Quand vous appelez la <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> méthode dans la <xref:System.Linq.Queryable?displayProperty=nameWithType> classe, par exemple dans LINQ to SQL, le type de paramètre est un type d’arborescence d’expression [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) .</span><span class="sxs-lookup"><span data-stu-id="6dc1c-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="6dc1c-121">Dans les deux cas, vous pouvez utiliser la même expression lambda pour spécifier la valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="6dc1c-122">Les deux appels `Select` semblent ainsi semblables alors qu’en fait le type des objets créés à partir des lambdas est différent.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="6dc1c-123">Expressions lambdas</span><span class="sxs-lookup"><span data-stu-id="6dc1c-123">Expression lambdas</span></span>

<span data-ttu-id="6dc1c-124">Une expression lambda comportant une expression à droite de l’opérateur `=>` est appelée *expression lambda*.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="6dc1c-125">Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-125">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="6dc1c-126">Le corps d’une expression lambda peut se composer d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-126">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="6dc1c-127">Toutefois, si vous créez des [arborescences d’expressions](../../programming-guide/concepts/expression-trees/index.md) qui sont évaluées en dehors du contexte de l’Common Language Runtime .net, par exemple dans SQL Server, vous ne devez pas utiliser les appels de méthode dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-127">However, if you are creating [expression trees](../../programming-guide/concepts/expression-trees/index.md) that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="6dc1c-128">Les méthodes n'auront aucune signification en dehors du contexte du Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-128">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="6dc1c-129">Instructions lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-129">Statement lambdas</span></span>

<span data-ttu-id="6dc1c-130">Une instruction lambda ressemble à une expression lambda, sauf que ses instructions sont placées entre accolades :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-130">A statement lambda resembles an expression lambda except that its statements are enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="6dc1c-131">Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-131">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatementLambda":::

<span data-ttu-id="6dc1c-132">Vous ne pouvez pas utiliser des lambdas d’instruction pour créer des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-132">You cannot use statement lambdas to create expression trees.</span></span>

## <a name="input-parameters-of-a-lambda-expression"></a><span data-ttu-id="6dc1c-133">Paramètres d’entrée d’une expression lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-133">Input parameters of a lambda expression</span></span>

<span data-ttu-id="6dc1c-134">Placez les paramètres d’entrée d’une expression lambda entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-134">You enclose input parameters of a lambda expression in parentheses.</span></span> <span data-ttu-id="6dc1c-135">Spécifiez des paramètres d'entrée de zéro avec des parenthèses vides :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-135">Specify zero input parameters with empty parentheses:</span></span>  

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetZeroParameters":::

<span data-ttu-id="6dc1c-136">Si une expression lambda a un seul paramètre d’entrée, les parenthèses sont facultatives :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-136">If a lambda expression has only one input parameter, parentheses are optional:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetOneParameter":::

<span data-ttu-id="6dc1c-137">Deux ou plusieurs paramètres d’entrée sont séparés par des virgules :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-137">Two or more input parameters are separated by commas:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetTwoParameters":::

<span data-ttu-id="6dc1c-138">Parfois, le compilateur ne peut pas déduire les types de paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-138">Sometimes the compiler can't infer the types of input parameters.</span></span> <span data-ttu-id="6dc1c-139">Vous pouvez spécifier les types explicitement comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-139">You can specify the types explicitly as shown in the following example:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetExplicitlyTypedParameters":::

<span data-ttu-id="6dc1c-140">Les types de paramètres d’entrée doivent être tous explicites ou tous implicites ; sinon, une erreur de compilateur [CS0748](../../misc/cs0748.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-140">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="6dc1c-141">À compter de C# 9,0, vous pouvez utiliser des éléments [ignorés](../../discards.md) pour spécifier au moins deux paramètres d’entrée d’une expression lambda qui ne sont pas utilisés dans l’expression :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-141">Beginning with C# 9.0, you can use [discards](../../discards.md) to specify two or more input parameters of a lambda expression that aren't used in the expression:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetDiscards":::

<span data-ttu-id="6dc1c-142">Les paramètres d’abandon lambda peuvent être utiles lorsque vous utilisez une expression lambda pour [fournir un gestionnaire d’événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-142">Lambda discard parameters may be useful when you use a lambda expression to [provide an event handler](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6dc1c-143">À des fins de compatibilité descendante, si un seul paramètre d’entrée est nommé `_` , alors, dans une expression lambda, `_` est traité comme le nom de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-143">For backwards compatibility, if only a single input parameter is named `_`, then, within a lambda expression, `_` is treated as the name of that parameter.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="6dc1c-144">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="6dc1c-144">Async lambdas</span></span>

<span data-ttu-id="6dc1c-145">Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../keywords/async.md) et [await](await.md) .</span><span class="sxs-lookup"><span data-stu-id="6dc1c-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="6dc1c-146">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="6dc1c-147">Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="6dc1c-148">Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="6dc1c-149">Pour plus d’informations sur la création et l’utilisation des méthodes Async, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="6dc1c-150">Expressions lambda et tuples</span><span class="sxs-lookup"><span data-stu-id="6dc1c-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="6dc1c-151">À compter de C# 7,0, le langage C# offre une prise en charge intégrée des [tuples](../builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="6dc1c-152">Vous pouvez fournir un tuple comme argument à une expression lambda, et votre expression lambda peut aussi retourner un tuple.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="6dc1c-153">Dans certains cas, le compilateur C# utilise l’inférence de type pour déterminer les types des composants du tuple.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="6dc1c-154">Vous définissez un tuple en plaçant entre des parenthèses une liste de ses composants avec des virgules comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="6dc1c-155">L’exemple suivant utilise un tuple à trois composants pour passer une séquence de nombres à une expression lambda, qui double chaque valeur et retourne un tuple à trois composants contenant le résultat des multiplications.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="6dc1c-156">En règle générale, les champs d’un tuple sont nommés `Item1` , `Item2` , etc. Toutefois, vous pouvez définir un tuple avec des composants nommés, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="6dc1c-157">Pour plus d’informations sur les tuples C#, consultez [types de tuples](../../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-157">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="6dc1c-158">Lambdas avec les opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="6dc1c-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="6dc1c-159">LINQ to Objects, parmi d’autres implémentations, a un paramètre d’entrée dont le type fait partie de la famille <xref:System.Func%601> de délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="6dc1c-160">Ces délégués utilisent des paramètres de type pour définir le nombre et le type des paramètres d’entrée, ainsi que le type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="6dc1c-161">Les délégués`Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="6dc1c-162">Prenons par exemple le type délégué <xref:System.Func%602> :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="6dc1c-163">Ce délégué peut être instancié comme une instance `Func<int, bool>`, où `int` est un paramètre d’entrée et `bool` la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="6dc1c-164">La valeur de retour est toujours spécifiée dans le dernier paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="6dc1c-165">Par exemple, `Func<int, string, bool>` définit un délégué avec deux paramètres d’entrée, `int` et `string`, et un type de retour `bool`.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="6dc1c-166">Le délégué `Func` suivant, lorsqu’il est appelé, retourne une valeur booléenne indiquant si le paramètre d’entrée est égal à cinq :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="6dc1c-167">Vous pouvez aussi fournir une expression lambda quand le type d’argument est <xref:System.Linq.Expressions.Expression%601>, par exemple, dans les opérateurs de requête standard définis dans le type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="6dc1c-168">Quand vous spécifiez un argument <xref:System.Linq.Expressions.Expression%601>, l’expression lambda est compilée en arborescence de l’expression.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="6dc1c-169">L’exemple suivant utilise l’opérateur de requête standard <xref:System.Linq.Enumerable.Count%2A> :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="6dc1c-170">Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="6dc1c-171">Cette expression lambda particulière compte les entiers (`n`) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="6dc1c-172">L’exemple suivant produit une séquence qui contient tous les éléments du tableau `numbers` précédant le 9, car c’est le premier nombre de la séquence qui ne remplit pas la condition :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="6dc1c-173">L’exemple suivant spécifie plusieurs paramètres d’entrée en les plaçant entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="6dc1c-174">La méthode retourne tous les éléments du tableau `numbers` jusqu’à ce qu’elle rencontre un nombre dont la valeur est inférieure à sa position ordinale dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="6dc1c-175">Inférence de type et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="6dc1c-176">Il n’est généralement pas nécessaire, avec les expressions lambda, de spécifier un type pour les paramètres d’entrée, car le compilateur peut le déduire du corps de l’expression, des types de paramètres et d’autres facteurs, comme le décrit la spécification du langage C#.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="6dc1c-177">Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="6dc1c-178">Si vous interrogez un `IEnumerable<Customer>`, le type de la variable d’entrée est inféré comme étant un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et à ses propriétés :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="6dc1c-179">Voici les règles générales de l’inférence de type pour les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="6dc1c-180">Le lambda doit contenir le même nombre de paramètres que le type délégué.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="6dc1c-181">Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="6dc1c-182">La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="6dc1c-183">Notez que les expressions lambda n’ont pas de type en elles-mêmes, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d’expression lambda ».</span><span class="sxs-lookup"><span data-stu-id="6dc1c-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="6dc1c-184">Toutefois, il est parfois commode de parler de manière informelle du « type » d’une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="6dc1c-185">Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="6dc1c-186">Capture des variables externes et de l’étendue variable dans les expressions lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-186">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="6dc1c-187">Les expressions lambda peuvent faire référence à des *variables externes*.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-187">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="6dc1c-188">Il s’agit de variables dans l’étendue de la méthode qui définit l’expression lambda, ou dans l’étendue du type qui contient l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-188">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="6dc1c-189">Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-189">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="6dc1c-190">Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-190">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="6dc1c-191">L'exemple suivant illustre ces règles :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-191">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="6dc1c-192">Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-192">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="6dc1c-193">Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-193">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="6dc1c-194">Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-194">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="6dc1c-195">Une expression lambda ne peut pas capturer directement un paramètre [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md) ou [out](../keywords/out-parameter-modifier.md) dans la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-195">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="6dc1c-196">Une instruction [return](../keywords/return.md) dans une expression lambda ne provoque pas le retour de la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-196">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="6dc1c-197">Une expression lambda ne peut pas contenir d’instruction [goto](../keywords/goto.md), [break](../keywords/break.md) ou [continue](../keywords/continue.md) si la cible de cette instruction de saut se trouve en dehors du bloc de l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-197">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="6dc1c-198">Il est également incorrect d’avoir une instruction de saut en dehors du bloc de l’expression lambda si la cible se trouve à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-198">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

<span data-ttu-id="6dc1c-199">À compter de C# 9,0, vous pouvez appliquer le `static` modificateur à une expression lambda pour empêcher la capture non intentionnelle de variables locales ou l’état de l’instance par le lambda :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-199">Beginning with C# 9.0, you can apply the `static` modifier to a lambda expression to prevent unintentional capture of local variables or instance state by the lambda:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatic":::

<span data-ttu-id="6dc1c-200">Une expression lambda statique ne peut pas capturer les variables locales ou l’état de l’instance à partir des étendues englobantes, mais peut référencer des membres statiques et des définitions de constantes.</span><span class="sxs-lookup"><span data-stu-id="6dc1c-200">A static lambda can't capture local variables or instance state from enclosing scopes, but may reference static members and constant definitions.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6dc1c-201">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6dc1c-201">C# language specification</span></span>

<span data-ttu-id="6dc1c-202">Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1c-202">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6dc1c-203">Pour plus d’informations sur les fonctionnalités ajoutées dans C# 9,0, consultez les notes de proposition de fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc1c-203">For more information about features added in C# 9.0, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="6dc1c-204">Paramètres d’abandon lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-204">Lambda discard parameters</span></span>](~/_csharplang/proposals/csharp-9.0/lambda-discard-parameters.md)
- [<span data-ttu-id="6dc1c-205">Fonctions anonymes statiques</span><span class="sxs-lookup"><span data-stu-id="6dc1c-205">Static anonymous functions</span></span>](~/_csharplang/proposals/csharp-9.0/static-anonymous-functions.md)

## <a name="see-also"></a><span data-ttu-id="6dc1c-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dc1c-206">See also</span></span>

- [<span data-ttu-id="6dc1c-207">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="6dc1c-207">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6dc1c-208">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="6dc1c-208">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="6dc1c-209">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6dc1c-209">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="6dc1c-210">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="6dc1c-210">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="6dc1c-211">Fonctions locales et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="6dc1c-211">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="6dc1c-212">Exemples Visual Studio 2008 C# (voir les fichiers d’exemples de requêtes LINQ et le programme XQuery)</span><span class="sxs-lookup"><span data-stu-id="6dc1c-212">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
