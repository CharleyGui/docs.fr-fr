---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351343"
---
# <a name="private-protected-visual-basic"></a>Private Protected (Visual Basic)

La combinaison de mots clés `Private Protected` est un modificateur d’accès de membre. A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.

You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.

The `Private Protected` access modifier is supported by Visual Basic 15.5 and later. To use it, you can add the following element to your Visual Basic project (\*.vbproj) file. As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).

> [!NOTE]
> In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md). The IDE picks the single token under the cursor rather than the compound word.

## <a name="rules"></a>Règles

- **Declaration Context.** You can use `Private Protected` only at the class level. This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.

## <a name="behavior"></a>Comportement

- **Access Level.** All code in a class can access its elements. Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class. However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.

- **Access Modifiers.** The keywords that specify access level are called *access modifiers*. For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Le modificateur `Private Protected` peut être utilisé dans les contextes suivants :

- [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class

- [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class

- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class

- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
