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
# <a name="resume-without-error"></a>Reprendre sans gestion d'erreur

Une `Resume` instruction est apparue en dehors du code de gestion des erreurs ou le code a été inséré dans un gestionnaire d’erreurs même si aucune erreur ne s’est produite.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déplacez l' `Resume` instruction dans un gestionnaire d’erreurs ou supprimez-la.  
  
2. Les sauts à des étiquettes ne peuvent pas se produire entre les procédures. par conséquent, recherchez dans la procédure l’étiquette qui identifie le gestionnaire d’erreurs. Si vous trouvez une étiquette en double spécifiée comme cible d’une `GoTo` instruction qui n’est pas une `On Error GoTo` instruction, modifiez l’étiquette de ligne pour qu’elle corresponde à la cible prévue.  
  
## <a name="see-also"></a>Voir aussi

- [Resume, instruction](../statements/resume-statement.md)
- [On Error (instruction)](../statements/on-error-statement.md)
