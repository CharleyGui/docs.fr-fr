---
title: Overrides
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351385"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Spécifie qu'une propriété ou procédure substitue une propriété ou procédure ayant un nom identique et ayant été héritée d'une classe de base.

## <a name="rules"></a>Règles

- **Declaration Context.** You can use `Overrides` only in a property or procedure declaration statement.

- **Combined Modifiers.** You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration. Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.

- **Matching Signatures.** The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides. Cela signifie que les listes de paramètres doivent avoir le même nombre de paramètres, dans le même ordre, avec les mêmes types de données.

  Outre la signature, la déclaration de substitution doit également correspondre exactement à ce qui suit :

  - Niveau d'accès

  - Type de retour, le cas échéant

- **Generic Signatures.** Pour une procédure générique, la signature inclut le nombre de paramètres de type. Par conséquent, la déclaration de substitution doit correspondre à la version de la classe de base également selon ce critère.

- **Additional Matching.** Cette déclaration doit non seulement correspondre à la signature de la version de la classe de base, mais aussi lui correspondre selon les critères suivants :

  - Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))

  - Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))

  - Listes de contraintes pour chaque paramètre de type d'une procédure générique

- **Shadowing and Overriding.** L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches. For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.

Le modificateur `Overrides` peut être utilisé dans les contextes suivants :

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)
