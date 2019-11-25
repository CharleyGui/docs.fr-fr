---
title: Protected
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
ms.openlocfilehash: 740c998b8a6ccc6798bce37e9b08e408dac7c17d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351300"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.

## <a name="remarks"></a>Notes

Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element. However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code. In such a case, you want the element to be accessible both from the base class and from all derived classes. To limit access to an element in this manner, you can declare it with `Protected`.

> [!NOTE]
> The `Protected` access modifier can be combined with two other modifiers:
>
> - The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.
> - The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.

## <a name="rules"></a>Règles

**Declaration Context.** You can use `Protected` only at the class level. This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.

## <a name="behavior"></a>Comportement

- **Access Level.** All code in a class can access its elements. Code in any class that derives from a base class can access all the `Protected` elements of the base class. This is true for all generations of derivation. This means that a class can access `Protected` elements of the base class of the base class, and so on.

     Protected access is not a superset or subset of friend access.

- **Access Modifiers.** The keywords that specify access level are called *access modifiers*. For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Le modificateur `Protected` peut être utilisé dans les contextes suivants :

- [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
