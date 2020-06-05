---
title: Remplacements
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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392026"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Spécifie qu'une propriété ou procédure substitue une propriété ou procédure ayant un nom identique et ayant été héritée d'une classe de base.

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Overrides` uniquement dans une instruction de déclaration de propriété ou de procédure.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Overrides` avec `Shadows` ou `Shared` dans la même déclaration. Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.

- **Correspondance entre signatures.** La signature de cette déclaration doit correspondre exactement à la *signature* de la propriété ou de la procédure qu’elle remplace. Cela signifie que les listes de paramètres doivent avoir le même nombre de paramètres, dans le même ordre, avec les mêmes types de données.

  Outre la signature, la déclaration de substitution doit également correspondre exactement à ce qui suit :

  - Niveau d'accès

  - Type de retour, le cas échéant

- **Signatures génériques.** Pour une procédure générique, la signature inclut le nombre de paramètres de type. Par conséquent, la déclaration de substitution doit correspondre à la version de la classe de base également selon ce critère.

- **Correspondance supplémentaire.** Cette déclaration doit non seulement correspondre à la signature de la version de la classe de base, mais aussi lui correspondre selon les critères suivants :

  - Modificateur de niveau d’accès (par exemple, [public](public.md))

  - Mécanisme de passage de chaque paramètre ([ByVal](byval.md) ou [ByRef](byref.md))

  - Listes de contraintes pour chaque paramètre de type d'une procédure générique

- **Occultation et substitution.** L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.

Le modificateur `Overrides` peut être utilisé dans les contextes suivants :

- [Function (instruction)](../statements/function-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub (instruction)](../statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Mots clés](../keywords/index.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Type List](../statements/type-list.md)
