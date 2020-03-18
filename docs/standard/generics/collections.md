---
title: Collections génériques dans .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708408"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="38e13-102">Collections génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="38e13-102">Generic collections in .NET</span></span>

 <span data-ttu-id="38e13-103">La bibliothèque de classes .NET fournit plusieurs classes de collections génériques dans les espaces de noms <xref:System.Collections.Generic> et <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="38e13-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="38e13-104">Pour plus d’informations sur ces classes, consultez [Types de collections fréquemment utilisés](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="38e13-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="38e13-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="38e13-105">System.Collections.Generic</span></span>

 <span data-ttu-id="38e13-106">La plupart des types de collections génériques sont des équivalents directs de types non génériques.</span><span class="sxs-lookup"><span data-stu-id="38e13-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="38e13-107"><xref:System.Collections.Generic.Dictionary%602> est une version générique de <xref:System.Collections.Hashtable> ; elle utilise la structure générique <xref:System.Collections.Generic.KeyValuePair%602> pour l'énumération, au lieu de <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="38e13-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="38e13-108"><xref:System.Collections.Generic.List%601> est une version générique de <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="38e13-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="38e13-109">Il existe des classes génériques <xref:System.Collections.Generic.Queue%601> et <xref:System.Collections.Generic.Stack%601> qui correspondent aux versions non génériques.</span><span class="sxs-lookup"><span data-stu-id="38e13-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="38e13-110">Il existe des versions génériques et non génériques de <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="38e13-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="38e13-111">Les deux versions sont des hybrides d'un dictionnaire et une liste.</span><span class="sxs-lookup"><span data-stu-id="38e13-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="38e13-112">La classe générique <xref:System.Collections.Generic.SortedDictionary%602> est un dictionnaire pur et n'a pas de contrepartie non générique.</span><span class="sxs-lookup"><span data-stu-id="38e13-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="38e13-113">La classe générique <xref:System.Collections.Generic.LinkedList%601> est une véritable liste liée.</span><span class="sxs-lookup"><span data-stu-id="38e13-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="38e13-114">Il n'a pas de contrepartie non générique.</span><span class="sxs-lookup"><span data-stu-id="38e13-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="38e13-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="38e13-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="38e13-116">La classe générique <xref:System.Collections.ObjectModel.Collection%601> fournit une classe de base pour dériver vos propres types de collections génériques.</span><span class="sxs-lookup"><span data-stu-id="38e13-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="38e13-117">La classe <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> offre un moyen facile de produire une collection en lecture seule à partir de n'importe quel type implémentant l'interface générique <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="38e13-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="38e13-118">La classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602> fournit un moyen de stocker des objets qui contiennent leurs propres clés.</span><span class="sxs-lookup"><span data-stu-id="38e13-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="38e13-119">Autres types génériques</span><span class="sxs-lookup"><span data-stu-id="38e13-119">Other generic types</span></span>

 <span data-ttu-id="38e13-120">La structure générique <xref:System.Nullable%601> vous permet d'utiliser des types valeur comme si la valeur `null` pouvait leur être affectée.</span><span class="sxs-lookup"><span data-stu-id="38e13-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="38e13-121">Ceci peut être utile quand vous travaillez avec des requêtes de base de données, où des champs contenant des types valeur peuvent être manquants.</span><span class="sxs-lookup"><span data-stu-id="38e13-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="38e13-122">Le paramètre de type générique peut être n'importe quel type valeur.</span><span class="sxs-lookup"><span data-stu-id="38e13-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38e13-123">En C# et Visual Basic, il n'est pas nécessaire d'utiliser <xref:System.Nullable%601> explicitement, car le langage a une syntaxe pour les types Nullables.</span><span class="sxs-lookup"><span data-stu-id="38e13-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="38e13-124">Voir [Les types de valeur nulables (référence C)](../../csharp/language-reference/builtin-types/nullable-value-types.md) et les types de valeur [nullable (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="38e13-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="38e13-125">La structure générique <xref:System.ArraySegment%601> offre un moyen de délimiter une plage d'éléments dans un tableau unidimensionnel de base zéro, de n'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="38e13-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="38e13-126">Le paramètre de type générique est le type des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="38e13-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="38e13-127">Le délégué générique <xref:System.EventHandler%601> élimine le besoin de déclarer un type de délégué pour gérer les événements, si votre événement respecte le modèle de gestion des événements utilisé par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38e13-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="38e13-128">Par exemple, supposons que vous avez créé une classe `MyEventArgs` dérivée de <xref:System.EventArgs>, pour stocker les données de votre événement.</span><span class="sxs-lookup"><span data-stu-id="38e13-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="38e13-129">Vous pouvez ensuite déclarer l'événement comme suit :</span><span class="sxs-lookup"><span data-stu-id="38e13-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="38e13-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38e13-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="38e13-131">Génériques</span><span class="sxs-lookup"><span data-stu-id="38e13-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="38e13-132">Délégués génériques pour la manipulation de tableaux et de listes</span><span class="sxs-lookup"><span data-stu-id="38e13-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="38e13-133">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="38e13-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
