---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415347"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Spécifie qu’un ou plusieurs éléments de programmation déclarés n’ont pas de restrictions d’accès.  
  
## <a name="remarks"></a>Notes  
 Si vous publiez un composant ou un ensemble de composants, par exemple une bibliothèque de classes, vous souhaitez généralement que les éléments de programmation soient accessibles par tout code qui interagit avec votre assembly. Pour conférer un accès illimité à un élément, vous pouvez le déclarer avec `Public` .  
  
 L’accès public est le niveau normal d’un élément de programmation lorsque vous n’avez pas besoin de limiter l’accès à celui-ci. Notez que le niveau d’accès d’un élément déclaré dans une interface, un module, une classe ou une structure est défini par défaut sur `Public` si vous ne le déclarez pas dans le cas contraire.  
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `Public` uniquement au niveau du module, de l’interface ou de l’espace de noms. Cela signifie que le contexte de déclaration pour un `Public` élément doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure, et ne peut pas être une procédure.  
  
## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Tout le code qui peut accéder à un module, une classe ou une structure peut accéder à ses `Public` éléments.  
  
- **Accès par défaut.** Les variables locales à l’intérieur d’une procédure utilisent par défaut un accès public, et vous ne pouvez pas utiliser de modificateurs d’accès.  
  
- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Public` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../statements/class-statement.md)  
  
 [Const (instruction)](../statements/const-statement.md)  
  
 [Declare Statement](../statements/declare-statement.md)  
  
 [Delegate, instruction](../statements/delegate-statement.md)  
  
 [Dim (instruction)](../statements/dim-statement.md)  
  
 [Enum (instruction)](../statements/enum-statement.md)  
  
 [Event, instruction](../statements/event-statement.md)  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Interface (instruction)](../statements/interface-statement.md)  
  
 [Module, instruction](../statements/module-statement.md)  
  
 [Operator Statement](../statements/operator-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Structure, instruction](../statements/structure-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Protect](protected.md)
- [Contact](friend.md)
- [Privé](private.md)
- [Protégé privé](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
