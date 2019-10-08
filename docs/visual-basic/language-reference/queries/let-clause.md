---
title: Let, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004727"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="f20d0-102">Let, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f20d0-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="f20d0-103">Calcule une valeur et l’assigne à une nouvelle variable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="f20d0-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f20d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f20d0-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="f20d0-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f20d0-105">Parts</span></span>  
  
|<span data-ttu-id="f20d0-106">Terme</span><span class="sxs-lookup"><span data-stu-id="f20d0-106">Term</span></span>|<span data-ttu-id="f20d0-107">Définition</span><span class="sxs-lookup"><span data-stu-id="f20d0-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="f20d0-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f20d0-108">Required.</span></span> <span data-ttu-id="f20d0-109">Alias qui peut être utilisé pour référencer les résultats de l’expression fournie.</span><span class="sxs-lookup"><span data-stu-id="f20d0-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="f20d0-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f20d0-110">Required.</span></span> <span data-ttu-id="f20d0-111">Expression qui sera évaluée et assignée à la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f20d0-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f20d0-112">Notes</span><span class="sxs-lookup"><span data-stu-id="f20d0-112">Remarks</span></span>  
 <span data-ttu-id="f20d0-113">La clause `Let` vous permet de calculer des valeurs pour chaque résultat de la requête et de les référencer à l’aide d’un alias.</span><span class="sxs-lookup"><span data-stu-id="f20d0-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="f20d0-114">L’alias peut être utilisé dans d’autres clauses, telles que la clause `Where`.</span><span class="sxs-lookup"><span data-stu-id="f20d0-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="f20d0-115">La clause `Let` vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et remplacer l’alias chaque fois que la clause d’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f20d0-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="f20d0-116">Vous pouvez inclure un nombre quelconque d’assignations `variable` et `expression` dans la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="f20d0-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="f20d0-117">Séparez chaque assignation par une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="f20d0-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f20d0-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="f20d0-118">Example</span></span>  
 <span data-ttu-id="f20d0-119">L’exemple de code suivant utilise la clause `Let` pour calculer une remise de 10% sur les produits.</span><span class="sxs-lookup"><span data-stu-id="f20d0-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="f20d0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f20d0-120">See also</span></span>

- [<span data-ttu-id="f20d0-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f20d0-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f20d0-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="f20d0-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f20d0-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="f20d0-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="f20d0-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="f20d0-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="f20d0-125">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="f20d0-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
