---
title: let, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173586"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="de751-102">let, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="de751-102">let clause (C# Reference)</span></span>

<span data-ttu-id="de751-103">Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures.</span><span class="sxs-lookup"><span data-stu-id="de751-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="de751-104">Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="de751-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="de751-105">Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="de751-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="de751-106">Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.</span><span class="sxs-lookup"><span data-stu-id="de751-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="de751-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="de751-107">Example</span></span>

<span data-ttu-id="de751-108">Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="de751-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="de751-109">Pour créer un type énumérable qui peut lui-même être interrogé.</span><span class="sxs-lookup"><span data-stu-id="de751-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="de751-110">Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`.</span><span class="sxs-lookup"><span data-stu-id="de751-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="de751-111">Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="de751-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="de751-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de751-112">See also</span></span>

- [<span data-ttu-id="de751-113">Référence C</span><span class="sxs-lookup"><span data-stu-id="de751-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="de751-114">Mots-clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="de751-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="de751-115">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="de751-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="de751-116">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="de751-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="de751-117">Gérer des exceptions dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="de751-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
