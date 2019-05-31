---
title: Génériques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423401"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="3acef-102">Génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3acef-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="3acef-103">Les génériques ont été ajoutés à la version 2.0 du langage C# et du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3acef-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="3acef-104">Les génériques introduisent le concept des paramètres de type dans .NET Framework, qui permettent de concevoir des classes et des méthodes qui diffèrent la spécification d’un ou de plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instanciée par le code client.</span><span class="sxs-lookup"><span data-stu-id="3acef-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="3acef-105">Par exemple, à l’aide d’un paramètre de type générique T, vous pouvez écrire une seule classe qui peut être utilisée par un autre code client sans impliquer le coût ou le risque des casts ou des opérations de boxing à l’exécution, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="3acef-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="3acef-106">Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques.</span><span class="sxs-lookup"><span data-stu-id="3acef-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="3acef-107">Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux.</span><span class="sxs-lookup"><span data-stu-id="3acef-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="3acef-108">La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection génériques.</span><span class="sxs-lookup"><span data-stu-id="3acef-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="3acef-109">Pour toutes les applications qui ciblent le .NET Framework version 2.0 et ultérieures, il est recommandé d’utiliser les nouvelles classes de collection génériques plutôt que leurs équivalents non génériques, tels que <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="3acef-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="3acef-110">Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="3acef-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="3acef-111">Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="3acef-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="3acef-112">L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="3acef-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="3acef-113">Dans la plupart des cas, vous aurez tout intérêt à utiliser la classe <xref:System.Collections.Generic.List%601> fournie par la bibliothèque de classes .NET Framework plutôt que de créer la vôtre. Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste.</span><span class="sxs-lookup"><span data-stu-id="3acef-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="3acef-114">Il est utilisé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="3acef-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="3acef-115">Comme le type d’un paramètre de méthode dans la méthode`AddHead`.</span><span class="sxs-lookup"><span data-stu-id="3acef-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="3acef-116">Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="3acef-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="3acef-117">Comme le type de membre privé `data` de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="3acef-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="3acef-118">Notez que T est disponible pour la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="3acef-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="3acef-119">Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.</span><span class="sxs-lookup"><span data-stu-id="3acef-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="3acef-120">L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="3acef-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="3acef-121">En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :</span><span class="sxs-lookup"><span data-stu-id="3acef-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="3acef-122">Vue d’ensemble des génériques</span><span class="sxs-lookup"><span data-stu-id="3acef-122">Generics Overview</span></span>  
  
- <span data-ttu-id="3acef-123">Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.</span><span class="sxs-lookup"><span data-stu-id="3acef-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="3acef-124">L’utilisation la plus courante des génériques est de créer des classes de collection.</span><span class="sxs-lookup"><span data-stu-id="3acef-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="3acef-125">La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="3acef-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="3acef-126">Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="3acef-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="3acef-127">Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="3acef-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="3acef-128">Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.</span><span class="sxs-lookup"><span data-stu-id="3acef-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="3acef-129">Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3acef-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3acef-130">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3acef-130">Related Sections</span></span>  
 <span data-ttu-id="3acef-131">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="3acef-131">For more information:</span></span>  
  
- [<span data-ttu-id="3acef-132">Paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="3acef-132">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [<span data-ttu-id="3acef-133">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="3acef-133">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="3acef-134">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="3acef-134">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [<span data-ttu-id="3acef-135">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="3acef-135">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [<span data-ttu-id="3acef-136">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="3acef-136">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [<span data-ttu-id="3acef-137">Délégués génériques</span><span class="sxs-lookup"><span data-stu-id="3acef-137">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [<span data-ttu-id="3acef-138">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="3acef-138">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="3acef-139">Génériques et réflexion</span><span class="sxs-lookup"><span data-stu-id="3acef-139">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [<span data-ttu-id="3acef-140">Génériques dans le runtime</span><span class="sxs-lookup"><span data-stu-id="3acef-140">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3acef-141">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3acef-141">C# Language Specification</span></span>  
 <span data-ttu-id="3acef-142">Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="3acef-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acef-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3acef-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3acef-144">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3acef-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3acef-145">Types</span><span class="sxs-lookup"><span data-stu-id="3acef-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="3acef-146">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="3acef-146">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [<span data-ttu-id="3acef-147">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="3acef-147">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [<span data-ttu-id="3acef-148">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="3acef-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
