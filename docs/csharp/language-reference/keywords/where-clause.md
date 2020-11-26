---
description: where, clause - Référence C#
title: where, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141684"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="7c703-103">where, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="7c703-103">where clause (C# Reference)</span></span>

<span data-ttu-id="7c703-104">La clause `where` est utilisée dans une expression de requête pour spécifier les éléments de la source de données qui seront retournés dans l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="7c703-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="7c703-105">Elle applique une condition booléenne (un *prédicat*) à chaque élément source (référencé par la variable de portée) et retourne ceux pour lesquels la condition spécifiée est remplie.</span><span class="sxs-lookup"><span data-stu-id="7c703-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="7c703-106">Une expression de requête unique peut contenir plusieurs clauses `where` et une clause unique peut contenir plusieurs sous-expressions de prédicat.</span><span class="sxs-lookup"><span data-stu-id="7c703-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="7c703-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c703-107">Example</span></span>

<span data-ttu-id="7c703-108">Dans l’exemple suivant, la clause `where` élimine par filtrage tous les nombres excepté ceux inférieurs à cinq.</span><span class="sxs-lookup"><span data-stu-id="7c703-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="7c703-109">Si vous supprimez la clause `where`, tous les nombres de la source de données seront retournés.</span><span class="sxs-lookup"><span data-stu-id="7c703-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="7c703-110">L’expression `num < 5` est le prédicat qui est appliqué à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="7c703-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="7c703-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c703-111">Example</span></span>

<span data-ttu-id="7c703-112">Dans une seule `where` clause, vous pouvez spécifier autant de prédicats que nécessaire à l’aide des [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) opérateurs et [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="7c703-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="7c703-113">Dans l’exemple suivant, la requête spécifie deux prédicats pour sélectionner uniquement les nombres pairs inférieurs à cinq.</span><span class="sxs-lookup"><span data-stu-id="7c703-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="7c703-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c703-114">Example</span></span>

<span data-ttu-id="7c703-115">Une clause `where` peut contenir une ou plusieurs méthodes qui retournent des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="7c703-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="7c703-116">Dans l’exemple suivant, la clause `where` utilise une méthode pour déterminer si la valeur actuelle de la variable de portée est paire ou impaire.</span><span class="sxs-lookup"><span data-stu-id="7c703-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="7c703-117">Notes</span><span class="sxs-lookup"><span data-stu-id="7c703-117">Remarks</span></span>

<span data-ttu-id="7c703-118">La clause `where` est un mécanisme de filtrage.</span><span class="sxs-lookup"><span data-stu-id="7c703-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="7c703-119">Elle peut être placée à presque n’importe quel endroit d’une expression de requête, sauf qu’elle ne peut pas être la première ni la dernière clause.</span><span class="sxs-lookup"><span data-stu-id="7c703-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="7c703-120">Une clause `where` peut apparaître avant ou après une clause [group](group-clause.md) selon que vous devez filtrer les éléments sources avant ou après leur regroupement.</span><span class="sxs-lookup"><span data-stu-id="7c703-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="7c703-121">Si un prédicat spécifié n’est pas valide pour les éléments de la source de données, une erreur de compilation est générée.</span><span class="sxs-lookup"><span data-stu-id="7c703-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="7c703-122">C’est l’un des avantages du contrôle de type fort fourni par LINQ.</span><span class="sxs-lookup"><span data-stu-id="7c703-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="7c703-123">Au moment de la compilation, le mot clé `where` est converti en appel à la méthode d’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c703-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c703-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c703-124">See also</span></span>

- [<span data-ttu-id="7c703-125">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7c703-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="7c703-126">from, clause</span><span class="sxs-lookup"><span data-stu-id="7c703-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="7c703-127">clause SELECT</span><span class="sxs-lookup"><span data-stu-id="7c703-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="7c703-128">Filtrage des données</span><span class="sxs-lookup"><span data-stu-id="7c703-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="7c703-129">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="7c703-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="7c703-130">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="7c703-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
