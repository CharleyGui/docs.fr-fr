---
title: orderby, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173573"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="2aa4d-102">orderby, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="2aa4d-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="2aa4d-103">Dans une expression de requête, la clause `orderby` a pour effet de trier la séquence ou la sous-séquence (groupe) retournée par ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="2aa4d-104">Il est possible de spécifier plusieurs clés de façon à effectuer une ou plusieurs opérations de tri secondaire.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="2aa4d-105">Le tri est effectué par le comparateur par défaut du type de l’élément.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="2aa4d-106">L’ordre de tri par défaut est croissant.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-106">The default sort order is ascending.</span></span> <span data-ttu-id="2aa4d-107">Vous pouvez aussi spécifier un comparateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="2aa4d-108">Cependant, sa disponibilité est soumise à l’utilisation d’une syntaxe fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="2aa4d-109">Pour plus d’informations, consultez [Tri des données](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="2aa4d-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="2aa4d-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2aa4d-110">Example</span></span>

<span data-ttu-id="2aa4d-111">Dans l’exemple suivant, la première requête trie les mots par ordre alphabétique à partir de A, tandis que la deuxième requête trie les mêmes mots par ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="2aa4d-112">(Le mot clé `ascending` est la valeur de tri par défaut et peut être omis.)</span><span class="sxs-lookup"><span data-stu-id="2aa4d-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="2aa4d-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2aa4d-113">Example</span></span>

<span data-ttu-id="2aa4d-114">L’exemple suivant effectue un tri principal sur les noms des étudiants, puis un tri secondaire sur leurs prénoms.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="2aa4d-115">Notes </span><span class="sxs-lookup"><span data-stu-id="2aa4d-115">Remarks</span></span>

<span data-ttu-id="2aa4d-116">Au moment de la compilation, la clause `orderby` est traduite en appel à la méthode <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="2aa4d-117">Les différentes clés présentes dans la clause `orderby` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="2aa4d-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="2aa4d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aa4d-118">See also</span></span>

- [<span data-ttu-id="2aa4d-119">Référence C</span><span class="sxs-lookup"><span data-stu-id="2aa4d-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2aa4d-120">Mots-clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2aa4d-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="2aa4d-121">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="2aa4d-121">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="2aa4d-122">group, clause</span><span class="sxs-lookup"><span data-stu-id="2aa4d-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="2aa4d-123">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2aa4d-123">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
