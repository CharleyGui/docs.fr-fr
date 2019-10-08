---
title: 'Procédure : Faire référence à l’instance actuelle d’un objet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005655"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Procédure : Faire référence à l’instance actuelle d’un objet (Visual Basic)
L' *instance actuelle* d’un objet est l’instance dans laquelle le code est en cours d’exécution.  
  
 Vous utilisez le mot clé `Me` pour faire référence à l’instance actuelle.  
  
### <a name="to-refer-to-the-current-instance"></a>Pour faire référence à l’instance actuelle  
  
- Utilisez le mot clé `Me` dans lequel vous utiliseriez normalement le nom d’une variable objet.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Bien que `Me` se comporte comme une variable objet, vous ne pouvez pas le déclarer ou lui affecter n’importe quoi. `Me` fait toujours référence à l’instance actuelle.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
