---
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 27fc993ca0b94d406261d5e6275de8cd619eb6a8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303450"
---
# <a name="protected-friend-visual-basic"></a>Ami protégé (Visual Basic)

La combinaison de mots clés `Protected Friend` est un modificateur d’accès de membre. Il confère à l’accès [Friend](friend.md) et à l’accès [protégé](protected.md) sur les éléments déclarés, de sorte qu’ils sont accessibles depuis n’importe où dans le même assembly, à partir de leur propre classe et à partir de classes dérivées. Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes ; vous ne pouvez pas appliquer `Protected Friend` aux membres d’une structure, car les structures ne peuvent pas être héritées.

> [!NOTE]
> Dans Visual Studio, la sélection de l’aide F1 dans `protected friend` fournit de l’aide pour [protected](protected.md) ou [Friend](friend.md). L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.

## <a name="rules"></a>Règles

**Contexte de déclaration.** Vous pouvez utiliser `Protected Friend` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.

## <a name="see-also"></a>Voir aussi

- [Public](public.md)
- [Protect](protected.md)
- [Contact](friend.md)
- [Privé](private.md)
- [Protégé privé](./private-protected.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
