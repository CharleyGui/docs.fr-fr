---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: c9dfff99e2634b79ad6b44721f40583d21c9b98e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664135"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Spécifie qu’un élément de programmation déclaré redéclare et masque un élément portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base.

## <a name="remarks"></a>Notes

L’objectif principal d’une occultation (qui est également appelé *masquage par nom*) consiste à conserver la définition de vos membres de classe. La classe de base peut subir un changement qui crée un élément avec le même nom qu’un que vous avez déjà défini. Si cela se produit, le `Shadows` modificateur force références de votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de classe de base.

L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Shadows` uniquement au niveau de classe. Cela signifie que le contexte de déclaration pour un `Shadows` élément doit être une classe et ne peut pas être une fichier source, un espace de noms, un module, une structure ou une procédure.

  Vous pouvez déclarer qu’un seul élément d’occultation dans une instruction de déclaration unique.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shadows` avec `Overloads`, `Overrides`, ou `Static` dans la même déclaration.

- **Types d’éléments.** Vous pouvez occulter tout type d'élément déclaré par un autre type. Si vous masquez une propriété ou procédure avec une autre propriété ou procédure, les paramètres et le type de retour est inutile correspondre à ceux de la propriété de classe de base ou de la procédure.

- **L’accès à.** L’élément occulté dans la classe de base est normalement pas disponible dans la classe dérivée qui l’occulte. Toutefois, les considérations suivantes s’appliquent.

  - Si l’élément d’occultation n’est pas accessible à partir du code faisant référence à ce dernier, la référence est résolue à l’élément occulté. Par exemple, si un `Private` élément occulte un élément de la classe de base, le code qui n’est pas autorisé à accéder à la `Private` élément accède à l’élément de la classe de base à la place.

  - Si vous masquez un élément, vous pouvez toujours accéder à l’élément occulté via un objet déclaré avec le type de la classe de base. Vous pouvez également y accéder via `MyBase`.

Le modificateur `Shadows` peut être utilisé dans les contextes suivants :

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

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
