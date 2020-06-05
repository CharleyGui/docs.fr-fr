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
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398218"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

Modificateur d’accès au membre qui spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur propre classe ou d’une classe dérivée.

## <a name="remarks"></a>Notes

Parfois, un élément de programmation déclaré dans une classe contient des données sensibles ou du Code restreint, et vous souhaitez limiter l’accès à l’élément. Toutefois, si la classe peut être héritée et que vous vous attendez à une hiérarchie de classes dérivées, il peut être nécessaire que ces classes dérivées accèdent aux données ou au code. Dans ce cas, vous souhaitez que l’élément soit accessible à la fois à partir de la classe de base et à partir de toutes les classes dérivées. Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer avec `Protected` .

> [!NOTE]
> Le `Protected` modificateur d’accès peut être combiné avec deux autres modificateurs :
>
> - Le modificateur [Friend protégé](protected-friend.md) rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie.
> - Le modificateur [protected Private](private-protected.md) rend un membre de classe accessible par les types dérivés, mais uniquement au sein de son assembly conteneur.

## <a name="rules"></a>Règles

**Contexte de déclaration.** Vous pouvez utiliser `Protected` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.

## <a name="behavior"></a>Comportement

- **Niveau d’accès.** Tout le code d’une classe peut accéder à ses éléments. Le code d’une classe qui dérive d’une classe de base peut accéder à tous les `Protected` éléments de la classe de base. Cela est vrai pour toutes les générations de dérivation. Cela signifie qu’une classe peut accéder aux `Protected` éléments de la classe de base de la classe de base, et ainsi de suite.

     L’accès protégé n’est pas un sur-ensemble ou un sous-ensemble d’accès Friend.

- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Le modificateur `Protected` peut être utilisé dans les contextes suivants :

- [Class (instruction)](../statements/class-statement.md)

- [Const (instruction)](../statements/const-statement.md)

- [Declare Statement](../statements/declare-statement.md)

- [Delegate, instruction](../statements/delegate-statement.md)

- [Dim (instruction)](../statements/dim-statement.md)

- [Enum (instruction)](../statements/enum-statement.md)

- [Event, instruction](../statements/event-statement.md)

- [Function (instruction)](../statements/function-statement.md)

- [Interface (instruction)](../statements/interface-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Structure, instruction](../statements/structure-statement.md)

- [Sub (instruction)](../statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Public](public.md)
- [Contact](friend.md)
- [Privé](private.md)
- [Protégé privé](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
