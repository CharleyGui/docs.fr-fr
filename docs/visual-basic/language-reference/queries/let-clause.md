---
title: Let (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 4bf832651d9753c41ee5a02defec4adc55af1ff1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359759"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="f3927-102">Let, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3927-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="f3927-103">Calcule une valeur et l’assigne à une nouvelle variable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="f3927-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3927-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3927-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="f3927-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="f3927-105">Parts</span></span>  
  
|<span data-ttu-id="f3927-106">Terme</span><span class="sxs-lookup"><span data-stu-id="f3927-106">Term</span></span>|<span data-ttu-id="f3927-107">Définition</span><span class="sxs-lookup"><span data-stu-id="f3927-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="f3927-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f3927-108">Required.</span></span> <span data-ttu-id="f3927-109">Alias qui peut être utilisé pour référencer les résultats de l’expression fournie.</span><span class="sxs-lookup"><span data-stu-id="f3927-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="f3927-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f3927-110">Required.</span></span> <span data-ttu-id="f3927-111">Expression qui sera évaluée et assignée à la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f3927-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3927-112">Notes</span><span class="sxs-lookup"><span data-stu-id="f3927-112">Remarks</span></span>  
 <span data-ttu-id="f3927-113">La `Let` clause vous permet de calculer des valeurs pour chaque résultat de la requête et de les référencer à l’aide d’un alias.</span><span class="sxs-lookup"><span data-stu-id="f3927-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="f3927-114">L’alias peut être utilisé dans d’autres clauses, telles que la `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="f3927-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="f3927-115">La `Let` clause vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et substituer l’alias chaque fois que la clause d’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f3927-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="f3927-116">Vous pouvez inclure n’importe quel nombre d' `variable` `expression` affectations et dans la `Let` clause.</span><span class="sxs-lookup"><span data-stu-id="f3927-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="f3927-117">Séparez chaque assignation par une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="f3927-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3927-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3927-118">Example</span></span>  
 <span data-ttu-id="f3927-119">L’exemple de code suivant utilise la `Let` clause pour calculer une remise de 10 pour cent sur les produits.</span><span class="sxs-lookup"><span data-stu-id="f3927-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="f3927-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3927-120">See also</span></span>

- [<span data-ttu-id="f3927-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3927-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f3927-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="f3927-122">Queries</span></span>](index.md)
- [<span data-ttu-id="f3927-123">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="f3927-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="f3927-124">From, clause</span><span class="sxs-lookup"><span data-stu-id="f3927-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="f3927-125">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="f3927-125">Where Clause</span></span>](where-clause.md)
