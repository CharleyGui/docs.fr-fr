---
title: <type1><typename> doit implémenter <methodname> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408495"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>\<typename> doit implémenter \<methodname> pour l’interface \<interfacename>
Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure définie par l’interface. Chaque membre de l’interface doit être implémenté.  
  
 **ID d’erreur :** BC30149  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déclarez une procédure avec les mêmes nom et signature que ceux définis dans l’interface. Veillez à inclure au moins l' `End Function` `End Sub` instruction ou.  
  
2. Ajoutez une `Implements` clause à la fin de l' `Function` `Sub` instruction ou. Par exemple :  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Implements, instruction](../statements/implements-statement.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
