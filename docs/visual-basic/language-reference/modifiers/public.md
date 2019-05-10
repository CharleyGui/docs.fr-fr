---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0b8c31facc3605ff5a77aecf7b11456b33fbab72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647748"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Spécifie ne qu’aucune restriction d’accès à un ou plusieurs éléments de programmation déclarés.  
  
## <a name="remarks"></a>Notes  
 Si vous publiez un composant ou un ensemble de composants, tels qu’une bibliothèque de classes, vous souhaitez généralement les éléments de programmation accessibles par tout code qui interagit avec votre assembly. Pour octroyer cet accès illimité sur un élément, vous pouvez le déclarer avec `Public`.  
  
 L’accès public est le niveau normal pour un élément de programmation lorsque vous n’avez pas besoin de restreindre l’accès. Notez que le niveau d’accès d’un élément déclaré dans une interface, un module, une classe ou une structure par défaut est `Public` si vous ne déclarez pas une dans le cas contraire.  
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `Public` uniquement au niveau du module, interface ou espace de noms. Cela signifie que le contexte de déclaration pour un `Public` élément doit être un fichier source, un espace de noms, un module, une classe ou une structure et ne peut pas être une procédure.  
  
## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Tout le code qui peut accéder à un module, une classe ou une structure peut accéder à ses `Public` éléments.  
  
- **Accès par défaut.** Les variables locales à l’intérieur d’une procédure reviennent par défaut pour l’accès public et vous ne pouvez pas utiliser n’importe quel modificateur d’accès sur ces derniers.  
  
- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour obtenir une comparaison des modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Public` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
