---
title: L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161333"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="712b3-102">BC32005 : l’instruction ne peut pas terminer un bloc en dehors d’une instruction’If’d’une ligne</span><span class="sxs-lookup"><span data-stu-id="712b3-102">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="712b3-103">Une instruction sur une seule ligne `If` contient plusieurs instructions séparées par des signes deux-points ( :), l’une d’elles étant une `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If` .</span><span class="sxs-lookup"><span data-stu-id="712b3-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="712b3-104">Les instructions sur une seule ligne `If` n’utilisent pas l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="712b3-104">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="712b3-105">**ID d’erreur :** BC32005</span><span class="sxs-lookup"><span data-stu-id="712b3-105">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="712b3-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="712b3-106">To correct this error</span></span>

- <span data-ttu-id="712b3-107">Déplacez l’instruction sur une seule ligne à l' `If` extérieur du bloc de contrôle qui contient l' `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="712b3-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="712b3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="712b3-108">See also</span></span>

- [<span data-ttu-id="712b3-109">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="712b3-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
