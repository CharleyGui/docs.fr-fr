---
title: group, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713471"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="bbd73-102">group, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="bbd73-102">group clause (C# Reference)</span></span>

<span data-ttu-id="bbd73-103">La clause `group` retourne une séquence d’objets <xref:System.Linq.IGrouping%602> qui contient zéro, un ou plusieurs éléments qui correspondent à la valeur de clé du groupe.</span><span class="sxs-lookup"><span data-stu-id="bbd73-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="bbd73-104">Par exemple, vous pouvez regrouper une séquence de chaînes en fonction de la première lettre de chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="bbd73-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="bbd73-105">Dans ce cas, la première lettre est la clé, elle a le type [char](../builtin-types/char.md) et elle est stockée dans la propriété `Key` de chaque objet <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="bbd73-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="bbd73-106">Le compilateur déduit le type de la clé.</span><span class="sxs-lookup"><span data-stu-id="bbd73-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="bbd73-107">Vous pouvez terminer une expression de requête avec une clause `group`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bbd73-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="bbd73-108">Si vous souhaitez effectuer des opérations de requête supplémentaires sur chaque groupe, vous pouvez spécifier un identificateur temporaire en utilisant le mot clé contextuel [into](into.md).</span><span class="sxs-lookup"><span data-stu-id="bbd73-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="bbd73-109">Quand vous utilisez `into`, vous devez continuer la requête et finalement la terminer avec une instruction `select` ou une autre clause `group`, comme illustré dans l’extrait suivant :</span><span class="sxs-lookup"><span data-stu-id="bbd73-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="bbd73-110">Des exemples d’utilisation plus complets de `group` avec et sans `into` sont fournis dans la section Exemple de cet article.</span><span class="sxs-lookup"><span data-stu-id="bbd73-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="bbd73-111">Énumération des résultats d’une requête de groupe</span><span class="sxs-lookup"><span data-stu-id="bbd73-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="bbd73-112">Étant donné que les objets <xref:System.Linq.IGrouping%602> générés par une requête `group` sont essentiellement une liste de listes, vous devez utiliser une boucle [foreach](foreach-in.md) imbriquée pour accéder aux éléments dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="bbd73-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="bbd73-113">La boucle externe itère les clés de groupe, et la boucle interne itère chaque élément dans le groupe proprement dit.</span><span class="sxs-lookup"><span data-stu-id="bbd73-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="bbd73-114">Un groupe peut avoir une clé mais pas d’éléments.</span><span class="sxs-lookup"><span data-stu-id="bbd73-114">A group may have a key but no elements.</span></span> <span data-ttu-id="bbd73-115">Voici la boucle `foreach` qui exécute la requête dans les exemples de code précédents :</span><span class="sxs-lookup"><span data-stu-id="bbd73-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="bbd73-116">Types de clés</span><span class="sxs-lookup"><span data-stu-id="bbd73-116">Key types</span></span>

<span data-ttu-id="bbd73-117">Les clés de groupes peuvent être de tout type, comme une chaîne, un type numérique intégré, ou un type nommé ou un type anonyme défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bbd73-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="bbd73-118">Regroupement par chaîne</span><span class="sxs-lookup"><span data-stu-id="bbd73-118">Grouping by string</span></span>

<span data-ttu-id="bbd73-119">Les exemples de code précédents utilisaient un `char`.</span><span class="sxs-lookup"><span data-stu-id="bbd73-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="bbd73-120">On aurait facilement pu spécifier une clé de chaîne à la place, par exemple le nom de famille complet :</span><span class="sxs-lookup"><span data-stu-id="bbd73-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="bbd73-121">Regroupement par valeur booléenne</span><span class="sxs-lookup"><span data-stu-id="bbd73-121">Grouping by bool</span></span>

<span data-ttu-id="bbd73-122">L’exemple suivant illustre l’utilisation d’une valeur booléenne pour une clé afin de répartir les résultats en deux groupes.</span><span class="sxs-lookup"><span data-stu-id="bbd73-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="bbd73-123">Notez que la valeur est générée par une sous-expression dans la clause `group`.</span><span class="sxs-lookup"><span data-stu-id="bbd73-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="bbd73-124">Regroupement par plage numérique</span><span class="sxs-lookup"><span data-stu-id="bbd73-124">Grouping by numeric range</span></span>

<span data-ttu-id="bbd73-125">L’exemple suivant utilise une expression pour créer des clés de groupes numériques qui représentent une plage de centiles.</span><span class="sxs-lookup"><span data-stu-id="bbd73-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="bbd73-126">Notez l’utilisation de [let](let-clause.md) comme emplacement pratique pour stocker un résultat d’appel de méthode, qui vous évite d’avoir à appeler deux fois la méthode dans la clause `group`.</span><span class="sxs-lookup"><span data-stu-id="bbd73-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="bbd73-127">Pour plus d’informations sur la façon d’utiliser en toute sécurité les méthodes dans les expressions de requête, voir [les exceptions De poignée dans les expressions de requête](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="bbd73-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="bbd73-128">Regroupement par clés composites</span><span class="sxs-lookup"><span data-stu-id="bbd73-128">Grouping by composite keys</span></span>

<span data-ttu-id="bbd73-129">Utilisez une clé composite quand vous souhaitez regrouper des éléments en fonction de plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="bbd73-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="bbd73-130">Vous créez une clé composite en utilisant un type anonyme ou un type nommé pour contenir l’élément clé.</span><span class="sxs-lookup"><span data-stu-id="bbd73-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="bbd73-131">Dans l’exemple suivant, supposons qu’une classe `Person` a été déclarée avec les membres nommés `surname` et `city`.</span><span class="sxs-lookup"><span data-stu-id="bbd73-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="bbd73-132">La clause `group` provoque la création d’un groupe distinct pour chaque ensemble de personnes ayant le même nom de famille et la même ville.</span><span class="sxs-lookup"><span data-stu-id="bbd73-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="bbd73-133">Utilisez un type nommé si vous devez passer la variable de requête à une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="bbd73-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="bbd73-134">Créez une classe spéciale à l’aide de propriétés implémentées automatiquement pour les clés, puis substituez les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbd73-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="bbd73-135">Vous pouvez également utiliser un struct, auquel cas vous n’êtes pas obligé de substituer ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="bbd73-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="bbd73-136">Pour plus d’informations voir [Comment mettre en œuvre une classe légère avec des propriétés auto-mises en œuvre](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) et [Comment interroger les fichiers en double dans un arbre d’annuaire](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="bbd73-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="bbd73-137">Ce dernier article contient un exemple de code qui montre comment utiliser une clé composite avec un type nommé.</span><span class="sxs-lookup"><span data-stu-id="bbd73-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="bbd73-138"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bbd73-138">Example</span></span>

<span data-ttu-id="bbd73-139">L’exemple suivant montre le modèle standard pour organiser des données sources en groupes quand aucune logique de requête supplémentaire n’est appliquée aux groupes.</span><span class="sxs-lookup"><span data-stu-id="bbd73-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="bbd73-140">Il s’agit alors d’un regroupement sans continuation.</span><span class="sxs-lookup"><span data-stu-id="bbd73-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="bbd73-141">Les éléments du tableau de chaînes sont regroupés en fonction de leur première lettre.</span><span class="sxs-lookup"><span data-stu-id="bbd73-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="bbd73-142">Le résultat de la requête est un type <xref:System.Linq.IGrouping%602> contenant une propriété `Key` publique de type `char` et une collection <xref:System.Collections.Generic.IEnumerable%601> qui contient chaque élément du regroupement.</span><span class="sxs-lookup"><span data-stu-id="bbd73-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="bbd73-143">Le résultat d’une clause `group` est une séquence de séquences.</span><span class="sxs-lookup"><span data-stu-id="bbd73-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="bbd73-144">Ainsi, pour accéder aux différents éléments de chaque groupe retourné, vous devez utiliser une boucle `foreach` imbriquée à l’intérieur de la boucle qui itère les clés de groupe, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bbd73-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="bbd73-145"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bbd73-145">Example</span></span>

<span data-ttu-id="bbd73-146">Cet exemple montre comment exécuter une logique supplémentaire sur les groupes après les avoir créés, à l’aide une *continuation* avec `into`.</span><span class="sxs-lookup"><span data-stu-id="bbd73-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="bbd73-147">Pour plus d’informations, consultez [into](into.md).</span><span class="sxs-lookup"><span data-stu-id="bbd73-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="bbd73-148">L’exemple suivant interroge chaque groupe pour sélectionner uniquement ceux dont la valeur de clé est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="bbd73-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="bbd73-149">Notes </span><span class="sxs-lookup"><span data-stu-id="bbd73-149">Remarks</span></span>

<span data-ttu-id="bbd73-150">Lors de la compilation, les clauses `group` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbd73-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbd73-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbd73-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="bbd73-152">Mots clés de requête</span><span class="sxs-lookup"><span data-stu-id="bbd73-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="bbd73-153">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bbd73-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="bbd73-154">Créer un groupe imbriqué</span><span class="sxs-lookup"><span data-stu-id="bbd73-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="bbd73-155">Regrouper les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="bbd73-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="bbd73-156">Effectuer une sous-requête sur une opération de regroupement</span><span class="sxs-lookup"><span data-stu-id="bbd73-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
