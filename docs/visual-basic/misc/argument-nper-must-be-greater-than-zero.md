---
title: L’argument 'NPer' doit être supérieur à zéro
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 0c2cf0f0000de44e1be796bb2de962b45c1d6969
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368060"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="1e5e3-102">L’argument 'NPer' doit être supérieur à zéro</span><span class="sxs-lookup"><span data-stu-id="1e5e3-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="1e5e3-103">La fonction `NPer` , qui retourne un `Double` spécifiant le nombre de périodes pour une annuité sur la base de versements fixes périodiques et d’un taux d’intérêt fixe, nécessite un argument supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="1e5e3-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e5e3-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1e5e3-104">To correct this error</span></span>  
  
- <span data-ttu-id="1e5e3-105">Vérifiez l’orthographe des arguments dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="1e5e3-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="1e5e3-106">Un nom de variable mal orthographié peut créer implicitement une variable numérique dont la valeur est zéro.</span><span class="sxs-lookup"><span data-stu-id="1e5e3-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="1e5e3-107">Vérifiez les opérations précédentes sur les variables de l’expression, surtout celles passées dans la procédure en tant qu’arguments à partir d’autres procédures.</span><span class="sxs-lookup"><span data-stu-id="1e5e3-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5e3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e5e3-108">See also</span></span>

- [<span data-ttu-id="1e5e3-109">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="1e5e3-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
