---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929455"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Modificateur d’accès au membre qui spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur propre classe ou d’une classe dérivée.  
  
## <a name="remarks"></a>Notes  
 Parfois, un élément de programmation déclaré dans une classe contient des données sensibles ou du Code restreint, et vous souhaitez limiter l’accès à l’élément. Toutefois, si la classe peut être héritée et que vous vous attendez à une hiérarchie de classes dérivées, il peut être nécessaire que ces classes dérivées accèdent aux données ou au code. Dans ce cas, vous souhaitez que l’élément soit accessible à la fois à partir de la classe de base et à partir de toutes les classes dérivées. Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer `Protected`avec.  

> [!NOTE]
> Le `Protected` modificateur d’accès peut être combiné avec deux autres modificateurs :
>
> - Le modificateur [Friend protégé](protected-friend.md) rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie. 
> - Le modificateur [protected Private](private-protected.md) rend un membre de classe accessible par les types dérivés, mais uniquement au sein de son assembly conteneur.
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `Protected` uniquement au niveau de la classe. Cela signifie que le contexte de Déclaration `Protected` pour un élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.  

## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Tout le code d’une classe peut accéder à ses éléments. Le `Protected` code d’une classe qui dérive d’une classe de base peut accéder à tous les éléments de la classe de base. Cela est vrai pour toutes les générations de dérivation. Cela signifie qu’une classe peut accéder `Protected` aux éléments de la classe de base de la classe de base, et ainsi de suite.  
  
     L’accès protégé n’est pas un sur-ensemble ou un sous-ensemble d’accès Friend.  
  
- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Protected` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
