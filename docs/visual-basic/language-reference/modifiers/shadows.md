---
title: Shadows
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
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402705"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Spécifie qu’un élément de programmation déclaré redéclare et masque un élément portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base.

## <a name="remarks"></a>Notes

L’objectif principal de l’occultation (qui est également connu sous le *nom de masquage par nom*) consiste à conserver la définition de vos membres de classe. La classe de base peut subir une modification qui crée un élément avec le même nom que celui que vous avez déjà défini. Dans ce cas, le `Shadows` modificateur force les références via votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.

L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Shadows` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un `Shadows` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.

  Vous pouvez déclarer un seul élément d’occultation dans une instruction de déclaration unique.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shadows` avec `Overloads` , `Overrides` ou `Static` dans la même déclaration.

- **Types d’éléments.** Vous pouvez occulter tout type d'élément déclaré par un autre type. Si vous occultez une propriété ou une procédure avec une autre propriété ou procédure, il n’est pas nécessaire que les paramètres et le type de retour correspondent à ceux de la procédure ou de la propriété de la classe de base.

- **L’accès à.** L’élément occulté dans la classe de base est normalement indisponible à partir de la classe dérivée qui l’occulte. Toutefois, les considérations suivantes s’appliquent.

  - Si l’élément d’occultation n’est pas accessible à partir du code qui y fait référence, la référence est résolue en élément occulté. Par exemple, si un `Private` élément occulte un élément de classe de base, le code qui n’a pas l’autorisation d’accéder à l' `Private` élément accède à l’élément de classe de base à la place.

  - Si vous occultez un élément, vous pouvez toujours accéder à l’élément occulté à l’aide d’un objet déclaré avec le type de la classe de base. Vous pouvez également y accéder via `MyBase` .

Le modificateur `Shadows` peut être utilisé dans les contextes suivants :

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

- [Partagé](shared.md)
- [Statique](static.md)
- [Privé](private.md)
- [Me, My, MyBase et MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Surcharges](overloads.md)
- [Overridable](overridable.md)
- [Remplacements](overrides.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
