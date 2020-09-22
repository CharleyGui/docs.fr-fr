---
title: Set (instruction)
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
ms.openlocfilehash: b3524769567a56a87184bf916a3e5ccb1fd4fa1c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871750"
---
# <a name="set-statement-visual-basic"></a>Set, instruction (Visual Basic)

Déclare une `Set` procédure de propriété utilisée pour assigner une valeur à une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Éléments  

 `attributelist`  
 Optionnel. Consultez la [liste des attributs](attribute-list.md).  
  
 `accessmodifier`  
 Facultatif sur au plus une des `Get` instructions et `Set` dans cette propriété. Il peut s'agir d'une des méthodes suivantes :  
  
- [Protect](../modifiers/protected.md)  
  
- [Friend](../modifiers/friend.md)  
  
- [Privé](../modifiers/private.md)  
  
- `Protected Friend`  
  
 Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Obligatoire. Paramètre contenant la nouvelle valeur de la propriété.  
  
 `datatype`  
 Obligatoire si `Option Strict` est `On` . Type de données du `value` paramètre. Le type de données spécifié doit être le même que le type de données de la propriété où cette `Set` instruction est déclarée.  
  
 `statements`  
 Optionnel. Une ou plusieurs instructions qui s’exécutent lorsque la `Set` procédure de propriété est appelée.  
  
 `End Set`  
 Obligatoire. Met fin à la définition de la `Set` procédure de propriété.  
  
## <a name="remarks"></a>Notes  

 Chaque propriété doit avoir une `Set` procédure de propriété, sauf si la propriété est marquée `ReadOnly` . La `Set` procédure est utilisée pour définir la valeur de la propriété.  
  
 Visual Basic appelle automatiquement la procédure d’une propriété `Set` lorsqu’une instruction d’assignation fournit une valeur à stocker dans la propriété.  
  
 Visual Basic passe un paramètre à la `Set` procédure lors de l’attribution des propriétés. Si vous ne fournissez pas de paramètre pour `Set` , l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value` . Le paramètre contient la valeur à assigner à la propriété. En général, vous stockez cette valeur dans une variable locale privée et la Retournez chaque fois que la `Get` procédure est appelée.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures et de la propriété `Get` `Set` entre l' [instruction Property](property-statement.md) et l' `End Property` instruction. Elle ne peut pas stocker d’autres éléments que ces procédures. En particulier, il ne peut pas stocker la valeur actuelle de la propriété. Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder. L’approche habituelle consiste à stocker la valeur dans une variable [privée](../modifiers/private.md) déclarée au même niveau que la propriété. Vous devez définir une `Set` procédure à l’intérieur de la propriété à laquelle elle s’applique.  
  
 La `Set` procédure utilise par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l' `Set` instruction.  
  
## <a name="rules"></a>Règles  
  
- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` `Set` procédure ou, mais pas pour les deux. Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend` , vous pouvez déclarer la `Set` procédure `Private` , mais pas `Public` .  
  
     Si vous définissez une `WriteOnly` propriété, la `Set` procédure représente la propriété entière. Vous ne pouvez pas déclarer un niveau d’accès différent pour `Set` , car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.  
  
## <a name="behavior"></a>Comportement  
  
- **Retour d’une procédure de propriété.** Lorsque la `Set` procédure revient au code appelant, l’exécution continue à suivre l’instruction qui a fourni la valeur à stocker.  
  
     `Set` les procédures de propriété peuvent être retournées à l’aide de l' [instruction return](return-statement.md) ou de l' [instruction Exit](exit-statement.md).  
  
     Les `Exit Property` `Return` instructions et provoquent une sortie immédiate d’une procédure de propriété. Un nombre quelconque `Exit Property` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Property` `Return` instructions et.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `Set` instruction pour définir la valeur d’une propriété.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Voir aussi

- [Get, instruction](get-statement.md)
- [Property Statement](property-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Procédures Property](../../programming-guide/language-features/procedures/property-procedures.md)
