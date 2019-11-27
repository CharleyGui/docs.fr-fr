---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350742"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.

## <a name="remarks"></a>Notes

Quand une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du mot clé `Handles`.

Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module. Cela signifie que le contexte de déclaration pour une variable de `WithEvents` doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.

Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.

Vous pouvez déclarer uniquement des variables individuelles, et non des tableaux, avec `WithEvents`.

## <a name="rules"></a>Règles

**Types d’éléments.** Vous devez déclarer les variables de `WithEvents` comme des variables d’objet afin qu’elles puissent accepter des instances de classe. Toutefois, vous ne pouvez pas les déclarer en tant que `Object`. Vous devez les déclarer en tant que classe spécifique qui peut déclencher les événements.

Le modificateur de `WithEvents` peut être utilisé dans ce contexte : [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Exemple

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Voir aussi

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
