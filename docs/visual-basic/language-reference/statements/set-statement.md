---
title: Set, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583238"
---
# <a name="set-statement-visual-basic"></a>Set, instruction (Visual Basic)
Déclare une procédure de propriété `Set` utilisée pour assigner une valeur à une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Composants  
 `attributelist`  
 Optionnel. Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Facultatif sur au plus une des instructions `Get` et `Set` de cette propriété. Il peut s'agir d'une des valeurs suivantes :  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Requis. Paramètre contenant la nouvelle valeur de la propriété.  
  
 `datatype`  
 Obligatoire si `Option Strict` est `On`. Type de données du paramètre `value`. Le type de données spécifié doit être le même que le type de données de la propriété où cette `Set` instruction est déclarée.  
  
 `statements`  
 Optionnel. Une ou plusieurs instructions qui s’exécutent lorsque la procédure de propriété `Set` est appelée.  
  
 `End Set`  
 Requis. Met fin à la définition de la procédure de propriété `Set`.  
  
## <a name="remarks"></a>Notes  
 Chaque propriété doit avoir une procédure de propriété `Set`, sauf si la propriété est marquée comme `ReadOnly`. La procédure `Set` est utilisée pour définir la valeur de la propriété.  
  
 Visual Basic appelle automatiquement la procédure `Set` d’une propriété lorsqu’une instruction d’assignation fournit une valeur à stocker dans la propriété.  
  
 Visual Basic passe un paramètre à la procédure `Set` au cours des assignations de propriété. Si vous ne fournissez pas de paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`. Le paramètre contient la valeur à assigner à la propriété. En général, cette valeur est stockée dans une variable locale privée et elle est retournée à chaque appel de la procédure `Get`.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures `Get` et `Set` de la propriété entre l' [instruction Property](../../../visual-basic/language-reference/statements/property-statement.md) et l’instruction `End Property`. Elle ne peut pas stocker d’autres éléments que ces procédures. En particulier, il ne peut pas stocker la valeur actuelle de la propriété. Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder. L’approche habituelle consiste à stocker la valeur dans une variable [privée](../../../visual-basic/language-reference/modifiers/private.md) déclarée au même niveau que la propriété. Vous devez définir une procédure `Set` à l’intérieur de la propriété à laquelle elle s’applique.  
  
 La procédure `Set` a comme valeur par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l’instruction `Set`.  
  
## <a name="rules"></a>Règles  
  
- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` ou la procédure `Set`, mais pas les deux. Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Set` `Private`, mais pas `Public`.  
  
     Si vous définissez une propriété `WriteOnly`, la procédure `Set` représente la propriété entière. Vous ne pouvez pas déclarer un niveau d’accès différent pour `Set`, car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.  
  
## <a name="behavior"></a>Comportement  
  
- **Retour d’une procédure de propriété.** Lorsque la procédure `Set` retourne au code appelant, l’exécution continue à suivre l’instruction qui a fourni la valeur à stocker.  
  
     les procédures de propriété `Set` peuvent être renvoyées à l’aide de l' [instruction return](../../../visual-basic/language-reference/statements/return-statement.md) ou de l' [instruction Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     Les instructions `Exit Property` et `Return` provoquent une sortie immédiate d’une procédure de propriété. Un nombre quelconque d’instructions `Exit Property` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Property` et `Return`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Set` pour définir la valeur d’une propriété.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Voir aussi

- [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
