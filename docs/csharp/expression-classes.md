---
title: Types de frameworks prenant en charge les arborescences d’expressions
description: En savoir plus sur les types de frameworks prenant en charge les arborescences d’expressions, la création d’arborescences d’expressions et les techniques d’utilisation des API d’arborescences d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 548f5ba6a2de00d9556621791515555b6f6a325c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180437"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="3dcd9-103">Types de frameworks prenant en charge les arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dcd9-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="3dcd9-104">Précédent – Explication des arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dcd9-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="3dcd9-105">Il existe une longue liste de classes dans le framework .NET Core qui fonctionnent avec des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="3dcd9-106">Vous pouvez voir la liste complète dans <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="3dcd9-107">Au lieu de parcourir la liste complète, essayons de comprendre comment les classes du framework ont été conçues.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="3dcd9-108">Dans la conception du langage, une expression est un corps de code qui évalue et retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="3dcd9-109">Les expressions peuvent être très simples : l’expression constante `1` retourne la valeur constante 1.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="3dcd9-110">Elles peuvent être plus compliquées : l’expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` retourne une racine pour une équation quadratique (dans le cas où l’équation a une solution).</span><span class="sxs-lookup"><span data-stu-id="3dcd9-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="3dcd9-111">Tout commence par System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="3dcd9-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="3dcd9-112">L’une des complexités liées à l’utilisation des arborescences d’expressions est que de nombreuses sortes d’expressions sont valides à de nombreux endroits dans les programmes.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="3dcd9-113">Prenez par exemple une expression d’assignation.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-113">Consider an assignment expression.</span></span> <span data-ttu-id="3dcd9-114">La partie droite d’une assignation peut être une valeur constante, une variable, une expression d’appel de méthode ou autre.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="3dcd9-115">Cette flexibilité linguistique signifie que vous pouvez rencontrer de nombreux types d’expressions différents à n’importe quel endroit dans les nœuds d’une arborescence quand vous parcourez une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="3dcd9-116">Ainsi, quand vous pouvez travailler avec le type d’expression de base, c’est le moyen le plus simple de procéder.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="3dcd9-117">Cependant, vous devez parfois en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="3dcd9-118">La classe Expression de base contient une propriété `NodeType` à cet effet.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="3dcd9-119">Elle retourne un `ExpressionType` qui est une énumération des types d’expressions possibles.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="3dcd9-120">Une fois que vous connaissez le type du nœud, vous pouvez le caster en ce type et effectuer des actions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="3dcd9-121">Vous pouvez rechercher certains types de nœuds, puis utiliser les propriétés spécifiques de ce genre d’expression.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="3dcd9-122">Par exemple, ce code imprime le nom d’une variable pour une expression d’accès à la variable.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="3dcd9-123">J’ai suivi la pratique qui consiste à vérifier le type de nœud, à caster en une expression d’accès à la variable, puis à vérifier les propriétés du type d’expression spécifique :</span><span class="sxs-lookup"><span data-stu-id="3dcd9-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="3dcd9-124">Création d’arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dcd9-124">Creating Expression Trees</span></span>

<span data-ttu-id="3dcd9-125">La classe `System.Linq.Expression` contient également de nombreuses méthodes statiques pour créer des expressions.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="3dcd9-126">Ces méthodes créent un nœud d’expression en utilisant les arguments fournis pour ses enfants.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="3dcd9-127">De cette façon, vous générez une expression à partir de ses nœuds terminaux.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="3dcd9-128">Par exemple, ce code génère une expression Add :</span><span class="sxs-lookup"><span data-stu-id="3dcd9-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="3dcd9-129">Vous pouvez constater d’après cet exemple simple que de nombreux types sont impliqués dans la création et l’utilisation des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="3dcd9-130">Cette complexité est nécessaire pour fournir les fonctionnalités du vocabulaire enrichi fourni par le langage C#.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="3dcd9-131">Navigation dans les API</span><span class="sxs-lookup"><span data-stu-id="3dcd9-131">Navigating the APIs</span></span>

<span data-ttu-id="3dcd9-132">Il existe des types de nœuds Expression qui mappent à presque tous les éléments de syntaxe du langage C#.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="3dcd9-133">Chaque type a des méthodes spécifiques pour ce type d’élément de langage.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="3dcd9-134">Cela fait beaucoup de choses à mémoriser en même temps.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="3dcd9-135">Plutôt que d’essayer de mémoriser tout, voici les techniques que je vous conseille d’appliquer quand vous travaillez avec des arborescences d’expressions :</span><span class="sxs-lookup"><span data-stu-id="3dcd9-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="3dcd9-136">Examinez les membres de l’énumération `ExpressionType` pour déterminer les éventuels nœuds à examiner.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="3dcd9-137">Cela aide vraiment quand vous souhaitez parcourir et comprendre une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="3dcd9-138">Examinez les membres statiques de la classe `Expression` pour générer une expression.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="3dcd9-139">Ces méthodes peuvent générer tout type d’expression à partir d’un ensemble de ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="3dcd9-140">Examinez la classe `ExpressionVisitor` pour générer une arborescence d’expressions modifiée.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="3dcd9-141">Vous trouverez davantage de choses à mesure que vous examinez chacune de ces trois zones.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="3dcd9-142">Vous trouverez invariablement ce dont vous avez besoin si vous commencez avec l’une de ces trois étapes.</span><span class="sxs-lookup"><span data-stu-id="3dcd9-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="3dcd9-143">Suivant – Exécution d’arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dcd9-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
