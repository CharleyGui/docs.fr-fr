---
title: Membres expression-bodied - Guide de programmation C#
description: En savoir plus sur les membres expression-extracorporels. Consultez des exemples de code qui utilisent la définition de corps d’expression pour les propriétés, les constructeurs, les finaliseurs et bien plus encore.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381656"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="abfc8-104">Membres expression-bodied (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="abfc8-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="abfc8-105">Les définitions de corps d’expression vous permettent de fournir l’implémentation d’un membre sous une forme lisible et très concise.</span><span class="sxs-lookup"><span data-stu-id="abfc8-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="abfc8-106">Vous pouvez utiliser une définition de corps d’expression chaque fois que la logique d’un membre pris en charge, comme une méthode ou une propriété, se compose d’une seule expression.</span><span class="sxs-lookup"><span data-stu-id="abfc8-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="abfc8-107">La syntaxe générale d’une définition de corps d’expression est la suivante :</span><span class="sxs-lookup"><span data-stu-id="abfc8-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="abfc8-108">où *expression* est une expression valide.</span><span class="sxs-lookup"><span data-stu-id="abfc8-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="abfc8-109">La prise en charge des définitions de corps d’expression a été introduite pour les méthodes et les propriétés en lecture seule dans C# 6 et a été étendue dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="abfc8-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="abfc8-110">Vous pouvez utiliser des définitions de corps d’expression avec les membres de type listés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="abfc8-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="abfc8-111">Membre</span><span class="sxs-lookup"><span data-stu-id="abfc8-111">Member</span></span>  |<span data-ttu-id="abfc8-112">Prise en charge à compter de</span><span class="sxs-lookup"><span data-stu-id="abfc8-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="abfc8-113">Méthode</span><span class="sxs-lookup"><span data-stu-id="abfc8-113">Method</span></span>](#methods)  |<span data-ttu-id="abfc8-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="abfc8-114">C# 6</span></span> |
|[<span data-ttu-id="abfc8-115">Propriété en lecture seule</span><span class="sxs-lookup"><span data-stu-id="abfc8-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="abfc8-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="abfc8-116">C# 6</span></span>  |
|[<span data-ttu-id="abfc8-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="abfc8-117">Property</span></span>](#properties)  |<span data-ttu-id="abfc8-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="abfc8-118">C# 7.0</span></span> |
|[<span data-ttu-id="abfc8-119">Constructeur</span><span class="sxs-lookup"><span data-stu-id="abfc8-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="abfc8-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="abfc8-120">C# 7.0</span></span> |
|[<span data-ttu-id="abfc8-121">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="abfc8-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="abfc8-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="abfc8-122">C# 7.0</span></span> |
|[<span data-ttu-id="abfc8-123">Indexeur</span><span class="sxs-lookup"><span data-stu-id="abfc8-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="abfc8-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="abfc8-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="abfc8-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="abfc8-125">Methods</span></span>

<span data-ttu-id="abfc8-126">Une méthode expression-bodied se compose d’une seule expression qui retourne une valeur dont le type correspond au type de retour de la méthode ou, pour les méthodes qui retournent `void`, qui effectue une opération.</span><span class="sxs-lookup"><span data-stu-id="abfc8-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="abfc8-127">Par exemple, les types qui substituent la méthode <xref:System.Object.ToString%2A> incluent généralement une expression unique qui retourne la représentation sous forme de chaîne de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="abfc8-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="abfc8-128">L’exemple suivant définit une classe `Person` qui substitue la méthode <xref:System.Object.ToString%2A> avec une définition de corps d’expression.</span><span class="sxs-lookup"><span data-stu-id="abfc8-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="abfc8-129">Il définit également une méthode `DisplayName` qui affiche un nom sur la console.</span><span class="sxs-lookup"><span data-stu-id="abfc8-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="abfc8-130">Notez que le mot clé `return` n’est pas utilisé dans la définition de corps d’expression `ToString`.</span><span class="sxs-lookup"><span data-stu-id="abfc8-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="abfc8-131">Pour plus d’informations, consultez [Méthodes (Guide de programmation C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="abfc8-132">Propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="abfc8-132">Read-only properties</span></span>

<span data-ttu-id="abfc8-133">Depuis C# 6, vous pouvez utiliser une définition de corps d’expression pour implémenter une propriété en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="abfc8-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="abfc8-134">Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="abfc8-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="abfc8-135">L’exemple suivant définit une classe `Location` dont la propriété en lecture seule `Name` est implémentée comme une définition de corps d’expression qui retourne la valeur du champ privé `locationName` :</span><span class="sxs-lookup"><span data-stu-id="abfc8-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="abfc8-136">Pour plus d’informations sur les propriétés, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="abfc8-137">Propriétés</span><span class="sxs-lookup"><span data-stu-id="abfc8-137">Properties</span></span>

<span data-ttu-id="abfc8-138">Depuis C# 7.0, vous pouvez utiliser des définitions de corps d’expression pour implémenter la propriété `get` et les accesseurs `set`.</span><span class="sxs-lookup"><span data-stu-id="abfc8-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="abfc8-139">L’exemple suivant montre comment faire :</span><span class="sxs-lookup"><span data-stu-id="abfc8-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="abfc8-140">Pour plus d’informations sur les propriétés, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="abfc8-141">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="abfc8-141">Constructors</span></span>

<span data-ttu-id="abfc8-142">Une définition de corps d’expression pour un constructeur se compose généralement d’une seule expression d’assignation ou d’un appel de méthode qui gère les arguments du constructeur ou qui initialise l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="abfc8-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="abfc8-143">L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*.</span><span class="sxs-lookup"><span data-stu-id="abfc8-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="abfc8-144">La définition de corps d’expression assigne l’argument à la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="abfc8-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="abfc8-145">Pour plus d’informations, consultez [Constructeurs (Guide de programmation C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="abfc8-146">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="abfc8-146">Finalizers</span></span>

<span data-ttu-id="abfc8-147">Une définition de corps d’expression pour un finaliseur contient généralement des instructions de nettoyage, telles que des instructions qui libèrent les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="abfc8-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="abfc8-148">L’exemple suivant définit un finaliseur qui utilise une définition de corps d’expression pour indiquer que le finaliseur a été appelé.</span><span class="sxs-lookup"><span data-stu-id="abfc8-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="abfc8-149">Pour plus d’informations, consultez [Finaliseurs (Guide de programmation C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="abfc8-150">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="abfc8-150">Indexers</span></span>

<span data-ttu-id="abfc8-151">Comme avec les propriétés, l’indexeur `get` et les `set` accesseurs se composent de définitions de corps d’expression si l' `get` accesseur se compose d’une expression unique qui retourne une valeur ou l' `set` accesseur effectue une assignation simple.</span><span class="sxs-lookup"><span data-stu-id="abfc8-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="abfc8-152">L’exemple suivant définit une classe nommée `Sports` qui inclut un tableau <xref:System.String> interne contenant les noms de plusieurs sports.</span><span class="sxs-lookup"><span data-stu-id="abfc8-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="abfc8-153">L’indexeur `get` et les `set` accesseurs sont tous deux implémentés en tant que définitions de corps d’expression.</span><span class="sxs-lookup"><span data-stu-id="abfc8-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="abfc8-154">Pour plus d’informations, consultez [Indexeurs (Guide de programmation C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="abfc8-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
