---
title: <type1> <typename> doit implémenter <membername> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696896"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > ' \<typename > 'doit implémenter' \<membername > 'pour l’interface' \<interfacename > '
' \<typename > 'doit implémenter' \<membername > 'pour l’interface' \<interfacename > '. La propriété d’implémentation doit avoir des spécificateurs’ReadOnly'/'WriteOnly’correspondants.  
  
 Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure, une propriété ou un événement défini par l’interface. Chaque membre de l’interface doit être implémenté.  
  
 **ID d’erreur :** BC30154  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déclarez un membre avec le même nom et la même signature que ceux définis dans l’interface. Veillez à inclure au moins l’instruction `End Function`, `End Sub` ou `End Property`.  
  
2. Ajoutez une clause `Implements` à la fin de l’instruction `Function`, `Sub`, `Property` ou `Event`. Exemple :  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Lors de l’implémentation d’une propriété, assurez-vous que `ReadOnly` ou `WriteOnly` est utilisé de la même façon que dans la définition de l’interface.  
  
4. Lors de l’implémentation d’une propriété, déclarez les procédures `Get` et `Set`, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
