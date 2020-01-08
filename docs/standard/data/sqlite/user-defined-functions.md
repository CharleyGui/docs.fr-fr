---
title: Fonctions définies par l’utilisateur
ms.date: 12/13/2019
description: Découvrez comment créer des fonctions scalaires et d’agrégation définies par l’utilisateur.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447173"
---
# <a name="user-defined-functions"></a><span data-ttu-id="5cfc9-103">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5cfc9-103">User-defined functions</span></span>

<span data-ttu-id="5cfc9-104">La plupart des bases de données ont un dialecte de procédure SQL que vous pouvez utiliser pour définir vos propres fonctions.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="5cfc9-105">SQLite Toutefois, s’exécute in-process avec votre application.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="5cfc9-106">Au lieu d’avoir à apprendre un nouveau dialecte SQL, vous pouvez simplement utiliser le langage de programmation de votre application.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="5cfc9-107">Fonctions scalaires</span><span class="sxs-lookup"><span data-stu-id="5cfc9-107">Scalar functions</span></span>

<span data-ttu-id="5cfc9-108">Les fonctions scalaires retournent une valeur scalaire unique pour chaque ligne d’une requête.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="5cfc9-109">Définissez de nouvelles fonctions scalaires et remplacez les fonctions intégrées à l’aide de <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="5cfc9-110">Consultez [types de données](types.md) pour obtenir la liste des types de paramètres et de retour pris en charge pour l’argument `func`.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="5cfc9-111">La spécification de l’argument `state` passera cette valeur dans chaque appel de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="5cfc9-112">À utiliser pour éviter les fermetures.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-112">Use this to avoid closures.</span></span>

<span data-ttu-id="5cfc9-113">Spécifiez `isDeterministic` si votre fonction est déterministe pour permettre à SQLite d’utiliser des optimisations supplémentaires lors de la compilation des requêtes.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="5cfc9-114">L’exemple suivant montre comment ajouter une fonction scalaire pour calculer le rayon d’un cylindre.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="5cfc9-115">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="5cfc9-115">Operators</span></span>

<span data-ttu-id="5cfc9-116">Les opérateurs SQLite suivants sont implémentés par les fonctions scalaires correspondantes.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="5cfc9-117">La définition de ces fonctions scalaires dans votre application remplacera le comportement de ces opérateurs.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="5cfc9-118">opérateur</span><span class="sxs-lookup"><span data-stu-id="5cfc9-118">Operator</span></span>          | <span data-ttu-id="5cfc9-119">Fonction</span><span class="sxs-lookup"><span data-stu-id="5cfc9-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="5cfc9-120">X GLOB Y</span><span class="sxs-lookup"><span data-stu-id="5cfc9-120">X GLOB Y</span></span>          | <span data-ttu-id="5cfc9-121">glob (Y, X)</span><span class="sxs-lookup"><span data-stu-id="5cfc9-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="5cfc9-122">X LIKE Y</span><span class="sxs-lookup"><span data-stu-id="5cfc9-122">X LIKE Y</span></span>          | <span data-ttu-id="5cfc9-123">like (Y, X)</span><span class="sxs-lookup"><span data-stu-id="5cfc9-123">like(Y, X)</span></span>    |
| <span data-ttu-id="5cfc9-124">X LIKE O ESCAPE Z</span><span class="sxs-lookup"><span data-stu-id="5cfc9-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="5cfc9-125">like (Y, X, Z)</span><span class="sxs-lookup"><span data-stu-id="5cfc9-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="5cfc9-126">X CORRESPOND À Y</span><span class="sxs-lookup"><span data-stu-id="5cfc9-126">X MATCH Y</span></span>         | <span data-ttu-id="5cfc9-127">match (Y, X)</span><span class="sxs-lookup"><span data-stu-id="5cfc9-127">match(Y, X)</span></span>   |
| <span data-ttu-id="5cfc9-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="5cfc9-128">X REGEXP Y</span></span>        | <span data-ttu-id="5cfc9-129">RegExp (Y, X)</span><span class="sxs-lookup"><span data-stu-id="5cfc9-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="5cfc9-130">L’exemple suivant montre comment définir la fonction RegExp pour activer son opérateur correspondant.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="5cfc9-131">SQLite n’inclut pas d’implémentation par défaut de la fonction RegExp.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="5cfc9-132">Fonctions d’agrégation</span><span class="sxs-lookup"><span data-stu-id="5cfc9-132">Aggregate functions</span></span>

<span data-ttu-id="5cfc9-133">Les fonctions d’agrégation retournent une valeur agrégée unique pour toutes les lignes d’une requête.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="5cfc9-134">Définissez et remplacez les fonctions d’agrégation à l’aide de <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="5cfc9-135">L’argument `seed` spécifie l’état initial du contexte.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="5cfc9-136">Utilisez-le pour éviter également les fermetures.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="5cfc9-137">L’argument `func` est appelé une fois par ligne.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="5cfc9-138">Utilisez le contexte pour accumuler un résultat final.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="5cfc9-139">Retourne le contexte.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-139">Return the context.</span></span> <span data-ttu-id="5cfc9-140">Ce modèle permet au contexte d’être un type valeur ou immuable.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="5cfc9-141">Si aucun `resultSelector` n’est spécifié, l’état final du contexte est utilisé comme résultat.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="5cfc9-142">Cela peut simplifier la définition des fonctions telles que SUM et Count qui n’ont besoin d’incrémenter qu’un nombre pour chaque ligne et de la retourner.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="5cfc9-143">Spécifiez `resultSelector` pour calculer le résultat final à partir du contexte après l’itération dans toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="5cfc9-144">Consultez [types de données](types.md) pour obtenir la liste des types de paramètres pris en charge pour l’argument `func` et les types de retour pour `resultSelector`.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="5cfc9-145">Si votre fonction est déterministe, spécifiez `isDeterministic` pour autoriser SQLite à utiliser des optimisations supplémentaires lors de la compilation des requêtes.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="5cfc9-146">L’exemple suivant définit une fonction d’agrégation pour calculer l’écart type d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="5cfc9-147">Erreurs du</span><span class="sxs-lookup"><span data-stu-id="5cfc9-147">Errors</span></span>

<span data-ttu-id="5cfc9-148">Si une fonction définie par l’utilisateur lève une exception, le message est renvoyé à SQLite.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="5cfc9-149">SQLite déclenchera alors une erreur et Microsoft. Data. sqlite lèvera un SqliteException.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="5cfc9-150">Pour plus d’informations, consultez [Erreurs de base de données](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc9-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="5cfc9-151">Par défaut, l’erreur SQLite code d’erreur est SQLITE_ERROR (ou 1).</span><span class="sxs-lookup"><span data-stu-id="5cfc9-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="5cfc9-152">Toutefois, vous pouvez le modifier en levant une <xref:Microsoft.Data.Sqlite.SqliteException> dans votre fonction avec le <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> souhaité spécifié.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="5cfc9-153">débogage</span><span class="sxs-lookup"><span data-stu-id="5cfc9-153">Debugging</span></span>

<span data-ttu-id="5cfc9-154">SQLite appelle votre implémentation directement.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="5cfc9-155">Cela vous permet d’ajouter des points d’arrêt qui se déclenchent quand SQLite évalue des requêtes.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="5cfc9-156">L’expérience de débogage .NET complète est disponible pour vous aider à créer vos fonctions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5cfc9-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cfc9-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cfc9-157">See also</span></span>

* [<span data-ttu-id="5cfc9-158">Types de données</span><span class="sxs-lookup"><span data-stu-id="5cfc9-158">Data types</span></span>](types.md)
* [<span data-ttu-id="5cfc9-159">SQLite fonctions principales</span><span class="sxs-lookup"><span data-stu-id="5cfc9-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="5cfc9-160">Fonctions d’agrégation SQLite</span><span class="sxs-lookup"><span data-stu-id="5cfc9-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)
