---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362227"
---
# <a name="private-protected-visual-basic"></a>Protégé privé (Visual Basic)

La combinaison de mots clés `Private Protected` est un modificateur d’accès de membre. Un `Private Protected` membre est accessible par tous les membres de sa classe conteneur, ainsi que par les types dérivés de la classe conteneur, mais uniquement s’ils sont trouvés dans son assembly conteneur.

Vous pouvez spécifier `Private Protected` uniquement sur les membres de classes ; vous ne pouvez pas appliquer `Private Protected` aux membres d’une structure, car les structures ne peuvent pas être héritées.

Le `Private Protected` modificateur d’accès est pris en charge par Visual Basic 15,5 et versions ultérieures. Pour l’utiliser, vous pouvez ajouter l’élément suivant à votre fichier projet de Visual Basic ( \* . vbproj). Tant que Visual Basic 15,5 ou version ultérieure est installé sur votre système, il vous permet de tirer parti de toutes les fonctionnalités de langage prises en charge par la dernière version du compilateur Visual Basic :

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../configure-language-version.md).

> [!NOTE]
> Dans Visual Studio, la sélection de l’aide F1 dans `private protected` fournit de l’aide pour [privé](private.md) ou [protégé](protected.md). L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Private Protected` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.

## <a name="behavior"></a>Comportement

- **Niveau d’accès.** Tout le code d’une classe peut accéder à ses éléments. Le code d’une classe qui dérive d’une classe de base et est contenu dans le même assembly peut accéder à tous les `Private Protected` éléments de la classe de base. Toutefois, le code d’une classe qui dérive d’une classe de base et qui est contenu dans un assembly différent ne peut pas accéder aux éléments de la classe de base `Private Protected` .

- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Le modificateur `Private Protected` peut être utilisé dans les contextes suivants :

- [Instruction de classe](../statements/class-statement.md) d’une classe imbriquée

- [Const (instruction)](../statements/const-statement.md)

- [Declare Statement](../statements/declare-statement.md)

- [Déléguer une instruction](../statements/delegate-statement.md) d’un délégué imbriqué dans une classe

- [Dim (instruction)](../statements/dim-statement.md)

- [Instruction enum](../statements/enum-statement.md) d’une énumération imbriquée dans une classe

- [Event, instruction](../statements/event-statement.md)

- [Function (instruction)](../statements/function-statement.md)

- [Instruction d’interface](../statements/interface-statement.md) d’une interface imbriquée dans une classe

- [Property Statement](../statements/property-statement.md)

- [Instruction de structure](../statements/structure-statement.md) d’une structure imbriquée dans une classe

- [Sub (instruction)](../statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Public](public.md)
- [Protect](protected.md)
- [Contact](friend.md)
- [Privé](private.md)
- [Protected Friend](./protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
