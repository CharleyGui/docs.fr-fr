---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: d67f0e71dbdbf97420ec5b5ba4b6f06acfba1bd9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874616"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>Une instruction 'Class' doit se terminer par une 'End Class' correspondante

`Class` est utilisé pour initier un `Class` bloc. il ne peut donc apparaître qu’au début du bloc, avec une instruction correspondante qui `End Class` termine le bloc. Soit vous avez une instruction redondante `Class` , soit vous n’avez pas terminé votre `Class` bloc avec `End Class` .  
  
 **ID d’erreur :** BC30481  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Recherchez et supprimez l’instruction `Class` inutile.  
  
- Conclut le `Class` bloc avec un correspondant `End Class` .  
  
## <a name="see-also"></a>Voir aussi

- [End ( \<keyword> instruction)](../statements/end-keyword-statement.md)
- [Class (instruction)](../statements/class-statement.md)
