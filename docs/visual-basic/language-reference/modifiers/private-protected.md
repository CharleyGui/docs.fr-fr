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
# <a name="private-protected-visual-basic"></a>Protégé privé (Visual Basic)

La combinaison de mots clés `Private Protected` est un modificateur d’accès de membre. Un membre `Private Protected` est accessible par tous les membres de sa classe conteneur, ainsi que par les types dérivés de la classe conteneur, mais uniquement s’ils se trouvent dans l’assembly qui le contient.

Vous pouvez spécifier `Private Protected` uniquement sur les membres de classes ; vous ne pouvez pas appliquer de `Private Protected` aux membres d’une structure, car les structures ne peuvent pas être héritées.

Le modificateur d’accès `Private Protected` est pris en charge par Visual Basic 15,5 et versions ultérieures. Pour l’utiliser, vous pouvez ajouter l’élément suivant à votre fichier de projet de Visual Basic (\*. vbproj). Tant que Visual Basic 15,5 ou version ultérieure est installé sur votre système, il vous permet de tirer parti de toutes les fonctionnalités de langage prises en charge par la dernière version du compilateur Visual Basic :

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> Dans Visual Studio, la sélection de l’aide F1 sur `private protected` fournit de l’aide pour [privé](private.md) ou [protégé](protected.md). L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Private Protected` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un élément de `Protected` doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.

## <a name="behavior"></a>Comportement

- **Niveau d’accès.** Tout le code d’une classe peut accéder à ses éléments. Le code d’une classe qui dérive d’une classe de base et est contenu dans le même assembly peut accéder à tous les éléments `Private Protected` de la classe de base. Toutefois, le code d’une classe qui dérive d’une classe de base et qui est contenu dans un assembly différent ne peut pas accéder à la classe de base `Private Protected` éléments.

- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Le modificateur `Private Protected` peut être utilisé dans les contextes suivants :

- [Instruction de classe](../../../visual-basic/language-reference/statements/class-statement.md) d’une classe imbriquée

- [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Déléguer une instruction](../../../visual-basic/language-reference/statements/delegate-statement.md) d’un délégué imbriqué dans une classe

- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md) d’une énumération imbriquée dans une classe

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instruction d’interface](../../../visual-basic/language-reference/statements/interface-statement.md) d’une interface imbriquée dans une classe

- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instruction de structure](../../../visual-basic/language-reference/statements/structure-statement.md) d’une structure imbriquée dans une classe

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
