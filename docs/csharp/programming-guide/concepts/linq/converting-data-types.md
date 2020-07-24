---
title: Conversion des types de données (C#)
description: Les méthodes de conversion changent le type d’objets en entrée. Consultez opérations de conversion dans les requêtes LINQ en C#, telles que Enumerable. AsEnumerable et Enumerable. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105491"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="d5174-104">Conversion des types de données (C#)</span><span class="sxs-lookup"><span data-stu-id="d5174-104">Converting Data Types (C#)</span></span>
<span data-ttu-id="d5174-105">Les méthodes de conversion changent le type d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="d5174-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="d5174-106">Les opérations de conversion dans les requêtes LINQ sont utiles dans diverses applications.</span><span class="sxs-lookup"><span data-stu-id="d5174-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="d5174-107">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="d5174-107">Following are some examples:</span></span>

- <span data-ttu-id="d5174-108">La méthode <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> peut être utilisée pour masquer l’implémentation personnalisée d’un type d’un opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="d5174-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="d5174-109">La méthode <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> peut être utilisée pour activer des collections non paramétrables pour l’interrogation LINQ.</span><span class="sxs-lookup"><span data-stu-id="d5174-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="d5174-110">Les méthodes <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu’à ce que la requête soit énumérée.</span><span class="sxs-lookup"><span data-stu-id="d5174-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="d5174-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d5174-111">Methods</span></span>
 <span data-ttu-id="d5174-112">Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de types de données.</span><span class="sxs-lookup"><span data-stu-id="d5174-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="d5174-113">Les méthodes de conversion de ce tableau dont les noms commencent par "As" modifient le type statique de la collection source mais ne l’énumèrent pas.</span><span class="sxs-lookup"><span data-stu-id="d5174-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="d5174-114">Les méthodes dont les noms commencent par "To" énumèrent la collection source et placent les éléments dans le type de collection correspondant.</span><span class="sxs-lookup"><span data-stu-id="d5174-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="d5174-115">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="d5174-115">Method Name</span></span>|<span data-ttu-id="d5174-116">Description</span><span class="sxs-lookup"><span data-stu-id="d5174-116">Description</span></span>|<span data-ttu-id="d5174-117">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="d5174-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="d5174-118">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="d5174-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="d5174-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="d5174-119">AsEnumerable</span></span>|<span data-ttu-id="d5174-120">Retourne l’entrée typée comme <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d5174-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="d5174-121">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="d5174-122">AsQueryable</span></span>|<span data-ttu-id="d5174-123">Convertit un <xref:System.Collections.IEnumerable> (générique) en <xref:System.Linq.IQueryable> (générique).</span><span class="sxs-lookup"><span data-stu-id="d5174-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="d5174-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-125">Caster</span><span class="sxs-lookup"><span data-stu-id="d5174-125">Cast</span></span>|<span data-ttu-id="d5174-126">Effectue un cast des éléments d’une collection en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d5174-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="d5174-127">Utilisez une variable de portée explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="d5174-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="d5174-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d5174-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-129">OfType</span><span class="sxs-lookup"><span data-stu-id="d5174-129">OfType</span></span>|<span data-ttu-id="d5174-130">Filtre les valeurs en fonction de leur capacité à faire l’objet d’un cast en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d5174-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="d5174-131">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="d5174-132">ToArray</span></span>|<span data-ttu-id="d5174-133">Convertit une collection en un tableau.</span><span class="sxs-lookup"><span data-stu-id="d5174-133">Converts a collection to an array.</span></span> <span data-ttu-id="d5174-134">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="d5174-134">This method forces query execution.</span></span>|<span data-ttu-id="d5174-135">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="d5174-136">ToDictionary</span></span>|<span data-ttu-id="d5174-137">Place des éléments dans un <xref:System.Collections.Generic.Dictionary%602> basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="d5174-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="d5174-138">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="d5174-138">This method forces query execution.</span></span>|<span data-ttu-id="d5174-139">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-140">ToList</span><span class="sxs-lookup"><span data-stu-id="d5174-140">ToList</span></span>|<span data-ttu-id="d5174-141">Convertit une collection en <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="d5174-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="d5174-142">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="d5174-142">This method forces query execution.</span></span>|<span data-ttu-id="d5174-143">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="d5174-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="d5174-144">ToLookup</span></span>|<span data-ttu-id="d5174-145">Place des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="d5174-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="d5174-146">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="d5174-146">This method forces query execution.</span></span>|<span data-ttu-id="d5174-147">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d5174-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="d5174-148">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="d5174-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="d5174-149">L’exemple de code suivant utilise une variable de portée explicitement typée pour effectuer un cast d’un type en un sous-type avant d’accéder à un membre qui est disponible uniquement sur le sous-type.</span><span class="sxs-lookup"><span data-stu-id="d5174-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a><span data-ttu-id="d5174-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5174-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d5174-151">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="d5174-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d5174-152">from, clause</span><span class="sxs-lookup"><span data-stu-id="d5174-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="d5174-153">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="d5174-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="d5174-154">Comment interroger un ArrayList avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d5174-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
