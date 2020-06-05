---
title: Vue d'ensemble des opérateurs de requête standard
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406779"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="e5104-102">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="e5104-103">Les *opérateurs de requête standard* sont les méthodes qui forment le modèle de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="e5104-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="e5104-104">La plupart de ces méthodes fonctionnent sur des séquences, où une séquence est un objet dont le type implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> ou l’interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="e5104-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="e5104-105">Les opérateurs de requête standard fournissent des fonctionnalités de requête, dont notamment le filtrage, la projection, l’agrégation, le tri, etc.</span><span class="sxs-lookup"><span data-stu-id="e5104-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="e5104-106">Il existe deux ensembles d’opérateurs de requête standard LINQ, l’un opérant sur des objets de type <xref:System.Collections.Generic.IEnumerable%601> et l’autre sur des objets de type <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="e5104-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e5104-107">Les méthodes qui composent chaque ensemble sont des membres statiques des classes <xref:System.Linq.Enumerable> et <xref:System.Linq.Queryable>, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e5104-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="e5104-108">Elles sont définies en tant que *méthodes d’extension* du type sur lequel elles opèrent.</span><span class="sxs-lookup"><span data-stu-id="e5104-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="e5104-109">Cela signifie qu’elles peuvent être appelées à l’aide de la syntaxe de méthode statique ou de la syntaxe de méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="e5104-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="e5104-110">De plus, plusieurs méthodes d’opérateur de requête standard fonctionnent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="e5104-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e5104-111">Le type <xref:System.Linq.Enumerable> définit deux de ces méthodes qui fonctionnent toutes deux sur les objets de type <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="e5104-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="e5104-112">Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, vous permettent d’autoriser l’interrogation d’une collection non paramétrée, ou non générique, dans le modèle LINQ.</span><span class="sxs-lookup"><span data-stu-id="e5104-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="e5104-113">Pour ce faire, ils créent une collection fortement typée d’objets.</span><span class="sxs-lookup"><span data-stu-id="e5104-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="e5104-114">La classe <xref:System.Linq.Queryable> définit deux méthodes similaires, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur les objets de type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="e5104-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="e5104-115">Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="e5104-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="e5104-116">Les méthodes qui retournent une valeur de singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="e5104-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="e5104-117">Les méthodes qui retournent une séquence diffèrent l’exécution de la requête et retournent un objet énumérable.</span><span class="sxs-lookup"><span data-stu-id="e5104-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="e5104-118">Dans le cas des méthodes qui opèrent sur des collections en mémoire, c’est-à-dire des méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601>, l’objet énumérable retourné capture les arguments passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="e5104-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="e5104-119">Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.</span><span class="sxs-lookup"><span data-stu-id="e5104-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="e5104-120">En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601> n’implémentent aucun comportement d’interrogation, mais créent une arborescence d’expressions qui représente la requête à exécuter.</span><span class="sxs-lookup"><span data-stu-id="e5104-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="e5104-121">Le traitement des requêtes est géré par l’objet <xref:System.Linq.IQueryable%601> source.</span><span class="sxs-lookup"><span data-stu-id="e5104-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="e5104-122">Les appels aux méthodes de requête peuvent être chaînés dans une requête unique, ce qui permet de rendre les requêtes arbitrairement complexes.</span><span class="sxs-lookup"><span data-stu-id="e5104-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="e5104-123">L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.</span><span class="sxs-lookup"><span data-stu-id="e5104-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

```vb
Dim sentence = "the quick brown fox jumps over the lazy dog"
' Split the string into individual words to create a collection.
Dim words = sentence.Split(" "c)

Dim query = From word In words
            Group word.ToUpper() By word.Length Into gr = Group
            Order By Length _
            Select Length, GroupedWords = gr

Dim output As New System.Text.StringBuilder
For Each obj In query
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))
    For Each word As String In obj.GroupedWords
        output.AppendLine(word)
    Next
Next

'Display the output
MsgBox(output.ToString())

' This code example produces the following output:
'
' Words of length 3:
' THE
' FOX
' THE
' DOG
' Words of length 4:
' OVER
' LAZY
' Words of length 5:
' QUICK
' BROWN
' JUMPS
```

## <a name="query-expression-syntax"></a><span data-ttu-id="e5104-124">Syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="e5104-124">Query Expression Syntax</span></span>

<span data-ttu-id="e5104-125">Certains des opérateurs de requête standard les plus fréquemment utilisés ont une syntaxe de mot clé C# et Visual Basic Language dédiée qui leur permet d’être appelés dans le cadre d’une *expression*de *requête* .</span><span class="sxs-lookup"><span data-stu-id="e5104-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="e5104-126">Pour plus d’informations sur les opérateurs de requête standard qui ont des mots clés dédiés et leurs syntaxes correspondantes, consultez [syntaxe des expressions de requête pour les opérateurs de requête standard (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e5104-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="e5104-127">Extension des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="e5104-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="e5104-128">Vous pouvez augmenter l’ensemble d’opérateurs de requête standard en créant des méthodes spécifiques au domaine appropriées pour votre domaine ou technologie cible.</span><span class="sxs-lookup"><span data-stu-id="e5104-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="e5104-129">Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires, tels que l’évaluation à distance, la traduction des requêtes et l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="e5104-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="e5104-130">Pour obtenir un exemple, consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5104-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e5104-131">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="e5104-131">Related Sections</span></span>

<span data-ttu-id="e5104-132">Les liens suivants renvoient à des rubriques contenant des informations supplémentaires sur les divers opérateurs de requête standard, selon leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e5104-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="e5104-133">Tri des données</span><span class="sxs-lookup"><span data-stu-id="e5104-133">Sorting Data</span></span>](sorting-data.md)

- [<span data-ttu-id="e5104-134">Opérations de définition (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-134">Set Operations (Visual Basic)</span></span>](set-operations.md)

- [<span data-ttu-id="e5104-135">Filtrage des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-135">Filtering Data (Visual Basic)</span></span>](filtering-data.md)

- [<span data-ttu-id="e5104-136">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-136">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)

- [<span data-ttu-id="e5104-137">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-137">Projection Operations (Visual Basic)</span></span>](projection-operations.md)

- [<span data-ttu-id="e5104-138">Partitionnement des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-138">Partitioning Data (Visual Basic)</span></span>](partitioning-data.md)

- [<span data-ttu-id="e5104-139">Opérations de jointure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-139">Join Operations (Visual Basic)</span></span>](join-operations.md)

- [<span data-ttu-id="e5104-140">Regroupement de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-140">Grouping Data (Visual Basic)</span></span>](grouping-data.md)

- [<span data-ttu-id="e5104-141">Opérations de génération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-141">Generation Operations (Visual Basic)</span></span>](generation-operations.md)

- [<span data-ttu-id="e5104-142">Opérations d’égalité (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-142">Equality Operations (Visual Basic)</span></span>](equality-operations.md)

- [<span data-ttu-id="e5104-143">Opérations d’élément (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-143">Element Operations (Visual Basic)</span></span>](element-operations.md)

- [<span data-ttu-id="e5104-144">Conversion des types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-144">Converting Data Types (Visual Basic)</span></span>](converting-data-types.md)

- [<span data-ttu-id="e5104-145">Opérations de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-145">Concatenation Operations (Visual Basic)</span></span>](concatenation-operations.md)

- [<span data-ttu-id="e5104-146">Opérations d’agrégation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-146">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="e5104-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5104-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="e5104-148">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-148">Introduction to LINQ (Visual Basic)</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="e5104-149">Syntaxe des expressions de requête pour les opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="e5104-150">Classification des opérateurs de requête standard par mode d’exécution (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5104-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="e5104-151">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="e5104-151">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
