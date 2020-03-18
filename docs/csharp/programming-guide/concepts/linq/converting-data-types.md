---
title: Conversion des types de données (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347201"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="c28ef-102">Conversion des types de données (C#)</span><span class="sxs-lookup"><span data-stu-id="c28ef-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="c28ef-103">Les méthodes de conversion changent le type d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="c28ef-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="c28ef-104">Les opérations de conversion dans les requêtes LINQ sont utiles dans diverses applications.</span><span class="sxs-lookup"><span data-stu-id="c28ef-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="c28ef-105">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="c28ef-105">Following are some examples:</span></span>

- <span data-ttu-id="c28ef-106">La méthode <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> peut être utilisée pour masquer l’implémentation personnalisée d’un type d’un opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="c28ef-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="c28ef-107">La méthode <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> peut être utilisée pour activer des collections non paramétrables pour l’interrogation LINQ.</span><span class="sxs-lookup"><span data-stu-id="c28ef-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="c28ef-108">Les méthodes <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu’à ce que la requête soit énumérée.</span><span class="sxs-lookup"><span data-stu-id="c28ef-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="c28ef-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c28ef-109">Methods</span></span>
 <span data-ttu-id="c28ef-110">Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de types de données.</span><span class="sxs-lookup"><span data-stu-id="c28ef-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="c28ef-111">Les méthodes de conversion de ce tableau dont les noms commencent par "As" modifient le type statique de la collection source mais ne l’énumèrent pas.</span><span class="sxs-lookup"><span data-stu-id="c28ef-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="c28ef-112">Les méthodes dont les noms commencent par "To" énumèrent la collection source et placent les éléments dans le type de collection correspondant.</span><span class="sxs-lookup"><span data-stu-id="c28ef-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="c28ef-113">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="c28ef-113">Method Name</span></span>|<span data-ttu-id="c28ef-114">Description</span><span class="sxs-lookup"><span data-stu-id="c28ef-114">Description</span></span>|<span data-ttu-id="c28ef-115">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="c28ef-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="c28ef-116">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="c28ef-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="c28ef-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="c28ef-117">AsEnumerable</span></span>|<span data-ttu-id="c28ef-118">Retourne l’entrée typée comme <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c28ef-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="c28ef-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="c28ef-120">AsQueryable</span></span>|<span data-ttu-id="c28ef-121">Convertit un <xref:System.Collections.IEnumerable> (générique) en <xref:System.Linq.IQueryable> (générique).</span><span class="sxs-lookup"><span data-stu-id="c28ef-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="c28ef-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-123">Cast</span><span class="sxs-lookup"><span data-stu-id="c28ef-123">Cast</span></span>|<span data-ttu-id="c28ef-124">Effectue un cast des éléments d’une collection en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="c28ef-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="c28ef-125">Utilisez une variable de portée explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="c28ef-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="c28ef-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c28ef-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-127">OfType</span><span class="sxs-lookup"><span data-stu-id="c28ef-127">OfType</span></span>|<span data-ttu-id="c28ef-128">Filtre les valeurs en fonction de leur capacité à faire l’objet d’un cast en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="c28ef-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="c28ef-129">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="c28ef-130">ToArray</span></span>|<span data-ttu-id="c28ef-131">Convertit une collection en un tableau.</span><span class="sxs-lookup"><span data-stu-id="c28ef-131">Converts a collection to an array.</span></span> <span data-ttu-id="c28ef-132">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="c28ef-132">This method forces query execution.</span></span>|<span data-ttu-id="c28ef-133">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="c28ef-134">ToDictionary</span></span>|<span data-ttu-id="c28ef-135">Place des éléments dans un <xref:System.Collections.Generic.Dictionary%602> basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="c28ef-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="c28ef-136">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="c28ef-136">This method forces query execution.</span></span>|<span data-ttu-id="c28ef-137">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-138">ToList</span><span class="sxs-lookup"><span data-stu-id="c28ef-138">ToList</span></span>|<span data-ttu-id="c28ef-139">Convertit une collection en <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="c28ef-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c28ef-140">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="c28ef-140">This method forces query execution.</span></span>|<span data-ttu-id="c28ef-141">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c28ef-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="c28ef-142">ToLookup</span></span>|<span data-ttu-id="c28ef-143">Place des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="c28ef-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="c28ef-144">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="c28ef-144">This method forces query execution.</span></span>|<span data-ttu-id="c28ef-145">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c28ef-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="c28ef-146">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="c28ef-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="c28ef-147">L’exemple de code suivant utilise une variable de plage explicitement tapée pour jeter un type à un sous-type avant d’accéder à un membre qui n’est disponible que sur le sous-type.</span><span class="sxs-lookup"><span data-stu-id="c28ef-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c28ef-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c28ef-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c28ef-149">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="c28ef-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c28ef-150">de la clause</span><span class="sxs-lookup"><span data-stu-id="c28ef-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="c28ef-151">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="c28ef-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="c28ef-152">Comment interroger un ArrayList avec LINQ (C)</span><span class="sxs-lookup"><span data-stu-id="c28ef-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
