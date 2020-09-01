---
description: let, clause - Référence C#
title: let, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139591"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="e2949-103">let, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="e2949-103">let clause (C# Reference)</span></span>

<span data-ttu-id="e2949-104">Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e2949-104">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="e2949-105">Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="e2949-105">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="e2949-106">Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="e2949-106">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="e2949-107">Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.</span><span class="sxs-lookup"><span data-stu-id="e2949-107">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="e2949-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2949-108">Example</span></span>

<span data-ttu-id="e2949-109">Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="e2949-109">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="e2949-110">Pour créer un type énumérable qui peut lui-même être interrogé.</span><span class="sxs-lookup"><span data-stu-id="e2949-110">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="e2949-111">Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`.</span><span class="sxs-lookup"><span data-stu-id="e2949-111">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="e2949-112">Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="e2949-112">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="e2949-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2949-113">See also</span></span>

- [<span data-ttu-id="e2949-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e2949-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2949-115">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e2949-115">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="e2949-116">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="e2949-116">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="e2949-117">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e2949-117">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="e2949-118">Gérer des exceptions dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="e2949-118">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
