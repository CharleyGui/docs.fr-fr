---
title: SkipWhile (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: af722f7aee021f244b411cdc61619b7de3c20607
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866226"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="64757-102">Skip While, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64757-102">Skip While Clause (Visual Basic)</span></span>

<span data-ttu-id="64757-103">Ignore les éléments d’une collection tant qu’une condition spécifiée a la valeur `true`, puis retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="64757-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64757-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64757-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="64757-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="64757-105">Parts</span></span>  
  
|<span data-ttu-id="64757-106">Terme</span><span class="sxs-lookup"><span data-stu-id="64757-106">Term</span></span>|<span data-ttu-id="64757-107">Définition</span><span class="sxs-lookup"><span data-stu-id="64757-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="64757-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="64757-108">Required.</span></span> <span data-ttu-id="64757-109">Expression qui représente une condition pour laquelle tester des éléments.</span><span class="sxs-lookup"><span data-stu-id="64757-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="64757-110">L’expression doit retourner une `Boolean` valeur ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="64757-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64757-111">Notes</span><span class="sxs-lookup"><span data-stu-id="64757-111">Remarks</span></span>  

 <span data-ttu-id="64757-112">La `Skip While` clause ignore les éléments à partir du début d’un résultat de requête jusqu’à ce que le fourni soit `expression` retourné `false` .</span><span class="sxs-lookup"><span data-stu-id="64757-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="64757-113">Une fois que `expression` retourne `false` , la requête retourne tous les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="64757-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="64757-114">`expression`Est ignoré pour les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="64757-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="64757-115">La clause `Skip While` est différente de la clause `Where` dans la `Where` mesure où la clause peut être utilisée pour exclure tous les éléments d’une requête qui ne respectent pas une condition particulière.</span><span class="sxs-lookup"><span data-stu-id="64757-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="64757-116">La `Skip While` clause exclut les éléments uniquement jusqu’à la première fois que la condition n’est pas satisfaite.</span><span class="sxs-lookup"><span data-stu-id="64757-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="64757-117">La `Skip While` clause est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.</span><span class="sxs-lookup"><span data-stu-id="64757-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="64757-118">Vous pouvez ignorer un nombre spécifique de résultats à partir du début d’un résultat de requête à l’aide de la `Skip` clause.</span><span class="sxs-lookup"><span data-stu-id="64757-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64757-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="64757-119">Example</span></span>  

 <span data-ttu-id="64757-120">L’exemple de code suivant utilise la `Skip While` clause pour ignorer les résultats jusqu’à ce que le premier client du États-Unis soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="64757-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="64757-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64757-121">See also</span></span>

- [<span data-ttu-id="64757-122">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64757-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="64757-123">Requêtes</span><span class="sxs-lookup"><span data-stu-id="64757-123">Queries</span></span>](index.md)
- [<span data-ttu-id="64757-124">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="64757-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="64757-125">From, clause</span><span class="sxs-lookup"><span data-stu-id="64757-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="64757-126">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="64757-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="64757-127">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="64757-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="64757-128">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="64757-128">Where Clause</span></span>](where-clause.md)
