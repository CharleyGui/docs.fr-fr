---
title: Take While, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004677"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="be06a-102">Take While, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be06a-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="be06a-103">Inclut les éléments d’une collection tant qu’une condition spécifiée a la valeur `true` et ignore les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="be06a-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be06a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be06a-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="be06a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="be06a-105">Parts</span></span>  
  
|<span data-ttu-id="be06a-106">Terme</span><span class="sxs-lookup"><span data-stu-id="be06a-106">Term</span></span>|<span data-ttu-id="be06a-107">Définition</span><span class="sxs-lookup"><span data-stu-id="be06a-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="be06a-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="be06a-108">Required.</span></span> <span data-ttu-id="be06a-109">Expression qui représente une condition pour laquelle tester des éléments.</span><span class="sxs-lookup"><span data-stu-id="be06a-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="be06a-110">L’expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu’une `Integer` à évaluer en tant que `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="be06a-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be06a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="be06a-111">Remarks</span></span>  
 <span data-ttu-id="be06a-112">La clause `Take While` comprend des éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` fourni retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="be06a-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="be06a-113">Une fois le `expression` retourné `false`, la requête contourne tous les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="be06a-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="be06a-114">La `expression` est ignorée pour les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="be06a-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="be06a-115">La clause `Take While` est différente de la clause `Where` dans la mesure où la clause `Where` peut être utilisée pour inclure tous les éléments d’une requête qui remplissent une condition particulière.</span><span class="sxs-lookup"><span data-stu-id="be06a-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="be06a-116">La clause `Take While` comprend uniquement des éléments jusqu’à la première fois que la condition n’est pas satisfaite.</span><span class="sxs-lookup"><span data-stu-id="be06a-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="be06a-117">La clause `Take While` est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.</span><span class="sxs-lookup"><span data-stu-id="be06a-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be06a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="be06a-118">Example</span></span>  
 <span data-ttu-id="be06a-119">L’exemple de code suivant utilise la clause `Take While` pour récupérer les résultats jusqu’à ce que le premier client sans ordre soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="be06a-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="be06a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be06a-120">See also</span></span>

- [<span data-ttu-id="be06a-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be06a-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="be06a-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="be06a-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="be06a-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="be06a-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="be06a-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="be06a-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="be06a-125">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="be06a-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="be06a-126">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="be06a-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="be06a-127">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="be06a-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
