---
title: Join, clause
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
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353262"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="a94eb-102">Join, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a94eb-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="a94eb-103">Combine deux collections en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="a94eb-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="a94eb-104">L’opération de jointure est basée sur les clés correspondantes et utilise l’opérateur `Equals`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="a94eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a94eb-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="a94eb-106">Composants</span><span class="sxs-lookup"><span data-stu-id="a94eb-106">Parts</span></span>

<span data-ttu-id="a94eb-107">`element` (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="a94eb-107">`element` Required.</span></span> <span data-ttu-id="a94eb-108">Variable de contrôle pour la collection qui est jointe.</span><span class="sxs-lookup"><span data-stu-id="a94eb-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="a94eb-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="a94eb-109">Required.</span></span> <span data-ttu-id="a94eb-110">Collection à combiner à la collection identifiée sur le côté gauche de l’opérateur `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="a94eb-111">Une clause `Join` peut être imbriquée dans une autre clause `Join` ou dans une clause `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="a94eb-112">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a94eb-112">Optional.</span></span> <span data-ttu-id="a94eb-113">Une ou plusieurs clauses de `Join` supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="a94eb-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="a94eb-114">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a94eb-114">Optional.</span></span> <span data-ttu-id="a94eb-115">Une ou plusieurs clauses de `Group Join` supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="a94eb-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="a94eb-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="a94eb-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="a94eb-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="a94eb-117">Required.</span></span> <span data-ttu-id="a94eb-118">Identifie les clés pour les collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="a94eb-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="a94eb-119">Vous devez utiliser l’opérateur `Equals` pour comparer les clés des collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="a94eb-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="a94eb-120">Vous pouvez combiner des conditions de jointure à l’aide de l’opérateur `And` pour identifier plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="a94eb-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="a94eb-121">`key1` doit provenir de la collection sur le côté gauche de l’opérateur `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="a94eb-122">`key2` doit provenir de la collection sur le côté droit de l’opérateur `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="a94eb-123">Les clés utilisées dans la condition de jointure peuvent être des expressions qui incluent plus d’un élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="a94eb-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="a94eb-124">Toutefois, chaque expression de clé peut contenir uniquement des éléments de sa collection respective.</span><span class="sxs-lookup"><span data-stu-id="a94eb-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="a94eb-125">Notes</span><span class="sxs-lookup"><span data-stu-id="a94eb-125">Remarks</span></span>

<span data-ttu-id="a94eb-126">La clause `Join` combine deux collections en fonction des valeurs de clé correspondantes des collections qui sont jointes.</span><span class="sxs-lookup"><span data-stu-id="a94eb-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="a94eb-127">La collection résultante peut contenir n’importe quelle combinaison de valeurs de la collection identifiée sur le côté gauche de l’opérateur `Join` et la collection identifiée dans la clause `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="a94eb-128">La requête retourne uniquement les résultats pour lesquels la condition spécifiée par l’opérateur `Equals` est remplie.</span><span class="sxs-lookup"><span data-stu-id="a94eb-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="a94eb-129">Cela équivaut à une `INNER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="a94eb-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="a94eb-130">Vous pouvez utiliser plusieurs clauses `Join` dans une requête pour joindre deux collections ou plus dans une collection unique.</span><span class="sxs-lookup"><span data-stu-id="a94eb-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="a94eb-131">Vous pouvez effectuer une jointure implicite pour combiner des collections sans la clause `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="a94eb-132">Pour ce faire, incluez plusieurs clauses `In` dans votre clause `From` et spécifiez une clause `Where` qui identifie les clés que vous souhaitez utiliser pour la jointure.</span><span class="sxs-lookup"><span data-stu-id="a94eb-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="a94eb-133">Vous pouvez utiliser la clause `Group Join` pour combiner des collections dans une collection hiérarchique unique.</span><span class="sxs-lookup"><span data-stu-id="a94eb-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="a94eb-134">C’est comme un `LEFT OUTER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="a94eb-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="a94eb-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="a94eb-135">Example</span></span>

<span data-ttu-id="a94eb-136">L’exemple de code suivant effectue une jointure implicite pour combiner une liste de clients avec leurs commandes.</span><span class="sxs-lookup"><span data-stu-id="a94eb-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="a94eb-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="a94eb-137">Example</span></span>

<span data-ttu-id="a94eb-138">L’exemple de code suivant joint deux collections à l’aide de la clause `Join`.</span><span class="sxs-lookup"><span data-stu-id="a94eb-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="a94eb-139">Cet exemple produira une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a94eb-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="a94eb-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="a94eb-140">Example</span></span>

<span data-ttu-id="a94eb-141">L’exemple de code suivant joint deux collections à l’aide de la clause `Join` avec deux colonnes clés.</span><span class="sxs-lookup"><span data-stu-id="a94eb-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="a94eb-142">L’exemple produira une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a94eb-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="a94eb-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a94eb-143">See also</span></span>

- [<span data-ttu-id="a94eb-144">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a94eb-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a94eb-145">Requêtes</span><span class="sxs-lookup"><span data-stu-id="a94eb-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a94eb-146">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="a94eb-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="a94eb-147">From (clause)</span><span class="sxs-lookup"><span data-stu-id="a94eb-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="a94eb-148">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="a94eb-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="a94eb-149">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="a94eb-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
