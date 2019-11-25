---
title: Vue d'ensemble des opérateurs de requête standard
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9660e1d92db87e1ae906b3fd6616a51c8b8715fa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349297"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="3213f-102">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="3213f-103">Les *opérateurs de requête standard* sont les méthodes qui forment le modèle de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="3213f-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="3213f-104">La plupart de ces méthodes fonctionnent sur des séquences, où une séquence est un objet dont le type implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> ou l’interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3213f-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="3213f-105">Les opérateurs de requête standard fournissent des fonctionnalités de requête, dont notamment le filtrage, la projection, l’agrégation, le tri, etc.</span><span class="sxs-lookup"><span data-stu-id="3213f-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="3213f-106">Il existe deux ensembles d’opérateurs de requête standard LINQ, l’un opérant sur des objets de type <xref:System.Collections.Generic.IEnumerable%601> et l’autre sur des objets de type <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3213f-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3213f-107">Les méthodes qui composent chaque ensemble sont des membres statiques des classes <xref:System.Linq.Enumerable> et <xref:System.Linq.Queryable>, respectivement.</span><span class="sxs-lookup"><span data-stu-id="3213f-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="3213f-108">Elles sont définies en tant que *méthodes d’extension* du type sur lequel elles opèrent.</span><span class="sxs-lookup"><span data-stu-id="3213f-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="3213f-109">Cela signifie qu’elles peuvent être appelées à l’aide de la syntaxe de méthode statique ou de la syntaxe de méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="3213f-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="3213f-110">De plus, plusieurs méthodes d’opérateur de requête standard fonctionnent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3213f-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3213f-111">Le type <xref:System.Linq.Enumerable> définit deux de ces méthodes qui fonctionnent toutes deux sur les objets de type <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="3213f-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="3213f-112">Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, vous permettent d’autoriser l’interrogation d’une collection non paramétrée, ou non générique, dans le modèle LINQ.</span><span class="sxs-lookup"><span data-stu-id="3213f-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="3213f-113">Pour cela, elles créent une collection fortement typée d’objets.</span><span class="sxs-lookup"><span data-stu-id="3213f-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="3213f-114">La classe <xref:System.Linq.Queryable> définit deux méthodes similaires, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur les objets de type <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="3213f-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="3213f-115">Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="3213f-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="3213f-116">Les méthodes qui retournent une valeur de singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="3213f-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="3213f-117">Les méthodes qui retournent une séquence diffèrent l’exécution de la requête et retournent un objet énumérable.</span><span class="sxs-lookup"><span data-stu-id="3213f-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="3213f-118">Dans le cas des méthodes qui opèrent sur des collections en mémoire, c’est-à-dire des méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601>, l’objet énumérable retourné capture les arguments passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="3213f-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="3213f-119">Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.</span><span class="sxs-lookup"><span data-stu-id="3213f-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="3213f-120">En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601> n’implémentent aucun comportement d’interrogation, mais créent une arborescence d’expressions qui représente la requête à exécuter.</span><span class="sxs-lookup"><span data-stu-id="3213f-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="3213f-121">Le traitement des requêtes est géré par l’objet <xref:System.Linq.IQueryable%601> source.</span><span class="sxs-lookup"><span data-stu-id="3213f-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="3213f-122">Les appels aux méthodes de requête peuvent être chaînés dans une requête unique, ce qui permet de rendre les requêtes arbitrairement complexes.</span><span class="sxs-lookup"><span data-stu-id="3213f-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="3213f-123">L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.</span><span class="sxs-lookup"><span data-stu-id="3213f-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

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

## <a name="query-expression-syntax"></a><span data-ttu-id="3213f-124">Syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="3213f-124">Query Expression Syntax</span></span>

<span data-ttu-id="3213f-125">Certains des opérateurs de requête standard les plus courants ont une syntaxe de mots clés dédiée des langages C# et Visual Basic, qui permet de les appeler dans le cadre d’une *expression* de *requête*.</span><span class="sxs-lookup"><span data-stu-id="3213f-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="3213f-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3213f-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="3213f-127">Extension des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="3213f-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="3213f-128">Vous pouvez augmenter l’ensemble d’opérateurs de requête standard en créant des méthodes spécifiques au domaine appropriées pour votre domaine ou technologie cible.</span><span class="sxs-lookup"><span data-stu-id="3213f-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="3213f-129">Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires, tels que l’évaluation à distance, la traduction des requêtes et l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="3213f-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="3213f-130">Pour obtenir un exemple, consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="3213f-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3213f-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3213f-131">Related Sections</span></span>

<span data-ttu-id="3213f-132">Les liens suivants renvoient à des rubriques contenant des informations supplémentaires sur les divers opérateurs de requête standard, selon leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3213f-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="3213f-133">Tri des données</span><span class="sxs-lookup"><span data-stu-id="3213f-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)

- [<span data-ttu-id="3213f-134">Set Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)

- [<span data-ttu-id="3213f-135">Filtering Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)

- [<span data-ttu-id="3213f-136">Quantifier Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)

- [<span data-ttu-id="3213f-137">Projection Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)

- [<span data-ttu-id="3213f-138">Partitioning Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)

- [<span data-ttu-id="3213f-139">Join Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)

- [<span data-ttu-id="3213f-140">Grouping Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)

- [<span data-ttu-id="3213f-141">Generation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)

- [<span data-ttu-id="3213f-142">Equality Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)

- [<span data-ttu-id="3213f-143">Element Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)

- [<span data-ttu-id="3213f-144">Converting Data Types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)

- [<span data-ttu-id="3213f-145">Concatenation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)

- [<span data-ttu-id="3213f-146">Aggregation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="3213f-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3213f-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="3213f-148">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="3213f-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="3213f-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3213f-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="3213f-151">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="3213f-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
