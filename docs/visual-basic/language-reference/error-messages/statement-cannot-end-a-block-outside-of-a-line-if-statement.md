---
title: L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 5e75c29e57a9c04c66e6bca79d99bb18c513f667
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870744"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="ffef6-102">L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne</span><span class="sxs-lookup"><span data-stu-id="ffef6-102">Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="ffef6-103">Une instruction sur une seule ligne `If` contient plusieurs instructions séparées par des signes deux-points ( :), l’une d’elles étant une `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If` .</span><span class="sxs-lookup"><span data-stu-id="ffef6-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="ffef6-104">Les instructions sur une seule ligne `If` n’utilisent pas l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="ffef6-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="ffef6-105">**ID d’erreur :** BC32005</span><span class="sxs-lookup"><span data-stu-id="ffef6-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffef6-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ffef6-106">To correct this error</span></span>  
  
- <span data-ttu-id="ffef6-107">Déplacez l’instruction sur une seule ligne à l' `If` extérieur du bloc de contrôle qui contient l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="ffef6-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffef6-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffef6-108">See also</span></span>

- [<span data-ttu-id="ffef6-109">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="ffef6-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
