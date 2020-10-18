---
title: <type1><typename> doit implémenter <methodname> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 68c6f65e6be229cc74458fa56fe3d3aa889c18f7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161866"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a>BC30149 : \<type1> ' \<typename> 'doit implémenter' \<methodname> 'pour l’interface' \<interfacename> '

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
