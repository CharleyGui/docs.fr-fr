---
title: Interfaces génériques - Guide de programmation C#
description: En savoir plus sur l’utilisation des interfaces génériques en C#. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 43817a236e95b3ab8fd0ba94da98457eeec2396c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301890"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="bd2d9-104">Interfaces génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bd2d9-104">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="bd2d9-105">Il est souvent utile de définir des interfaces pour les classes de collections génériques, ou pour les classes génériques qui représentent des éléments dans la collection.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-105">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="bd2d9-106">Pour les classes génériques, il est préférable d’utiliser des interfaces génériques, comme <xref:System.IComparable%601> à la place d’<xref:System.IComparable>, pour éviter les opérations de boxing et d’unboxing sur les types valeur.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-106">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="bd2d9-107">La bibliothèque de classes .NET Framework définit plusieurs interfaces génériques à utiliser avec les classes de collections dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-107">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="bd2d9-108">Quand une interface est spécifiée comme une contrainte sur un paramètre de type, seuls les types qui implémentent l’interface peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-108">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="bd2d9-109">L’exemple de code suivant illustre une classe `SortedList<T>` qui dérive de la classe `GenericList<T>`.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-109">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="bd2d9-110">Pour plus d’informations, consultez [Introduction aux génériques](./index.md).</span><span class="sxs-lookup"><span data-stu-id="bd2d9-110">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="bd2d9-111">`SortedList<T>` ajoute la contrainte `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-111">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="bd2d9-112">Ceci permet à la méthode `BubbleSort` dans `SortedList<T>` d’utiliser la méthode générique <xref:System.IComparable%601.CompareTo%2A> sur les éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-112">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="bd2d9-113">Dans cet exemple, les éléments de liste sont une classe simple, `Person`, qui implémente `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-113">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="bd2d9-114">Plusieurs interfaces peuvent être spécifiées en tant que contraintes sur un seul type, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bd2d9-114">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="bd2d9-115">Une interface peut définir plusieurs paramètres de type, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bd2d9-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="bd2d9-116">Les règles d’héritage qui s’appliquent aux classes s’appliquent également aux interfaces :</span><span class="sxs-lookup"><span data-stu-id="bd2d9-116">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="bd2d9-117">Les interfaces génériques peuvent hériter d’interfaces non génériques si l’interface générique est de type contravariant, ce qui signifie qu’elle utilise uniquement son paramètre de type comme valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-117">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="bd2d9-118">Dans la bibliothèque de classes .NET Framework, <xref:System.Collections.Generic.IEnumerable%601> hérite d’<xref:System.Collections.IEnumerable>, car <xref:System.Collections.Generic.IEnumerable%601> utilise uniquement `T` dans la valeur de retour de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> et dans l’accesseur Get de propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-118">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="bd2d9-119">Les classes concrètes peuvent implémenter des interfaces construites fermées, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bd2d9-119">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="bd2d9-120">Les classes génériques peuvent implémenter des interfaces génériques ou des interfaces construites fermées tant que la liste de paramètres de classe fournit tous les arguments requis par l’interface, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bd2d9-120">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="bd2d9-121">Les règles qui déterminent la surcharge des méthodes sont les mêmes pour les méthodes dans les classes génériques, les structs génériques ou les interfaces génériques.</span><span class="sxs-lookup"><span data-stu-id="bd2d9-121">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="bd2d9-122">Pour plus d’informations, consultez [Méthodes génériques](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="bd2d9-122">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2d9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd2d9-123">See also</span></span>

- [<span data-ttu-id="bd2d9-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bd2d9-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bd2d9-125">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="bd2d9-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="bd2d9-126">interface</span><span class="sxs-lookup"><span data-stu-id="bd2d9-126">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="bd2d9-127">Génériques</span><span class="sxs-lookup"><span data-stu-id="bd2d9-127">Generics</span></span>](../../../standard/generics/index.md)
