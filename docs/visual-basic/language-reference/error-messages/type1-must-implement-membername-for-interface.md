---
title: <type1><typename> doit implémenter <membername> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 7b74ee3a05000f5d6cd94176b48dea116b647a2a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872177"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>\<typename> doit implémenter \<membername> pour l’interface \<interfacename>

' \<typename> 'doit implémenter' \<membername> 'pour l’interface' \<interfacename> '. La propriété d’implémentation doit avoir des spécificateurs’ReadOnly'/'WriteOnly’correspondants.  
  
 Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure, une propriété ou un événement défini par l’interface. Chaque membre de l’interface doit être implémenté.  
  
 **ID d’erreur :** BC30154  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déclarez un membre avec le même nom et la même signature que ceux définis dans l’interface. Veillez à inclure au moins l' `End Function` `End Sub` instruction, ou `End Property` .  
  
2. Ajoutez une `Implements` clause à la fin de l' `Function` instruction,, `Sub` `Property` ou `Event` . Par exemple :  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Lors de l’implémentation d’une propriété, assurez-vous que `ReadOnly` ou `WriteOnly` est utilisé de la même façon que dans la définition de l’interface.  
  
4. Lors de l’implémentation d’une propriété, déclarez `Get` et des `Set` procédures, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi

- [Implements, instruction](../statements/implements-statement.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
