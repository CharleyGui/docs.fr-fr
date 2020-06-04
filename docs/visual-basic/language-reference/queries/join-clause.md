---
title: Join (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359772"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="6f91a-102">Join, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f91a-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="6f91a-103">Combine deux collections en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="6f91a-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="6f91a-104">L’opération de jointure est basée sur les clés correspondantes et utilise l' `Equals` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6f91a-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f91a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f91a-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="6f91a-106">Éléments</span><span class="sxs-lookup"><span data-stu-id="6f91a-106">Parts</span></span>

<span data-ttu-id="6f91a-107">`element` Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6f91a-107">`element` Required.</span></span> <span data-ttu-id="6f91a-108">Variable de contrôle pour la collection qui est jointe.</span><span class="sxs-lookup"><span data-stu-id="6f91a-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="6f91a-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6f91a-109">Required.</span></span> <span data-ttu-id="6f91a-110">Collection à combiner avec la collection identifiée sur le côté gauche de l' `Join` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6f91a-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="6f91a-111">Une `Join` clause peut être imbriquée dans une autre `Join` clause ou dans une `Group Join` clause.</span><span class="sxs-lookup"><span data-stu-id="6f91a-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="6f91a-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="6f91a-112">Optional.</span></span> <span data-ttu-id="6f91a-113">Une ou plusieurs `Join` clauses supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="6f91a-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="6f91a-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="6f91a-114">Optional.</span></span> <span data-ttu-id="6f91a-115">Une ou plusieurs `Group Join` clauses supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="6f91a-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="6f91a-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="6f91a-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="6f91a-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6f91a-117">Required.</span></span> <span data-ttu-id="6f91a-118">Identifie les clés pour les collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="6f91a-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="6f91a-119">Vous devez utiliser l' `Equals` opérateur pour comparer les clés des collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="6f91a-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="6f91a-120">Vous pouvez combiner des conditions de jointure à l’aide de l' `And` opérateur pour identifier plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="6f91a-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="6f91a-121">`key1`doit provenir de la collection sur le côté gauche de l' `Join` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6f91a-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="6f91a-122">`key2`doit provenir de la collection sur le côté droit de l' `Join` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6f91a-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="6f91a-123">Les clés utilisées dans la condition de jointure peuvent être des expressions qui incluent plus d’un élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="6f91a-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="6f91a-124">Toutefois, chaque expression de clé peut contenir uniquement des éléments de sa collection respective.</span><span class="sxs-lookup"><span data-stu-id="6f91a-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f91a-125">Notes</span><span class="sxs-lookup"><span data-stu-id="6f91a-125">Remarks</span></span>

<span data-ttu-id="6f91a-126">La `Join` clause combine deux collections en fonction des valeurs de clé correspondantes des collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="6f91a-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="6f91a-127">La collection résultante peut contenir n’importe quelle combinaison de valeurs de la collection identifiée sur le côté gauche de l' `Join` opérateur et la collection identifiée dans la `Join` clause.</span><span class="sxs-lookup"><span data-stu-id="6f91a-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="6f91a-128">La requête retourne uniquement les résultats pour lesquels la condition spécifiée par l' `Equals` opérateur est remplie.</span><span class="sxs-lookup"><span data-stu-id="6f91a-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="6f91a-129">Cela équivaut à une `INNER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="6f91a-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="6f91a-130">Vous pouvez utiliser plusieurs `Join` clauses dans une requête pour joindre deux collections ou plus dans une collection unique.</span><span class="sxs-lookup"><span data-stu-id="6f91a-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="6f91a-131">Vous pouvez effectuer une jointure implicite pour combiner des collections sans la `Join` clause.</span><span class="sxs-lookup"><span data-stu-id="6f91a-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="6f91a-132">Pour ce faire, incluez plusieurs `In` clauses dans la `From` clause et spécifiez une `Where` clause qui identifie les clés que vous souhaitez utiliser pour la jointure.</span><span class="sxs-lookup"><span data-stu-id="6f91a-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="6f91a-133">Vous pouvez utiliser la `Group Join` clause pour combiner des collections dans une collection hiérarchique unique.</span><span class="sxs-lookup"><span data-stu-id="6f91a-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="6f91a-134">C’est comme un `LEFT OUTER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="6f91a-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="6f91a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f91a-135">Example</span></span>

<span data-ttu-id="6f91a-136">L’exemple de code suivant effectue une jointure implicite pour combiner une liste de clients avec leurs commandes.</span><span class="sxs-lookup"><span data-stu-id="6f91a-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="6f91a-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f91a-137">Example</span></span>

<span data-ttu-id="6f91a-138">L’exemple de code suivant joint deux collections à l’aide de la `Join` clause.</span><span class="sxs-lookup"><span data-stu-id="6f91a-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="6f91a-139">Cet exemple produira une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6f91a-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="6f91a-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f91a-140">Example</span></span>

<span data-ttu-id="6f91a-141">L’exemple de code suivant joint deux collections à l’aide de la `Join` clause avec deux colonnes clés.</span><span class="sxs-lookup"><span data-stu-id="6f91a-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="6f91a-142">L’exemple produira une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6f91a-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="6f91a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f91a-143">See also</span></span>

- [<span data-ttu-id="6f91a-144">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f91a-144">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6f91a-145">Requêtes</span><span class="sxs-lookup"><span data-stu-id="6f91a-145">Queries</span></span>](index.md)
- [<span data-ttu-id="6f91a-146">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="6f91a-146">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="6f91a-147">From, clause</span><span class="sxs-lookup"><span data-stu-id="6f91a-147">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="6f91a-148">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="6f91a-148">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="6f91a-149">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="6f91a-149">Where Clause</span></span>](where-clause.md)
