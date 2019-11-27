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
# <a name="let-clause-visual-basic"></a><span data-ttu-id="b79cd-102">Let, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b79cd-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="b79cd-103">Calcule une valeur et l’assigne à une nouvelle variable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="b79cd-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b79cd-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="b79cd-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b79cd-105">Parts</span></span>  
  
|<span data-ttu-id="b79cd-106">Terme</span><span class="sxs-lookup"><span data-stu-id="b79cd-106">Term</span></span>|<span data-ttu-id="b79cd-107">Définition</span><span class="sxs-lookup"><span data-stu-id="b79cd-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="b79cd-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="b79cd-108">Required.</span></span> <span data-ttu-id="b79cd-109">Alias qui peut être utilisé pour référencer les résultats de l’expression fournie.</span><span class="sxs-lookup"><span data-stu-id="b79cd-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="b79cd-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="b79cd-110">Required.</span></span> <span data-ttu-id="b79cd-111">Expression qui sera évaluée et assignée à la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b79cd-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b79cd-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b79cd-112">Remarks</span></span>  
 <span data-ttu-id="b79cd-113">La clause `Let` vous permet de calculer des valeurs pour chaque résultat de requête et de les référencer à l’aide d’un alias.</span><span class="sxs-lookup"><span data-stu-id="b79cd-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="b79cd-114">L’alias peut être utilisé dans d’autres clauses, telles que la clause `Where`.</span><span class="sxs-lookup"><span data-stu-id="b79cd-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="b79cd-115">La clause `Let` vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et remplacer l’alias chaque fois que la clause expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b79cd-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="b79cd-116">Vous pouvez inclure n’importe quel nombre de `variable` et `expression` assignations dans la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="b79cd-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="b79cd-117">Séparez chaque assignation par une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="b79cd-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b79cd-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="b79cd-118">Example</span></span>  
 <span data-ttu-id="b79cd-119">L’exemple de code suivant utilise la clause `Let` pour calculer une remise de 10% sur les produits.</span><span class="sxs-lookup"><span data-stu-id="b79cd-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="b79cd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b79cd-120">See also</span></span>

- [<span data-ttu-id="b79cd-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b79cd-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b79cd-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="b79cd-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b79cd-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="b79cd-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b79cd-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="b79cd-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b79cd-125">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="b79cd-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
