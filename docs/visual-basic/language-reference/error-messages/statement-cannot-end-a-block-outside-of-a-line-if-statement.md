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
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>L'instruction ne peut pas terminer un bloc en dehors d'une instruction 'If' d'une ligne

Une instruction sur une seule ligne `If` contient plusieurs instructions séparées par des signes deux-points ( :), l’une d’elles étant une `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If` . Les instructions sur une seule ligne `If` n’utilisent pas l' `End If` instruction.  
  
 **ID d’erreur :** BC32005  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez l’instruction sur une seule ligne à l' `If` extérieur du bloc de contrôle qui contient l' `End If` instruction.  
  
## <a name="see-also"></a>Voir aussi

- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
