---
title: <type1> <typename> doit implémenter <methodname> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591593"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > ' \<typename > 'doit implémenter' \<methodname > 'pour l’interface' \<interfacename > '
Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure définie par l’interface. Chaque membre de l’interface doit être implémenté.  
  
 **ID d’erreur :** BC30149  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déclarez une procédure avec les mêmes nom et signature que ceux définis dans l’interface. Veillez à inclure au moins l’instruction `End Function` ou `End Sub`.  
  
2. Ajoutez une clause `Implements` à la fin de l’instruction `Function` ou `Sub`. Exemple :  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
