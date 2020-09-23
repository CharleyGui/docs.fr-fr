---
title: "Comment : référencer l'instance actuelle d'un objet"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 64d21fe4aaf6fd34bf880373a7ab3067fb67820e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077057"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Comment : référencer l'instance actuelle d'un objet (Visual Basic)

L' *instance actuelle* d’un objet est l’instance dans laquelle le code est en cours d’exécution.  
  
 Vous utilisez le `Me` mot clé pour faire référence à l’instance actuelle.  
  
### <a name="to-refer-to-the-current-instance"></a>Pour faire référence à l’instance actuelle  
  
- Utilisez le `Me` mot clé dans lequel vous utiliseriez normalement le nom d’une variable objet.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Bien que `Me` se comporte comme une variable objet, vous ne pouvez pas le déclarer ou lui affecter n’importe quoi. `Me` fait toujours référence à l’instance actuelle.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](object-variables.md)
- [Affectation des variables objets](object-variable-assignment.md)
- [Me, My, MyBase et MyClass](../../program-structure/me-my-mybase-and-myclass.md)
