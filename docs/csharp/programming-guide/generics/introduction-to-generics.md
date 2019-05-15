---
title: Introduction aux génériques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 0d7ecb7f7fd0bb0985234cdc2cf8d37b53323c86
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595487"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="e7a21-102">Introduction aux génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e7a21-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="e7a21-103">Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques.</span><span class="sxs-lookup"><span data-stu-id="e7a21-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="e7a21-104">Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux.</span><span class="sxs-lookup"><span data-stu-id="e7a21-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="e7a21-105">La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection génériques.</span><span class="sxs-lookup"><span data-stu-id="e7a21-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="e7a21-106">Pour toutes les applications qui ciblent le .NET Framework version 2.0 et ultérieures, il est recommandé d’utiliser les nouvelles classes de collection génériques plutôt que leurs équivalents non génériques, tels que <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="e7a21-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="e7a21-107">Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7a21-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="e7a21-108">Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="e7a21-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="e7a21-109">L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="e7a21-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="e7a21-110">Dans la plupart des cas, vous aurez tout intérêt à utiliser la classe <xref:System.Collections.Generic.List%601> fournie par la bibliothèque de classes .NET Framework plutôt que de créer la vôtre. Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e7a21-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="e7a21-111">Il est utilisé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="e7a21-111">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="e7a21-112">Comme le type d’un paramètre de méthode dans la méthode`AddHead`.</span><span class="sxs-lookup"><span data-stu-id="e7a21-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="e7a21-113">Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="e7a21-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="e7a21-114">Comme le type de membre privé `data` de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="e7a21-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="e7a21-115">Notez que T est disponible pour la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="e7a21-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="e7a21-116">Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.</span><span class="sxs-lookup"><span data-stu-id="e7a21-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="e7a21-117">L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="e7a21-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="e7a21-118">En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :</span><span class="sxs-lookup"><span data-stu-id="e7a21-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e7a21-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7a21-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="e7a21-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e7a21-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e7a21-121">Génériques</span><span class="sxs-lookup"><span data-stu-id="e7a21-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
