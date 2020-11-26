---
description: select, clause - Référence C#
title: select, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89136900"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="672ca-103">select, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="672ca-103">select clause (C# Reference)</span></span>

<span data-ttu-id="672ca-104">Dans une expression de requête, la clause `select` spécifie le type de valeurs qui sont générées quand la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="672ca-104">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="672ca-105">Le résultat est basé sur l’évaluation de toutes les clauses précédentes et sur toutes les expressions de la clause `select` elle-même.</span><span class="sxs-lookup"><span data-stu-id="672ca-105">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="672ca-106">Une expression de requête doit se terminer par une clause `select` ou par une clause [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="672ca-106">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="672ca-107">L’exemple suivant présente une clause `select` simple dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="672ca-107">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="672ca-108">Le type de la séquence générée par la clause `select` détermine le type de la variable de requête `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="672ca-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="672ca-109">Dans le cas le plus simple, la clause `select` spécifie uniquement la variable de portée.</span><span class="sxs-lookup"><span data-stu-id="672ca-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="672ca-110">La séquence retournée contient alors des éléments du même type que la source de données.</span><span class="sxs-lookup"><span data-stu-id="672ca-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="672ca-111">Pour plus d’informations, consultez [relations de types dans les opérations de requête LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="672ca-111">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="672ca-112">Toutefois, la clause `select` fournit également un mécanisme puissant pour transformer (ou *projeter*) les données sources en nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="672ca-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="672ca-113">Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="672ca-113">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="672ca-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="672ca-114">Example</span></span>

<span data-ttu-id="672ca-115">L’exemple suivant affiche l’ensemble des différentes formes que peut prendre une clause `select`.</span><span class="sxs-lookup"><span data-stu-id="672ca-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="672ca-116">Dans chaque requête, notez la relation entre la `select` clause et le type de la *variable de requête* ( `studentQuery1` , `studentQuery2` , etc.).</span><span class="sxs-lookup"><span data-stu-id="672ca-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="672ca-117">Comme indiqué dans `studentQuery8` dans l’exemple précédent, vous pouvez parfois souhaiter que les éléments de la séquence retournée contiennent uniquement un sous-ensemble des propriétés des éléments sources.</span><span class="sxs-lookup"><span data-stu-id="672ca-117">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="672ca-118">En limitant au maximum la séquence retournée, vous pouvez réduire les besoins en ressources mémoire et augmenter la vitesse d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="672ca-118">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="672ca-119">Pour ce faire, créez un type anonyme dans la clause `select` et utilisez un initialiseur d’objet pour l’initialiser avec les propriétés appropriées de l’élément source.</span><span class="sxs-lookup"><span data-stu-id="672ca-119">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="672ca-120">Pour obtenir un exemple de la procédure à suivre, consultez [Initialiseurs d’objet et de collection](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="672ca-120">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="672ca-121">Notes</span><span class="sxs-lookup"><span data-stu-id="672ca-121">Remarks</span></span>

<span data-ttu-id="672ca-122">Au moment de la compilation, la clause `select` traduite en un appel de méthode à l’opérateur de requête standard <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="672ca-122">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="672ca-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="672ca-123">See also</span></span>

- [<span data-ttu-id="672ca-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="672ca-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="672ca-125">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="672ca-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="672ca-126">from, clause</span><span class="sxs-lookup"><span data-stu-id="672ca-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="672ca-127">partial, méthode (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="672ca-127">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="672ca-128">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="672ca-128">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="672ca-129">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="672ca-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="672ca-130">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="672ca-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
