---
title: Conversion des types de données
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410849"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="43548-102">Conversion des types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43548-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="43548-103">Les méthodes de conversion changent le type d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="43548-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="43548-104">Les opérations de conversion dans les requêtes LINQ sont utiles dans diverses applications.</span><span class="sxs-lookup"><span data-stu-id="43548-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="43548-105">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="43548-105">The following are some examples:</span></span>

- <span data-ttu-id="43548-106">La méthode <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> peut être utilisée pour masquer l’implémentation personnalisée d’un type d’un opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="43548-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="43548-107">La méthode <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> peut être utilisée pour activer des collections non paramétrables pour l’interrogation LINQ.</span><span class="sxs-lookup"><span data-stu-id="43548-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="43548-108">Les méthodes <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu’à ce que la requête soit énumérée.</span><span class="sxs-lookup"><span data-stu-id="43548-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="43548-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43548-109">Methods</span></span>

<span data-ttu-id="43548-110">Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de types de données.</span><span class="sxs-lookup"><span data-stu-id="43548-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="43548-111">Les méthodes de conversion de ce tableau dont les noms commencent par "As" modifient le type statique de la collection source mais ne l’énumèrent pas.</span><span class="sxs-lookup"><span data-stu-id="43548-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="43548-112">Les méthodes dont les noms commencent par "To" énumèrent la collection source et placent les éléments dans le type de collection correspondant.</span><span class="sxs-lookup"><span data-stu-id="43548-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="43548-113">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="43548-113">Method Name</span></span>|<span data-ttu-id="43548-114">Description</span><span class="sxs-lookup"><span data-stu-id="43548-114">Description</span></span>|<span data-ttu-id="43548-115">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43548-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="43548-116">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="43548-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="43548-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="43548-117">AsEnumerable</span></span>|<span data-ttu-id="43548-118">Retourne l’entrée typée comme <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="43548-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="43548-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="43548-120">AsQueryable</span></span>|<span data-ttu-id="43548-121">Convertit un <xref:System.Collections.IEnumerable> (générique) en <xref:System.Linq.IQueryable> (générique).</span><span class="sxs-lookup"><span data-stu-id="43548-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="43548-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-123">Caster</span><span class="sxs-lookup"><span data-stu-id="43548-123">Cast</span></span>|<span data-ttu-id="43548-124">Effectue un cast des éléments d’une collection en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="43548-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-125">OfType</span><span class="sxs-lookup"><span data-stu-id="43548-125">OfType</span></span>|<span data-ttu-id="43548-126">Filtre les valeurs en fonction de leur capacité à faire l’objet d’un cast en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="43548-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="43548-127">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="43548-128">ToArray</span></span>|<span data-ttu-id="43548-129">Convertit une collection en un tableau.</span><span class="sxs-lookup"><span data-stu-id="43548-129">Converts a collection to an array.</span></span> <span data-ttu-id="43548-130">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="43548-130">This method forces query execution.</span></span>|<span data-ttu-id="43548-131">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="43548-132">ToDictionary</span></span>|<span data-ttu-id="43548-133">Place des éléments dans un <xref:System.Collections.Generic.Dictionary%602> basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="43548-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="43548-134">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="43548-134">This method forces query execution.</span></span>|<span data-ttu-id="43548-135">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-136">ToList</span><span class="sxs-lookup"><span data-stu-id="43548-136">ToList</span></span>|<span data-ttu-id="43548-137">Convertit une collection en <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="43548-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="43548-138">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="43548-138">This method forces query execution.</span></span>|<span data-ttu-id="43548-139">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="43548-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="43548-140">ToLookup</span></span>|<span data-ttu-id="43548-141">Place des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="43548-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="43548-142">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="43548-142">This method forces query execution.</span></span>|<span data-ttu-id="43548-143">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="43548-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="43548-144">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="43548-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="43548-145">L’exemple de code suivant utilise la `From As` clause pour effectuer un cast d’un type en un sous-type avant d’accéder à un membre qui est disponible uniquement sur le sous-type.</span><span class="sxs-lookup"><span data-stu-id="43548-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a><span data-ttu-id="43548-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43548-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="43548-147">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43548-147">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="43548-148">From, clause</span><span class="sxs-lookup"><span data-stu-id="43548-148">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="43548-149">Comment : interroger un ArrayList avec LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43548-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)
