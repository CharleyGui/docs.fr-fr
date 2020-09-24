---
title: Conversion des types de données (C#)
description: Les méthodes de conversion changent le type d’objets en entrée. Consultez opérations de conversion dans les requêtes LINQ en C#, telles que Enumerable. AsEnumerable et Enumerable. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: f9e3b354fd6eeba6564067550ea3821e4946d92f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159135"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="1fe11-104">Conversion des types de données (C#)</span><span class="sxs-lookup"><span data-stu-id="1fe11-104">Converting Data Types (C#)</span></span>

<span data-ttu-id="1fe11-105">Les méthodes de conversion changent le type d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="1fe11-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="1fe11-106">Les opérations de conversion dans les requêtes LINQ sont utiles dans diverses applications.</span><span class="sxs-lookup"><span data-stu-id="1fe11-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="1fe11-107">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="1fe11-107">Following are some examples:</span></span>

- <span data-ttu-id="1fe11-108">La méthode <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> peut être utilisée pour masquer l’implémentation personnalisée d’un type d’un opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="1fe11-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="1fe11-109">La méthode <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> peut être utilisée pour activer des collections non paramétrables pour l’interrogation LINQ.</span><span class="sxs-lookup"><span data-stu-id="1fe11-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="1fe11-110">Les méthodes <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu’à ce que la requête soit énumérée.</span><span class="sxs-lookup"><span data-stu-id="1fe11-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="1fe11-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1fe11-111">Methods</span></span>

 <span data-ttu-id="1fe11-112">Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de types de données.</span><span class="sxs-lookup"><span data-stu-id="1fe11-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="1fe11-113">Les méthodes de conversion de ce tableau dont les noms commencent par "As" modifient le type statique de la collection source mais ne l’énumèrent pas.</span><span class="sxs-lookup"><span data-stu-id="1fe11-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="1fe11-114">Les méthodes dont les noms commencent par "To" énumèrent la collection source et placent les éléments dans le type de collection correspondant.</span><span class="sxs-lookup"><span data-stu-id="1fe11-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="1fe11-115">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="1fe11-115">Method Name</span></span>|<span data-ttu-id="1fe11-116">Description</span><span class="sxs-lookup"><span data-stu-id="1fe11-116">Description</span></span>|<span data-ttu-id="1fe11-117">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="1fe11-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="1fe11-118">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="1fe11-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="1fe11-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="1fe11-119">AsEnumerable</span></span>|<span data-ttu-id="1fe11-120">Retourne l’entrée typée comme <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1fe11-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="1fe11-121">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="1fe11-122">AsQueryable</span></span>|<span data-ttu-id="1fe11-123">Convertit un <xref:System.Collections.IEnumerable> (générique) en <xref:System.Linq.IQueryable> (générique).</span><span class="sxs-lookup"><span data-stu-id="1fe11-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="1fe11-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-125">Caster</span><span class="sxs-lookup"><span data-stu-id="1fe11-125">Cast</span></span>|<span data-ttu-id="1fe11-126">Effectue un cast des éléments d’une collection en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="1fe11-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="1fe11-127">Utilisez une variable de portée explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="1fe11-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="1fe11-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1fe11-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-129">OfType</span><span class="sxs-lookup"><span data-stu-id="1fe11-129">OfType</span></span>|<span data-ttu-id="1fe11-130">Filtre les valeurs en fonction de leur capacité à faire l’objet d’un cast en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="1fe11-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="1fe11-131">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="1fe11-132">ToArray</span></span>|<span data-ttu-id="1fe11-133">Convertit une collection en un tableau.</span><span class="sxs-lookup"><span data-stu-id="1fe11-133">Converts a collection to an array.</span></span> <span data-ttu-id="1fe11-134">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="1fe11-134">This method forces query execution.</span></span>|<span data-ttu-id="1fe11-135">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="1fe11-136">ToDictionary</span></span>|<span data-ttu-id="1fe11-137">Place des éléments dans un <xref:System.Collections.Generic.Dictionary%602> basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="1fe11-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="1fe11-138">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="1fe11-138">This method forces query execution.</span></span>|<span data-ttu-id="1fe11-139">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-140">ToList</span><span class="sxs-lookup"><span data-stu-id="1fe11-140">ToList</span></span>|<span data-ttu-id="1fe11-141">Convertit une collection en <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1fe11-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1fe11-142">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="1fe11-142">This method forces query execution.</span></span>|<span data-ttu-id="1fe11-143">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1fe11-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="1fe11-144">ToLookup</span></span>|<span data-ttu-id="1fe11-145">Place des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="1fe11-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="1fe11-146">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="1fe11-146">This method forces query execution.</span></span>|<span data-ttu-id="1fe11-147">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="1fe11-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="1fe11-148">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="1fe11-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="1fe11-149">L’exemple de code suivant utilise une variable de portée explicitement typée pour effectuer un cast d’un type en un sous-type avant d’accéder à un membre qui est disponible uniquement sur le sous-type.</span><span class="sxs-lookup"><span data-stu-id="1fe11-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1fe11-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fe11-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1fe11-151">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="1fe11-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1fe11-152">from, clause</span><span class="sxs-lookup"><span data-stu-id="1fe11-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="1fe11-153">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="1fe11-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="1fe11-154">Comment interroger un ArrayList avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1fe11-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
