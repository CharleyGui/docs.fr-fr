---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163192"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a>BC30481 : l’instruction’class’doit se terminer par un’End Class’correspondant

`Class` est utilisé pour initier un `Class` bloc. il ne peut donc apparaître qu’au début du bloc, avec une instruction correspondante qui `End Class` termine le bloc. Soit vous avez une instruction redondante `Class` , soit vous n’avez pas terminé votre `Class` bloc avec `End Class` .

 **ID d’erreur :** BC30481

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Recherchez et supprimez l’instruction `Class` inutile.

- Conclut le `Class` bloc avec un correspondant `End Class` .

## <a name="see-also"></a>Voir aussi

- [End ( \<keyword> instruction)](../statements/end-keyword-statement.md)
- [Class (instruction)](../statements/class-statement.md)
