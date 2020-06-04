---
title: La variable de portée '<variable>' masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400394"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="c789a-102">La variable de portée '\<variable>' masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="c789a-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="c789a-103">Un nom de variable de portée spécifié dans une `Select` `From` clause,, `Aggregate` ou `Let` est un doublon du nom d’une variable de portée déjà spécifiée dans la requête, ou du nom d’une variable déclarée implicitement par la requête, par exemple un nom de champ ou le nom d’une fonction d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="c789a-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="c789a-104">**ID d’erreur :** BC36633</span><span class="sxs-lookup"><span data-stu-id="c789a-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c789a-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c789a-105">To correct this error</span></span>  
  
- <span data-ttu-id="c789a-106">Vérifiez que toutes les variables de plage dans une étendue de requête particulière ont des noms uniques.</span><span class="sxs-lookup"><span data-stu-id="c789a-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="c789a-107">Vous pouvez placer une requête entre parenthèses pour vous assurer que les requêtes imbriquées ont une étendue unique.</span><span class="sxs-lookup"><span data-stu-id="c789a-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c789a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c789a-108">See also</span></span>

- [<span data-ttu-id="c789a-109">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c789a-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c789a-110">From, clause</span><span class="sxs-lookup"><span data-stu-id="c789a-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="c789a-111">Clause let</span><span class="sxs-lookup"><span data-stu-id="c789a-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="c789a-112">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="c789a-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="c789a-113">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="c789a-113">Select Clause</span></span>](../queries/select-clause.md)
