---
title: "'<methodname>' a plusieurs définitions comportant des signatures identiques"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: b884220053bbcec633c964a41892bc8df42f41c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602438"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="c8eb3-102">'\<nom_méthode >' a plusieurs définitions comportant des signatures identiques</span><span class="sxs-lookup"><span data-stu-id="c8eb3-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="c8eb3-103">Un `Function` ou `Sub` déclaration de procédure utilise la liste de nom et l’argument de procédure identiques comme une déclaration précédente.</span><span class="sxs-lookup"><span data-stu-id="c8eb3-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="c8eb3-104">Une des causes possibles sont une tentative de surcharge de la procédure d’origine.</span><span class="sxs-lookup"><span data-stu-id="c8eb3-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="c8eb3-105">Procédures surchargées doivent avoir des listes d’arguments différentes.</span><span class="sxs-lookup"><span data-stu-id="c8eb3-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="c8eb3-106">**ID d’erreur :** BC30269</span><span class="sxs-lookup"><span data-stu-id="c8eb3-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8eb3-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c8eb3-107">To correct this error</span></span>  
  
- <span data-ttu-id="c8eb3-108">Modifier le nom de la procédure ou la liste d’arguments, ou supprimez la déclaration en double.</span><span class="sxs-lookup"><span data-stu-id="c8eb3-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8eb3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8eb3-109">See also</span></span>

- [<span data-ttu-id="c8eb3-110">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="c8eb3-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c8eb3-111">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="c8eb3-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
