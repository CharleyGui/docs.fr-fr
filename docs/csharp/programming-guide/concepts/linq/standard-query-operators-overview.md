---
title: Présentation des opérateurs de requête standard (C#)
description: Les opérateurs de requête standard LINQ fournissent des fonctionnalités de requête, notamment le filtrage, la projection, l’agrégation et le tri en C#.
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 8a399f52881e10f8d94263843b5992101f96a5ea
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302319"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="52c3d-103">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-103">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="52c3d-104">Les *opérateurs de requête standard* sont les méthodes qui forment le modèle de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="52c3d-104">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="52c3d-105">La plupart de ces méthodes fonctionnent sur des séquences, où une séquence est un objet dont le type implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> ou l’interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="52c3d-105">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="52c3d-106">Les opérateurs de requête standard fournissent des fonctionnalités de requête, dont notamment le filtrage, la projection, l’agrégation, le tri, etc.</span><span class="sxs-lookup"><span data-stu-id="52c3d-106">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="52c3d-107">Il existe deux ensembles d’opérateurs de requête standard LINQ : un qui opère sur des objets de type <xref:System.Collections.Generic.IEnumerable%601> , un autre qui opère sur des objets de type <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="52c3d-107">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="52c3d-108">Les méthodes qui composent chaque ensemble sont des membres statiques des classes <xref:System.Linq.Enumerable> et <xref:System.Linq.Queryable>, respectivement.</span><span class="sxs-lookup"><span data-stu-id="52c3d-108">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="52c3d-109">Elles sont définies en tant que *méthodes d’extension* du type sur lequel elles opèrent.</span><span class="sxs-lookup"><span data-stu-id="52c3d-109">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="52c3d-110">Les méthodes d’extension peuvent être appelées à l’aide de la syntaxe de méthode statique ou de la syntaxe de méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="52c3d-110">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="52c3d-111">De plus, plusieurs méthodes d’opérateur de requête standard fonctionnent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="52c3d-111">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="52c3d-112">Le type <xref:System.Linq.Enumerable> définit deux de ces méthodes qui fonctionnent toutes deux sur les objets de type <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="52c3d-112">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="52c3d-113">Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, vous permettent d’autoriser l’interrogation d’une collection non paramétrée, ou non générique, dans le modèle LINQ.</span><span class="sxs-lookup"><span data-stu-id="52c3d-113">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="52c3d-114">Pour ce faire, ils créent une collection fortement typée d’objets.</span><span class="sxs-lookup"><span data-stu-id="52c3d-114">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="52c3d-115">La classe <xref:System.Linq.Queryable> définit deux méthodes similaires, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur les objets de type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="52c3d-115">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="52c3d-116">Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="52c3d-116">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="52c3d-117">Les méthodes qui retournent une valeur de singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="52c3d-117">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="52c3d-118">Les méthodes qui retournent une séquence diffèrent l’exécution de la requête et retournent un objet énumérable.</span><span class="sxs-lookup"><span data-stu-id="52c3d-118">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="52c3d-119">Pour les méthodes qui opèrent sur des collections en mémoire, autrement dit, les méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601> , l’objet énumérable retourné capture les arguments passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="52c3d-119">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="52c3d-120">Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.</span><span class="sxs-lookup"><span data-stu-id="52c3d-120">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="52c3d-121">En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601> n’implémentent aucun comportement d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="52c3d-121">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="52c3d-122">Ils créent une arborescence d’expressions qui représente la requête à exécuter.</span><span class="sxs-lookup"><span data-stu-id="52c3d-122">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="52c3d-123">Le traitement des requêtes est géré par l’objet <xref:System.Linq.IQueryable%601> source.</span><span class="sxs-lookup"><span data-stu-id="52c3d-123">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="52c3d-124">Les appels aux méthodes de requête peuvent être chaînés dans une requête unique, ce qui permet de rendre les requêtes arbitrairement complexes.</span><span class="sxs-lookup"><span data-stu-id="52c3d-124">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="52c3d-125">L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.</span><span class="sxs-lookup"><span data-stu-id="52c3d-125">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="52c3d-126">Syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="52c3d-126">Query Expression Syntax</span></span>  
 <span data-ttu-id="52c3d-127">Certains des opérateurs de requête standard les plus fréquemment utilisés ont une syntaxe de mot clé C# et Visual Basic Language dédiée qui leur permet d’être appelés dans le cadre d’une *expression*de *requête* .</span><span class="sxs-lookup"><span data-stu-id="52c3d-127">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="52c3d-128">Pour plus d’informations sur les opérateurs de requête standard qui ont des mots clés dédiés et sur leurs syntaxes correspondantes, consultez [Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="52c3d-128">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="52c3d-129">Extension des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="52c3d-129">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="52c3d-130">Vous pouvez augmenter l’ensemble d’opérateurs de requête standard en créant des méthodes spécifiques au domaine appropriées pour votre domaine ou technologie cible.</span><span class="sxs-lookup"><span data-stu-id="52c3d-130">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="52c3d-131">Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires, tels que l’évaluation à distance, la traduction des requêtes et l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="52c3d-131">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="52c3d-132">Pour obtenir un exemple, consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="52c3d-132">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52c3d-133">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="52c3d-133">Related Sections</span></span>  
 <span data-ttu-id="52c3d-134">Les liens suivants vous permettent d’accéder à des articles qui fournissent des informations supplémentaires sur les différents opérateurs de requête standard en fonction de leur fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="52c3d-134">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="52c3d-135">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-135">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="52c3d-136">Opérations ensemblistes (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-136">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="52c3d-137">Filtrage des données (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-137">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="52c3d-138">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-138">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="52c3d-139">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-139">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="52c3d-140">Partitionnement des données (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-140">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="52c3d-141">Opérations de jointure (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-141">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="52c3d-142">Regroupement de données (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-142">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="52c3d-143">Opérations de génération (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-143">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="52c3d-144">Opérations d’égalité (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-144">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="52c3d-145">Opérations d’élément (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-145">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="52c3d-146">Conversion des types de données (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-146">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="52c3d-147">Opérations de concaténation (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-147">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="52c3d-148">Opérations d’agrégation (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-148">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="52c3d-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52c3d-149">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="52c3d-150">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-150">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="52c3d-151">Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-151">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="52c3d-152">Classification des opérateurs de requête standard en fonction de leur mode d’exécution (C#)</span><span class="sxs-lookup"><span data-stu-id="52c3d-152">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="52c3d-153">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="52c3d-153">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
