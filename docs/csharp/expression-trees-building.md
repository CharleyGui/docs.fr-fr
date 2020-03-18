---
title: Génération d’arborescences d’expressions
description: En savoir plus sur les techniques de génération d’arborescences d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146045"
---
# <a name="building-expression-trees"></a><span data-ttu-id="0366f-103">Génération d’arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="0366f-103">Building Expression Trees</span></span>

[<span data-ttu-id="0366f-104">Précédent -- Interprétation d’expressions</span><span class="sxs-lookup"><span data-stu-id="0366f-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="0366f-105">Toutes les arborescences d’expressions que vous avez vues jusqu’ici ont été créées par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="0366f-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="0366f-106">Tout ce que vous aviez à faire était de créer une expression lambda qui était assignée à une variable de type `Expression<Func<T>>` ou d’un type similaire.</span><span class="sxs-lookup"><span data-stu-id="0366f-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="0366f-107">Ce n’est pas la seule façon de créer une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="0366f-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="0366f-108">Dans de nombreux scénarios, vous constaterez peut-être que vous devez générer une expression en mémoire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0366f-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="0366f-109">La génération d’arborescences d’expressions est compliquée par le fait qu’elles sont immuables.</span><span class="sxs-lookup"><span data-stu-id="0366f-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="0366f-110">Cela signifie que vous devez générer l’arborescence à partir des feuilles jusqu’à la racine.</span><span class="sxs-lookup"><span data-stu-id="0366f-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="0366f-111">Les API que vous utiliserez pour générer des arborescences d’expressions reflètent cet état de fait : les méthodes que vous utiliserez pour générer un nœud prennent tous ses enfants en tant qu’arguments.</span><span class="sxs-lookup"><span data-stu-id="0366f-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="0366f-112">Examinons quelques exemples illustrant les techniques à appliquer.</span><span class="sxs-lookup"><span data-stu-id="0366f-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="0366f-113">Création de nœuds</span><span class="sxs-lookup"><span data-stu-id="0366f-113">Creating Nodes</span></span>

<span data-ttu-id="0366f-114">Commençons par quelque chose de relativement simple.</span><span class="sxs-lookup"><span data-stu-id="0366f-114">Let's start relatively simply again.</span></span> <span data-ttu-id="0366f-115">Nous allons utiliser l’expression d’addition avec laquelle j’ai travaillé tout au long de ces sections :</span><span class="sxs-lookup"><span data-stu-id="0366f-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="0366f-116">Pour construire cette arborescence d’expressions, nous devons construire les nœuds terminaux.</span><span class="sxs-lookup"><span data-stu-id="0366f-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="0366f-117">Les nœuds terminaux étant des constantes, nous pouvons utiliser la méthode `Expression.Constant` pour créer les nœuds :</span><span class="sxs-lookup"><span data-stu-id="0366f-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="0366f-118">Ensuite, nous allons générer l’expression d’addition :</span><span class="sxs-lookup"><span data-stu-id="0366f-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="0366f-119">Après cela, nous pouvons créer l’expression lambda :</span><span class="sxs-lookup"><span data-stu-id="0366f-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="0366f-120">Cette expression lambda est très simple, car elle ne contient aucun argument.</span><span class="sxs-lookup"><span data-stu-id="0366f-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="0366f-121">Plus loin dans cette section, nous verrons comment mapper des arguments à des paramètres, et comment générer des expressions plus complexes.</span><span class="sxs-lookup"><span data-stu-id="0366f-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="0366f-122">Pour les expressions qui sont aussi simples que celle-ci, nous pouvons combiner tous les appels en une seule instruction :</span><span class="sxs-lookup"><span data-stu-id="0366f-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="0366f-123">Génération d’une arborescence</span><span class="sxs-lookup"><span data-stu-id="0366f-123">Building a Tree</span></span>

<span data-ttu-id="0366f-124">Voilà les principes fondamentaux de génération d’une arborescence d’expressions en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0366f-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="0366f-125">Les arborescences plus complexes signifient généralement qu’il y a davantage de types de nœuds et davantage de nœuds dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="0366f-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="0366f-126">Examinons un autre exemple et voyons deux autres types de nœuds que vous générerez souvent lors de la création d’arborescences d’expressions : les nœuds d’argument et les nœuds d’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="0366f-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="0366f-127">Commençons par générer une arborescence d’expressions pour créer cette expression :</span><span class="sxs-lookup"><span data-stu-id="0366f-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="0366f-128">Nous allons commencer par créer des expressions de paramètre pour `x` et `y` :</span><span class="sxs-lookup"><span data-stu-id="0366f-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="0366f-129">La création des expressions de multiplication et d’addition suit le modèle que nous avons déjà vu :</span><span class="sxs-lookup"><span data-stu-id="0366f-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="0366f-130">Ensuite, nous devons créer une expression d’appel de méthode pour l’appel à `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="0366f-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="0366f-131">Pour finir, nous plaçons l’appel de méthode dans une expression lambda et nous veillons à définir les arguments de l’expression lambda :</span><span class="sxs-lookup"><span data-stu-id="0366f-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="0366f-132">Dans cet exemple plus complexe, vous pouvez observer quelques techniques supplémentaires dont vous aurez souvent besoin pour créer des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="0366f-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="0366f-133">Tout d’abord, vous devez créer les objets qui représentent des variables locales ou des paramètres avant de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="0366f-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="0366f-134">Une fois que vous avez créé ces objets, vous pouvez les utiliser dans votre arborescence d’expressions partout où vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="0366f-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="0366f-135">Ensuite, vous devez utiliser un sous-ensemble des API de réflexion pour créer un objet `MethodInfo` afin de pouvoir créer une arborescence d’expressions pour accéder à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="0366f-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="0366f-136">Vous devez vous limiter au sous-ensemble des API de réflexion disponibles sur la plateforme .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0366f-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="0366f-137">Là encore, ces techniques s’étendront à d’autres arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="0366f-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="0366f-138">Code de génération en profondeur</span><span class="sxs-lookup"><span data-stu-id="0366f-138">Building Code In Depth</span></span>

<span data-ttu-id="0366f-139">Vous n’êtes pas limité dans ce que vous pouvez générer à l’aide de ces API.</span><span class="sxs-lookup"><span data-stu-id="0366f-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="0366f-140">Toutefois, plus l’arborescence d’expressions que vous souhaitez générer est compliquée, plus le code est difficile à gérer et à lire.</span><span class="sxs-lookup"><span data-stu-id="0366f-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="0366f-141">Nous allons générer une arborescence d’expressions qui est l’équivalent de ce code :</span><span class="sxs-lookup"><span data-stu-id="0366f-141">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="0366f-142">Vous remarquerez ci-dessus que je n’ai pas généré l’arborescence d’expressions, mais simplement le délégué.</span><span class="sxs-lookup"><span data-stu-id="0366f-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="0366f-143">À l’aide de la classe `Expression`, vous ne pouvez pas créer de lambda-instructions.</span><span class="sxs-lookup"><span data-stu-id="0366f-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="0366f-144">Voici le code nécessaire pour générer la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0366f-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="0366f-145">Il est compliqué par le fait qu’il n’existe pas d’API pour générer une boucle `while`. Au lieu de cela, vous devez générer une boucle qui contient un test conditionnel, et une cible d’étiquette pour quitter la boucle.</span><span class="sxs-lookup"><span data-stu-id="0366f-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="0366f-146">Le code de génération de l’arborescence d’expressions pour la fonction factorielle est un peu plus long, plus compliqué et truffé d’étiquettes, d’instructions break et d’autres éléments que nous souhaitons éviter lors de nos tâches quotidiennes de codage.</span><span class="sxs-lookup"><span data-stu-id="0366f-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="0366f-147">Dans cette section, j’ai également mis à jour le code de visiteur pour visiter tous les nœuds de cette arborescence d’expressions et écrire des informations sur les nœuds créés dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="0366f-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="0366f-148">Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) à partir du dépôt GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="0366f-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="0366f-149">Essayez par vous-même en créant et en exécutant les exemples.</span><span class="sxs-lookup"><span data-stu-id="0366f-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="0366f-150">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0366f-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="0366f-151">Examen des API</span><span class="sxs-lookup"><span data-stu-id="0366f-151">Examining the APIs</span></span>

<span data-ttu-id="0366f-152">Les API d’arborescence d’expressions comptent parmi les plus difficiles à parcourir dans .NET Core, mais ce n’est pas grave.</span><span class="sxs-lookup"><span data-stu-id="0366f-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="0366f-153">Leur objectif est plutôt complexe : écrire du code qui génère du code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0366f-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="0366f-154">Elles sont nécessairement compliquées afin de fournir un équilibre entre la prise en charge de toutes les structures de contrôle disponibles en langage C# et la taille de la surface d’exposition des API (qui doit être la plus petite possible).</span><span class="sxs-lookup"><span data-stu-id="0366f-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="0366f-155">Cet équilibre signifie que de nombreuses structures de contrôle sont représentées non pas par leurs constructions C#, mais par des constructions qui représentent la logique sous-jacente générée par le compilateur à partir de ces constructions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="0366f-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="0366f-156">Il existe aussi actuellement des expressions C# qui ne peuvent pas être créées directement à l’aide de méthodes de classe `Expression`.</span><span class="sxs-lookup"><span data-stu-id="0366f-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="0366f-157">En général, il s’agit des opérateurs et expressions les plus récents ajoutés dans C# 5 et C# 6.</span><span class="sxs-lookup"><span data-stu-id="0366f-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="0366f-158">(Par exemple, les expressions `async` ne peuvent pas être générées et le nouvel opérateur `?.` ne peut pas être créé directement.)</span><span class="sxs-lookup"><span data-stu-id="0366f-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="0366f-159">Suivant -- Traduction d’expressions</span><span class="sxs-lookup"><span data-stu-id="0366f-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
