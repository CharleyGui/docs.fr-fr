---
title: L’argument ’Period’ doit être inférieur ou égal à l’argument ’Life’
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 844192f1168e6fef7906ffc133dcc3b5ba40b42c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087035"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a><span data-ttu-id="db58c-102">L’argument ’Period’ doit être inférieur ou égal à l’argument ’Life’</span><span class="sxs-lookup"><span data-stu-id="db58c-102">Argument 'Period' must be less than or equal to argument 'Life'</span></span>

<span data-ttu-id="db58c-103">La valeur de l’argument `Period` , qui indique la période pendant laquelle l’amortissement de la ressource est calculé, est supérieure à la valeur de l’argument `Life` .</span><span class="sxs-lookup"><span data-stu-id="db58c-103">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db58c-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="db58c-104">To correct this error</span></span>  
  
- <span data-ttu-id="db58c-105">Vérifiez que les arguments `Life` et `Period` sont exprimés dans la même unité.</span><span class="sxs-lookup"><span data-stu-id="db58c-105">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="db58c-106">Par exemple, si `Life` est mesuré en mois, `Period` doit l’être également.</span><span class="sxs-lookup"><span data-stu-id="db58c-106">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db58c-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db58c-107">See also</span></span>

- [<span data-ttu-id="db58c-108">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="db58c-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
