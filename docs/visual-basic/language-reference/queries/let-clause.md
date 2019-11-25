---
title: Let, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350434"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="3455d-102">Let, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3455d-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="3455d-103">Computes a value and assigns it to a new variable within the query.</span><span class="sxs-lookup"><span data-stu-id="3455d-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3455d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3455d-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="3455d-105">Composants</span><span class="sxs-lookup"><span data-stu-id="3455d-105">Parts</span></span>  
  
|<span data-ttu-id="3455d-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3455d-106">Term</span></span>|<span data-ttu-id="3455d-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3455d-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="3455d-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="3455d-108">Required.</span></span> <span data-ttu-id="3455d-109">An alias that can be used to reference the results of the supplied expression.</span><span class="sxs-lookup"><span data-stu-id="3455d-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="3455d-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="3455d-110">Required.</span></span> <span data-ttu-id="3455d-111">An expression that will be evaluated and assigned to the specified variable.</span><span class="sxs-lookup"><span data-stu-id="3455d-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3455d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3455d-112">Remarks</span></span>  
 <span data-ttu-id="3455d-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span><span class="sxs-lookup"><span data-stu-id="3455d-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="3455d-114">The alias can be used in other clauses, such as the `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="3455d-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="3455d-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span><span class="sxs-lookup"><span data-stu-id="3455d-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="3455d-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span><span class="sxs-lookup"><span data-stu-id="3455d-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="3455d-117">Separate each assignment with a comma (,).</span><span class="sxs-lookup"><span data-stu-id="3455d-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3455d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="3455d-118">Example</span></span>  
 <span data-ttu-id="3455d-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span><span class="sxs-lookup"><span data-stu-id="3455d-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="3455d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3455d-120">See also</span></span>

- [<span data-ttu-id="3455d-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3455d-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3455d-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="3455d-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3455d-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="3455d-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3455d-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="3455d-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3455d-125">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="3455d-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
