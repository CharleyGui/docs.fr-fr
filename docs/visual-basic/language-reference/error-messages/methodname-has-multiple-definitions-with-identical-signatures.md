---
title: "'<methodname>' a plusieurs définitions comportant des signatures identiques"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 3b397711cc2fb1fd0c1dfd76899b162ab5fc1542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397231"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="f3f8f-102">'\<methodname>' a plusieurs définitions comportant des signatures identiques</span><span class="sxs-lookup"><span data-stu-id="f3f8f-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="f3f8f-103">Une `Function` `Sub` déclaration de procédure ou utilise le même nom de procédure et la même liste d’arguments qu’une déclaration précédente.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="f3f8f-104">L’une des causes possibles est une tentative de surcharge de la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="f3f8f-105">Les procédures surchargées doivent avoir des listes d’arguments différentes.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="f3f8f-106">**ID d’erreur :** BC30269</span><span class="sxs-lookup"><span data-stu-id="f3f8f-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3f8f-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f3f8f-107">To correct this error</span></span>  
  
- <span data-ttu-id="f3f8f-108">Modifiez le nom de la procédure ou la liste d’arguments, ou supprimez la déclaration dupliquée.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f8f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3f8f-109">See also</span></span>

- [<span data-ttu-id="f3f8f-110">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="f3f8f-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="f3f8f-111">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="f3f8f-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
