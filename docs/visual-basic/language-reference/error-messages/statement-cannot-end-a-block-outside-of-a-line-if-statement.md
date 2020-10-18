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
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005 : l’instruction ne peut pas terminer un bloc en dehors d’une instruction’If’d’une ligne

Une instruction sur une seule ligne `If` contient plusieurs instructions séparées par des signes deux-points ( :), l’une d’elles étant une `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If` . Les instructions sur une seule ligne `If` n’utilisent pas l' `End If` instruction.

 **ID d’erreur :** BC32005

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déplacez l’instruction sur une seule ligne à l' `If` extérieur du bloc de contrôle qui contient l' `End If` instruction.

## <a name="see-also"></a>Voir aussi

- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
