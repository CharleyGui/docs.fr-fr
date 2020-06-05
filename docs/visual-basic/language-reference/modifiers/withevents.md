---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386774"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.

## <a name="remarks"></a>Notes

Quand une variable est définie à l’aide `WithEvents` de, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` mot clé.

Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module. Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.

Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.

Vous pouvez déclarer uniquement des variables individuelles, et non des tableaux, avec `WithEvents` .

## <a name="rules"></a>Règles

**Types d’éléments.** Vous devez déclarer des `WithEvents` variables en tant que variables d’objet afin qu’elles puissent accepter des instances de classe. Toutefois, vous ne pouvez pas les déclarer en tant que `Object` . Vous devez les déclarer en tant que classe spécifique qui peut déclencher les événements.

Le `WithEvents` modificateur peut être utilisé dans ce contexte : [instruction Dim](../statements/dim-statement.md)

## <a name="example"></a>Exemple

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Voir aussi

- [Poignées](../statements/handles-clause.md)
- [Mots clés](../keywords/index.md)
- [Événements](../../programming-guide/language-features/events/index.md)
