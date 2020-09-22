---
title: Take While (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869656"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="9945d-102">Take While, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9945d-102">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="9945d-103">Inclut les éléments d’une collection tant qu’une condition spécifiée a la valeur `true` et ignore les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="9945d-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9945d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9945d-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9945d-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="9945d-105">Parts</span></span>  
  
|<span data-ttu-id="9945d-106">Terme</span><span class="sxs-lookup"><span data-stu-id="9945d-106">Term</span></span>|<span data-ttu-id="9945d-107">Définition</span><span class="sxs-lookup"><span data-stu-id="9945d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="9945d-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9945d-108">Required.</span></span> <span data-ttu-id="9945d-109">Expression qui représente une condition pour laquelle tester des éléments.</span><span class="sxs-lookup"><span data-stu-id="9945d-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="9945d-110">L’expression doit retourner une `Boolean` valeur ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9945d-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9945d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9945d-111">Remarks</span></span>  

 <span data-ttu-id="9945d-112">La `Take While` clause comprend des éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` retourne fourni `false` .</span><span class="sxs-lookup"><span data-stu-id="9945d-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="9945d-113">Une fois le `expression` retourné `false` , la requête contourne tous les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="9945d-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="9945d-114">`expression`Est ignoré pour les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="9945d-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="9945d-115">La clause `Take While` est différente de la clause `Where` dans la `Where` mesure où la clause peut être utilisée pour inclure tous les éléments d’une requête qui remplissent une condition particulière.</span><span class="sxs-lookup"><span data-stu-id="9945d-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="9945d-116">La `Take While` clause comprend uniquement des éléments jusqu’à la première fois que la condition n’est pas satisfaite.</span><span class="sxs-lookup"><span data-stu-id="9945d-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="9945d-117">La `Take While` clause est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.</span><span class="sxs-lookup"><span data-stu-id="9945d-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9945d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="9945d-118">Example</span></span>  

 <span data-ttu-id="9945d-119">L’exemple de code suivant utilise la `Take While` clause pour récupérer les résultats jusqu’à ce que le premier client sans ordre soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="9945d-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9945d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9945d-120">See also</span></span>

- [<span data-ttu-id="9945d-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9945d-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9945d-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="9945d-122">Queries</span></span>](index.md)
- [<span data-ttu-id="9945d-123">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="9945d-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="9945d-124">From, clause</span><span class="sxs-lookup"><span data-stu-id="9945d-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="9945d-125">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="9945d-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="9945d-126">SkipWhile (clause)</span><span class="sxs-lookup"><span data-stu-id="9945d-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="9945d-127">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="9945d-127">Where Clause</span></span>](where-clause.md)
