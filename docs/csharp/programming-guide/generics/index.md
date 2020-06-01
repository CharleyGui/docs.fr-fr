---
title: Génériques - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: a3ed3aa412c7d9c9d6b705dba80b527057c647fa
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241667"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="8d66d-102">Génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8d66d-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="8d66d-103">Les génériques introduisent le concept de paramètres de type dans .NET, ce qui permet de concevoir des classes et des méthodes qui diffèrent la spécification d’un ou plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instanciée par le code client.</span><span class="sxs-lookup"><span data-stu-id="8d66d-103">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="8d66d-104">Par exemple, en utilisant un paramètre de type générique `T` , vous pouvez écrire une seule classe qui peut être utilisée par un autre code client sans impliquer le coût ou le risque des casts ou des opérations de boxing du runtime, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="8d66d-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="8d66d-105">Les classes et les méthodes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité d’une façon que leurs équivalents non génériques ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="8d66d-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="8d66d-106">Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux.</span><span class="sxs-lookup"><span data-stu-id="8d66d-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="8d66d-107">L' <xref:System.Collections.Generic> espace de noms contient plusieurs classes de collection génériques.</span><span class="sxs-lookup"><span data-stu-id="8d66d-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="8d66d-108">Les collections non génériques, telles que, ne <xref:System.Collections.ArrayList> sont pas recommandées et sont conservées à des fins de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="8d66d-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="8d66d-109">Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d66d-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="8d66d-110">Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8d66d-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="8d66d-111">L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="8d66d-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="8d66d-112">(Dans la plupart des cas, vous devez utiliser la <xref:System.Collections.Generic.List%601> classe fournie par .net au lieu de créer la vôtre.) Le paramètre `T` de type est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste.</span><span class="sxs-lookup"><span data-stu-id="8d66d-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="8d66d-113">Il est utilisé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="8d66d-113">It is used in the following ways:</span></span>

- <span data-ttu-id="8d66d-114">Comme le type d’un paramètre de méthode dans la méthode`AddHead`.</span><span class="sxs-lookup"><span data-stu-id="8d66d-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="8d66d-115">Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="8d66d-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="8d66d-116">Comme le type de membre privé `data` de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="8d66d-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="8d66d-117">Notez que `T` est disponible pour la classe imbriquée `Node` .</span><span class="sxs-lookup"><span data-stu-id="8d66d-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="8d66d-118">Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.</span><span class="sxs-lookup"><span data-stu-id="8d66d-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="8d66d-119">L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="8d66d-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="8d66d-120">En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :</span><span class="sxs-lookup"><span data-stu-id="8d66d-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="8d66d-121">Vue d’ensemble des génériques</span><span class="sxs-lookup"><span data-stu-id="8d66d-121">Generics overview</span></span>

- <span data-ttu-id="8d66d-122">Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.</span><span class="sxs-lookup"><span data-stu-id="8d66d-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="8d66d-123">L’utilisation la plus courante des génériques est de créer des classes de collection.</span><span class="sxs-lookup"><span data-stu-id="8d66d-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="8d66d-124">La bibliothèque de classes .NET contient plusieurs classes de collection génériques dans l' <xref:System.Collections.Generic> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8d66d-124">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="8d66d-125">Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="8d66d-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="8d66d-126">Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="8d66d-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="8d66d-127">Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.</span><span class="sxs-lookup"><span data-stu-id="8d66d-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="8d66d-128">Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="8d66d-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8d66d-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="8d66d-129">Related sections</span></span>

- [<span data-ttu-id="8d66d-130">Paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="8d66d-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="8d66d-131">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="8d66d-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="8d66d-132">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="8d66d-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="8d66d-133">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="8d66d-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="8d66d-134">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="8d66d-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="8d66d-135">Délégués génériques</span><span class="sxs-lookup"><span data-stu-id="8d66d-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="8d66d-136">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="8d66d-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="8d66d-137">Génériques et réflexion</span><span class="sxs-lookup"><span data-stu-id="8d66d-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="8d66d-138">Génériques dans le runtime</span><span class="sxs-lookup"><span data-stu-id="8d66d-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="8d66d-139">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8d66d-139">C# language specification</span></span>

<span data-ttu-id="8d66d-140">Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="8d66d-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d66d-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d66d-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="8d66d-142">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8d66d-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d66d-143">Types</span><span class="sxs-lookup"><span data-stu-id="8d66d-143">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="8d66d-144">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="8d66d-144">Generics in .NET</span></span>](../../../standard/generics/index.md)
