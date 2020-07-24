---
title: Fonctionnalités C# qui prennent en charge LINQ
description: En savoir plus sur les fonctionnalités C# à utiliser avec les requêtes LINQ et dans d’autres contextes. Ces constructions de langage ont été introduites dans C# 3,0.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f72b82180d794086dcea9f11a7a057dc26ab0b26
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105418"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="833b9-104">Fonctionnalités C# qui prennent en charge LINQ</span><span class="sxs-lookup"><span data-stu-id="833b9-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="833b9-105">La section suivante présente de nouvelles constructions de langage qui sont apparues avec C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="833b9-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="833b9-106">Bien que ces nouvelles fonctionnalités soient toutes utilisées dans un certain degré avec des requêtes LINQ, elles ne sont pas limitées à LINQ et peuvent être utilisées dans n’importe quel contexte où elles sont utiles.</span><span class="sxs-lookup"><span data-stu-id="833b9-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="833b9-107">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="833b9-107">Query Expressions</span></span>

<span data-ttu-id="833b9-108">Les expressions de requête utilisent une syntaxe déclarative similaire à SQL ou XQuery pour interroger les collections IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="833b9-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="833b9-109">Au moment de la compilation, la syntaxe de requête est convertie en appels de méthode à l’implémentation d’un fournisseur LINQ des méthodes d’extension d’opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="833b9-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="833b9-110">Les applications contrôlent les opérateurs de requête standard qui se trouvent dans la portée en spécifiant l’espace de noms approprié avec une directive `using`.</span><span class="sxs-lookup"><span data-stu-id="833b9-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="833b9-111">L’expression de requête suivante accepte un tableau de chaînes, regroupe les chaînes qui commencent par le même caractère, puis trie ces groupes de chaînes.</span><span class="sxs-lookup"><span data-stu-id="833b9-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="833b9-112">Pour plus d’informations, consultez [Expressions de requête LINQ](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="833b9-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="833b9-113">Variables implicitement typées (var)</span><span class="sxs-lookup"><span data-stu-id="833b9-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="833b9-114">Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez utiliser le modificateur [var](../../../language-reference/keywords/var.md) pour indiquer au compilateur qu’il doit déduire et assigner le type, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="833b9-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="833b9-115">Les variables déclarées comme `var` sont tout aussi fortement typées en tant que variables dont le type est spécifié explicitement.</span><span class="sxs-lookup"><span data-stu-id="833b9-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="833b9-116">`var` permet de créer des types anonymes, mais peut être utilisé uniquement pour les variables locales.</span><span class="sxs-lookup"><span data-stu-id="833b9-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="833b9-117">Les tableaux peuvent également être déclarés avec un typage implicite.</span><span class="sxs-lookup"><span data-stu-id="833b9-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="833b9-118">Pour plus d’informations, consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="833b9-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="833b9-119">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="833b9-119">Object and Collection Initializers</span></span>

<span data-ttu-id="833b9-120">Les initialiseurs d’objets et de collections permettent d’initialiser un objet sans appeler explicitement un constructeur pour cet objet.</span><span class="sxs-lookup"><span data-stu-id="833b9-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="833b9-121">Les initialiseurs sont généralement utilisés dans les expressions de requête pour projeter la source de données en un nouveau type de données.</span><span class="sxs-lookup"><span data-stu-id="833b9-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="833b9-122">En supposant une classe nommée `Customer` avec les propriétés publiques `Name` et `Phone`, l’initialiseur d’objet peut être utilisé, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="833b9-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="833b9-123">Si l’on reprend notre classe `Customer`, supposons qu’il existe une source de données appelée `IncomingOrders` et que, pour chaque commande caractérisée par un grand `OrderSize`, nous souhaitons créer un nouveau `Customer` basé sur cette commande.</span><span class="sxs-lookup"><span data-stu-id="833b9-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="833b9-124">Une requête LINQ peut être exécutée sur cette source de données et utiliser l’initialisation d’objets pour remplir une collection :</span><span class="sxs-lookup"><span data-stu-id="833b9-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="833b9-125">La source de données peut avoir plus de propriétés sous-jacentes que la classe `Customer`, par exemple, `OrderSize` ; cependant, avec l’initialisation d’objets, les données retournées par la requête sont moulées dans le type de données souhaité ; nous choisissons les données correspondant à notre classe.</span><span class="sxs-lookup"><span data-stu-id="833b9-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="833b9-126">Par conséquent, nous disposons désormais d’un `IEnumerable` contenant les nouveaux `Customer` que nous voulions.</span><span class="sxs-lookup"><span data-stu-id="833b9-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="833b9-127">La requête ci-dessus peut également s’écrire avec la syntaxe de méthode LINQ :</span><span class="sxs-lookup"><span data-stu-id="833b9-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="833b9-128">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="833b9-128">For more information, see:</span></span>

- [<span data-ttu-id="833b9-129">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="833b9-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="833b9-130">Syntaxe des expressions de requête pour les opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="833b9-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="833b9-131">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="833b9-131">Anonymous Types</span></span>

<span data-ttu-id="833b9-132">Un type anonyme est construit par le compilateur et le nom du type est uniquement disponible pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="833b9-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="833b9-133">Les types anonymes permettent de regrouper facilement des propriétés de manière temporaire dans un résultat de requête, sans avoir à définir un type nommé distinct.</span><span class="sxs-lookup"><span data-stu-id="833b9-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="833b9-134">Les types anonymes sont initialisés avec une nouvelle expression et un initialiseur d’objet, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="833b9-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="833b9-135">Pour plus d’informations, consultez [types anonymes](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="833b9-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="833b9-136">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="833b9-136">Extension Methods</span></span>

<span data-ttu-id="833b9-137">Une méthode d’extension est une méthode statique qui peut être associée à un type, de manière à être appelée comme une méthode d’instance de ce type.</span><span class="sxs-lookup"><span data-stu-id="833b9-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="833b9-138">Cette fonctionnalité permet d’ajouter de nouvelles méthodes aux types existants sans les modifier.</span><span class="sxs-lookup"><span data-stu-id="833b9-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="833b9-139">Les opérateurs de requête standard sont un ensemble de méthodes d’extension qui fournissent des fonctionnalités de requête LINQ pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="833b9-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="833b9-140">Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="833b9-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="833b9-141">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="833b9-141">Lambda Expressions</span></span>

<span data-ttu-id="833b9-142">Une expression lambda est une fonction inline qui utilise l’opérateur => pour séparer les paramètres d’entrée du corps de la fonction, et qui peut être convertie au moment de la compilation en un délégué ou une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="833b9-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="833b9-143">Dans la programmation LINQ, vous rencontrerez des expressions lambda lorsque vous effectuerez des appels de méthode directs aux opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="833b9-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="833b9-144">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="833b9-144">For more information, see:</span></span>

- [<span data-ttu-id="833b9-145">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="833b9-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="833b9-146">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="833b9-146">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="833b9-147">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="833b9-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="833b9-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="833b9-148">See also</span></span>

- [<span data-ttu-id="833b9-149">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="833b9-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
