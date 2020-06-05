---
title: 'Guide pratique : passer des procédures à une autre procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 36f623068372614ae034a8a7b31bffb7496f98b1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410693"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Comment : passer des procédures à une autre procédure en Visual Basic
Cet exemple montre comment utiliser des délégués pour passer une procédure à une autre procédure.  
  
 Un délégué est un type que vous pouvez utiliser comme tout autre type dans Visual Basic. L' `AddressOf` opérateur retourne un objet délégué lorsqu’il est appliqué à un nom de procédure.  
  
 Cet exemple contient une procédure avec un paramètre délégué qui peut prendre une référence à une autre procédure, obtenue avec l' `AddressOf` opérateur.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Créer le délégué et les procédures de correspondance  
  
1. Créez un délégué nommé `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Créez une procédure nommée `AddNumbers` avec des paramètres et une valeur de retour qui correspondent à ceux de `MathOperator` , afin que les signatures correspondent.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Créez une procédure nommée `SubtractNumbers` avec une signature qui correspond à `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Créez une procédure nommée `DelegateTest` qui accepte un délégué comme paramètre.  
  
     Cette procédure peut accepter une référence à `AddNumbers` ou `SubtractNumbers` , car leurs signatures correspondent à la `MathOperator` signature.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Créez une procédure nommée `Test` qui appelle `DelegateTest` une seule fois avec le délégué pour `AddNumbers` en tant que paramètre, et à nouveau avec le délégué pour `SubtractNumbers` en tant que paramètre.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Lorsque `Test` est appelé, il affiche tout d’abord le résultat de `AddNumbers` Status sur `5` et `3` , qui est 8. Le résultat de `SubtractNumbers` Status sur `9` et `3` est affiché, ce qui correspond à 6.  
  
## <a name="see-also"></a>Voir aussi

- [Délégués](index.md)
- [AddressOf, opérateur](../../../language-reference/operators/addressof-operator.md)
- [Delegate, instruction](../../../language-reference/statements/delegate-statement.md)
- [Comment : appeler une méthode déléguée](how-to-invoke-a-delegate-method.md)
