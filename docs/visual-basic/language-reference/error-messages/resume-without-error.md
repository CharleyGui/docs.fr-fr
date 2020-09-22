---
title: Reprendre sans gestion d'erreur
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870832"
---
# <a name="resume-without-error"></a><span data-ttu-id="ad287-102">Reprendre sans gestion d'erreur</span><span class="sxs-lookup"><span data-stu-id="ad287-102">Resume without error</span></span>

<span data-ttu-id="ad287-103">Une `Resume` instruction est apparue en dehors du code de gestion des erreurs ou le code a été inséré dans un gestionnaire d’erreurs même si aucune erreur ne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ad287-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad287-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ad287-104">To correct this error</span></span>  
  
1. <span data-ttu-id="ad287-105">Déplacez l' `Resume` instruction dans un gestionnaire d’erreurs ou supprimez-la.</span><span class="sxs-lookup"><span data-stu-id="ad287-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="ad287-106">Les sauts à des étiquettes ne peuvent pas se produire entre les procédures. par conséquent, recherchez dans la procédure l’étiquette qui identifie le gestionnaire d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ad287-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="ad287-107">Si vous trouvez une étiquette en double spécifiée comme cible d’une `GoTo` instruction qui n’est pas une `On Error GoTo` instruction, modifiez l’étiquette de ligne pour qu’elle corresponde à la cible prévue.</span><span class="sxs-lookup"><span data-stu-id="ad287-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad287-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad287-108">See also</span></span>

- [<span data-ttu-id="ad287-109">Resume, instruction</span><span class="sxs-lookup"><span data-stu-id="ad287-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="ad287-110">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="ad287-110">On Error Statement</span></span>](../statements/on-error-statement.md)
