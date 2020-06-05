---
title: L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400316"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="d5c18-102">L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne</span><span class="sxs-lookup"><span data-stu-id="d5c18-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="d5c18-103">Une instruction sur une seule ligne `If` contient plusieurs instructions séparées par des signes deux-points ( :), l’une d’elles étant une `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If` .</span><span class="sxs-lookup"><span data-stu-id="d5c18-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="d5c18-104">Les instructions sur une seule ligne `If` n’utilisent pas l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="d5c18-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="d5c18-105">**ID d’erreur :** BC32005</span><span class="sxs-lookup"><span data-stu-id="d5c18-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5c18-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d5c18-106">To correct this error</span></span>  
  
- <span data-ttu-id="d5c18-107">Déplacez l’instruction sur une seule ligne à l' `If` extérieur du bloc de contrôle qui contient l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="d5c18-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c18-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c18-108">See also</span></span>

- [<span data-ttu-id="d5c18-109">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="d5c18-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
