---
title: Comparaisons et tris dans les collections
description: Les comparaisons &es sont triées à l’aide des classes System. Collections dans .NET, ce qui permet de trouver un élément pour supprimer ou retourner la valeur d’une paire clé-valeur.
ms.date: 04/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: e4d40568710498df811954c86bb36382d93057a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733540"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="0f570-103">Comparaisons et tris dans les collections</span><span class="sxs-lookup"><span data-stu-id="0f570-103">Comparisons and sorts within collections</span></span>

<span data-ttu-id="0f570-104">Les classes <xref:System.Collections> effectuent des comparaisons dans quasiment tous les processus impliqués dans la gestion des collections, que ce soit pendant la recherche d'un élément à supprimer ou le renvoi d'une valeur d'une paire clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="0f570-104">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="0f570-105">Les collections utilisent généralement un comparateur d’égalité et/ou un comparateur de classement.</span><span class="sxs-lookup"><span data-stu-id="0f570-105">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="0f570-106">Deux constructions sont utilisées pour les comparaisons.</span><span class="sxs-lookup"><span data-stu-id="0f570-106">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>

## <a name="check-for-equality"></a><span data-ttu-id="0f570-107">Vérifier l’égalité</span><span class="sxs-lookup"><span data-stu-id="0f570-107">Check for equality</span></span>

<span data-ttu-id="0f570-108">Les méthodes telles que `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>et `Remove` utilisent un comparateur d'égalité pour les éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="0f570-108">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="0f570-109">Si la collection est générique, les éléments sont comparés pour déterminer leur égalité conformément aux indications suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f570-109">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="0f570-110">Si le type T implémente l'interface générique <xref:System.IEquatable%601> , le comparateur d'égalité est la méthode <xref:System.IEquatable%601.Equals%2A> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f570-110">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="0f570-111">Si le type T n'implémente pas <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0f570-111">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="0f570-112">De plus, certaines surcharges de constructeur pour les collections de dictionnaires acceptent une implémentation <xref:System.Collections.Generic.IEqualityComparer%601>, qui est utilisée pour comparer l'égalité de clés.</span><span class="sxs-lookup"><span data-stu-id="0f570-112">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="0f570-113">Pour obtenir un exemple, consultez le constructeur <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="0f570-113">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>

## <a name="determine-sort-order"></a><span data-ttu-id="0f570-114">Déterminer l’ordre de tri</span><span class="sxs-lookup"><span data-stu-id="0f570-114">Determine sort order</span></span>

<span data-ttu-id="0f570-115">Les méthodes telles que `BinarySearch` et `Sort` utilisent un comparateur de classement pour les éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="0f570-115">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="0f570-116">Les comparaisons peuvent être effectuées entre les éléments d'une collection, ou entre un élément et une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0f570-116">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="0f570-117">Pour comparer des objets, il existe le `default comparer` et le `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="0f570-117">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="0f570-118">Le comparateur par défaut repose sur au moins l'un des objets comparés pour implémenter l'interface **IComparable** .</span><span class="sxs-lookup"><span data-stu-id="0f570-118">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="0f570-119">Il est recommandé d'implémenter **IComparable** sur toutes les classes utilisées en tant que valeurs dans une collection de listes ou en tant que clés dans une collection de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="0f570-119">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="0f570-120">Pour une collection générique, la comparaison d'égalité est déterminée selon ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f570-120">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="0f570-121">Si le type T implémente l'interface générique <xref:System.IComparable%601?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f570-121">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="0f570-122">Si le type T implémente l'interface non générique <xref:System.IComparable?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f570-122">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="0f570-123">Si le type T n’implémente aucune interface, il n’existe aucun comparateur par défaut, et un comparateur ou un délégué de comparaison doit être fourni explicitement.</span><span class="sxs-lookup"><span data-stu-id="0f570-123">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="0f570-124">Pour fournir des comparaisons explicites, certaines méthodes acceptent une implémentation **IComparer** en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="0f570-124">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="0f570-125">Par exemple, la méthode <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> accepte une implémentation <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0f570-125">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="0f570-126">Le paramètre de culture actuel du système peut affecter les comparaisons et les tris d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0f570-126">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="0f570-127">Par défaut, les comparaisons et les tris des classes **Collections** sont dépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="0f570-127">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="0f570-128">Pour ignorer le paramètre de culture et donc obtenir des résultats cohérents de comparaison et de tri, utilisez <xref:System.Globalization.CultureInfo.InvariantCulture%2A> avec des surcharges de membre qui acceptent <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="0f570-128">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="0f570-129">Pour plus d’informations, consultez [Performing Culture-Insensitive String Operations in Collections](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) et [Performing Culture-Insensitive String Operations in Arrays](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="0f570-129">For more information, see [Performing Culture-Insensitive String Operations in Collections](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>

## <a name="equality-and-sort-example"></a><span data-ttu-id="0f570-130">Exemple d'égalité et de tri</span><span class="sxs-lookup"><span data-stu-id="0f570-130">Equality and sort example</span></span>

<span data-ttu-id="0f570-131">Le code suivant illustre une implémentation de <xref:System.IEquatable%601> et de <xref:System.IComparable%601> dans un objet métier simple.</span><span class="sxs-lookup"><span data-stu-id="0f570-131">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="0f570-132">De plus, quand l'objet est stocké dans une liste, puis trié, vous verrez que l'appel de la méthode <xref:System.Collections.Generic.List%601.Sort> se traduit par l'utilisation du comparateur par défaut pour le type `Part` , et par l'implémentation de la méthode <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> à l'aide d'une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="0f570-132">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0f570-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f570-133">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
