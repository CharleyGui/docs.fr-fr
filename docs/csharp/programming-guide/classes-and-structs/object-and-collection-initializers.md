---
title: Initialiseurs d’objet et de collection - Guide de programmation C#
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170193"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="f748e-102">Initialiseurs d’objet et de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f748e-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="f748e-103">C# vous permet d’instancier un objet ou une collection et d’effectuer des affectations de membres dans une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="f748e-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="f748e-104">Initialiseurs d’objet</span><span class="sxs-lookup"><span data-stu-id="f748e-104">Object initializers</span></span>

<span data-ttu-id="f748e-105">Les initialiseurs d'objet vous permettent d'affecter des valeurs aux champs ou propriétés accessibles d'un objet, au moment de sa création, sans devoir appeler un constructeur suivi de ses lignes d'instructions d'assignation.</span><span class="sxs-lookup"><span data-stu-id="f748e-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="f748e-106">La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre (et la syntaxe de parenthèses).</span><span class="sxs-lookup"><span data-stu-id="f748e-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="f748e-107">L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="f748e-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="f748e-108">Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`.</span><span class="sxs-lookup"><span data-stu-id="f748e-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="f748e-109">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f748e-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="f748e-110">La syntaxe des initialiseurs d’objet vous permet de créer une instance qui assigne l’objet nouvellement créé, avec ses propriétés, à la variable dans l’assignation.</span><span class="sxs-lookup"><span data-stu-id="f748e-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="f748e-111">À compter de C# 6, les initialiseurs d’objet peuvent, en plus d’affecter des champs et des propriétés, définir des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="f748e-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="f748e-112">Prenez l’exemple de cette classe `Matrix` de base :</span><span class="sxs-lookup"><span data-stu-id="f748e-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="f748e-113">Vous pouvez initialiser la matrice identity avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f748e-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="f748e-114">Tout indexeur accessible qui contient un setter accessible peut être utilisé comme l’une des expressions d’un initialiseur d’objet, indépendamment du nombre ou des types d’arguments.</span><span class="sxs-lookup"><span data-stu-id="f748e-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="f748e-115">Les arguments d’index forment le côté gauche de l’affectation, et la valeur le côté droit de l’expression.</span><span class="sxs-lookup"><span data-stu-id="f748e-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="f748e-116">Par exemple, les éléments suivants sont tous valides si `IndexersExample` a les indexeurs appropriés :</span><span class="sxs-lookup"><span data-stu-id="f748e-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="f748e-117">Pour le code précédent à compiler, le type `IndexersExample` doit avoir les membres suivants :</span><span class="sxs-lookup"><span data-stu-id="f748e-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="f748e-118">Initialiseurs d'objet avec des types anonymes</span><span class="sxs-lookup"><span data-stu-id="f748e-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="f748e-119">Bien que les initialisateurs d’objets puissent être utilisés dans n’importe quel contexte, ils sont particulièrement utiles dans les expressions de requête linQ.</span><span class="sxs-lookup"><span data-stu-id="f748e-119">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="f748e-120">Les expressions de requête utilisent souvent des [types anonymes](./anonymous-types.md), qui peuvent uniquement être initialisés à l’aide d’un initialiseur d’objet, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="f748e-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="f748e-121">Les types `select` anonymes permettent à la clause d’une expression de requête LINQ de transformer des objets de la séquence originale en objets dont la valeur et la forme peuvent différer de l’original.</span><span class="sxs-lookup"><span data-stu-id="f748e-121">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="f748e-122">Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="f748e-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="f748e-123">Dans l'exemple suivant, supposons qu'un objet de produit (`p`) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.</span><span class="sxs-lookup"><span data-stu-id="f748e-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="f748e-124">Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="f748e-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="f748e-125">Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="f748e-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="f748e-126">Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.</span><span class="sxs-lookup"><span data-stu-id="f748e-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="f748e-127">Initialiseurs de collection</span><span class="sxs-lookup"><span data-stu-id="f748e-127">Collection initializers</span></span>

<span data-ttu-id="f748e-128">Les initialiseurs de collection vous permettent de spécifier un ou plusieurs initialiseurs d’élément quand vous initialisez un type de collection qui implémente <xref:System.Collections.IEnumerable> et qui utilise `Add` comme méthode d’instance ou méthode d’extension avec la signature appropriée.</span><span class="sxs-lookup"><span data-stu-id="f748e-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="f748e-129">Les initialiseurs d’élément peuvent être une valeur simple, une expression ou un initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="f748e-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="f748e-130">En utilisant un initialiseur de collection, il n’est pas nécessaire de spécifier plusieurs appels ; le compilateur les ajoute automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f748e-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="f748e-131">L’exemple suivant montre deux initialiseurs de collection simples :</span><span class="sxs-lookup"><span data-stu-id="f748e-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="f748e-132">L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="f748e-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="f748e-133">Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="f748e-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="f748e-134">Vous pouvez spécifier [Null](../../language-reference/keywords/null.md) comme élément dans un initialiseur de collection si la méthode `Add` de la collection l’autorise.</span><span class="sxs-lookup"><span data-stu-id="f748e-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="f748e-135">Vous pouvez spécifier des éléments indexés si la collection prend en charge l’indexation en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="f748e-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="f748e-136">L’exemple précédent génère du code qui appelle <xref:System.Collections.Generic.Dictionary%602.Item(%600)> pour définir les valeurs.</span><span class="sxs-lookup"><span data-stu-id="f748e-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="f748e-137">Avant le numéro 6, vous pouvez initialiser les dictionnaires et autres contenants associatifs à l’aide de la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="f748e-137">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="f748e-138">Notez que la syntaxe de l’indexeur, avec des parenthèses et une affectation, est remplacée par un objet avec plusieurs valeurs :</span><span class="sxs-lookup"><span data-stu-id="f748e-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="f748e-139">Cet exemple d’initialiseur appelle <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> pour ajouter les trois éléments dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="f748e-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="f748e-140">Ces deux manières d’initialiser les collections associatives ont un comportement légèrement différent en raison des appels de méthode générés par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="f748e-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="f748e-141">Les deux variantes fonctionnent avec la classe `Dictionary`.</span><span class="sxs-lookup"><span data-stu-id="f748e-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="f748e-142">D’autres types peuvent uniquement prendre en charge l’une ou l’autre en fonction de leur API publique.</span><span class="sxs-lookup"><span data-stu-id="f748e-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="f748e-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="f748e-143">Examples</span></span>

<span data-ttu-id="f748e-144">L’exemple suivant combine les concepts d’initialiseurs d’objet et de collection.</span><span class="sxs-lookup"><span data-stu-id="f748e-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="f748e-145">L’exemple suivant montre un objet qui implémente <xref:System.Collections.IEnumerable> et qui contient une méthode `Add` avec plusieurs paramètres. Il utilise un initialiseur de collection avec plusieurs éléments dans la liste correspondant à la signature de la méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="f748e-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="f748e-146">Les méthodes `Add` peuvent utiliser le mot clé `params` pour sélectionner un nombre variable d’arguments, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f748e-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="f748e-147">Cet exemple montre également l’implémentation personnalisée d’un indexeur pour initialiser une collection à l’aide d’index.</span><span class="sxs-lookup"><span data-stu-id="f748e-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="f748e-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f748e-148">See also</span></span>

- [<span data-ttu-id="f748e-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f748e-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f748e-150">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="f748e-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="f748e-151">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="f748e-151">Anonymous Types</span></span>](anonymous-types.md)
