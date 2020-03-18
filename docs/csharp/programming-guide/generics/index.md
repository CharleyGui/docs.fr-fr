---
title: Génériques - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167490"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="42f18-102">Génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="42f18-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="42f18-103">Les génériques introduisent le concept de paramètres de type dans le cadre .NET, qui permettent de concevoir des classes et des méthodes qui reportent la spécification d’un ou plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instantanée par le code client.</span><span class="sxs-lookup"><span data-stu-id="42f18-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="42f18-104">Par exemple, en utilisant `T`un paramètre de type générique, vous pouvez écrire une seule classe que l’autre code client peut utiliser sans encourir le coût ou le risque de moulages en temps d’exécution ou d’opérations de boxe, comme indiqué ici:</span><span class="sxs-lookup"><span data-stu-id="42f18-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="42f18-105">Les classes et les méthodes génériques combinent la réutilisabilité, la sécurité de type et l’efficacité d’une manière que leurs homologues non génériques ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="42f18-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="42f18-106">Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux.</span><span class="sxs-lookup"><span data-stu-id="42f18-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="42f18-107">L’espace <xref:System.Collections.Generic> de nom contient plusieurs classes de collecte génériques.</span><span class="sxs-lookup"><span data-stu-id="42f18-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="42f18-108">Les collections non génériques, telles que <xref:System.Collections.ArrayList> ne sont pas recommandées et sont maintenues à des fins de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="42f18-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="42f18-109">Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="42f18-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="42f18-110">Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="42f18-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="42f18-111">L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="42f18-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="42f18-112">(Dans la plupart des <xref:System.Collections.Generic.List%601> cas, vous devriez utiliser la classe fournie par la bibliothèque de classe cadre .NET au lieu de créer votre propre.) Le paramètre de `T` type est utilisé à plusieurs endroits où un type concret serait normalement utilisé pour indiquer le type de l’article stocké dans la liste.</span><span class="sxs-lookup"><span data-stu-id="42f18-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="42f18-113">Il est utilisé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="42f18-113">It is used in the following ways:</span></span>

- <span data-ttu-id="42f18-114">Comme le type d’un paramètre de méthode dans la méthode`AddHead`.</span><span class="sxs-lookup"><span data-stu-id="42f18-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="42f18-115">Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="42f18-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="42f18-116">Comme le type de membre privé `data` de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="42f18-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="42f18-117">Notez `T` que c’est `Node` à la disposition de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="42f18-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="42f18-118">Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.</span><span class="sxs-lookup"><span data-stu-id="42f18-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="42f18-119">L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="42f18-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="42f18-120">En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :</span><span class="sxs-lookup"><span data-stu-id="42f18-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="42f18-121">Aperçu des génériques</span><span class="sxs-lookup"><span data-stu-id="42f18-121">Generics overview</span></span>

- <span data-ttu-id="42f18-122">Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.</span><span class="sxs-lookup"><span data-stu-id="42f18-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="42f18-123">L’utilisation la plus courante des génériques est de créer des classes de collection.</span><span class="sxs-lookup"><span data-stu-id="42f18-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="42f18-124">La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="42f18-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="42f18-125">Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="42f18-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="42f18-126">Vous pouvez créer vos propres interfaces génériques, classes, méthodes, événements et délégués.</span><span class="sxs-lookup"><span data-stu-id="42f18-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="42f18-127">Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.</span><span class="sxs-lookup"><span data-stu-id="42f18-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="42f18-128">Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="42f18-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="42f18-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="42f18-129">Related sections</span></span>

- [<span data-ttu-id="42f18-130">Paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="42f18-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="42f18-131">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="42f18-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="42f18-132">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="42f18-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="42f18-133">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="42f18-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="42f18-134">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="42f18-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="42f18-135">Délégués génériques</span><span class="sxs-lookup"><span data-stu-id="42f18-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="42f18-136">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="42f18-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="42f18-137">Génériques et réflexion</span><span class="sxs-lookup"><span data-stu-id="42f18-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="42f18-138">Génériques dans le runtime</span><span class="sxs-lookup"><span data-stu-id="42f18-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="42f18-139">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="42f18-139">C# language specification</span></span>

<span data-ttu-id="42f18-140">Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="42f18-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="42f18-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42f18-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="42f18-142">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="42f18-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42f18-143">Types</span><span class="sxs-lookup"><span data-stu-id="42f18-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="42f18-144">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="42f18-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="42f18-145">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="42f18-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="42f18-146">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="42f18-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
