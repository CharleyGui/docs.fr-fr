---
title: Variables de structure
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393583"
---
# <a name="structure-variables-visual-basic"></a>Variables de structure (Visual Basic)

Une fois que vous avez créé une structure, vous pouvez déclarer des variables au niveau de la procédure et au niveau du module comme ce type. Par exemple, vous pouvez créer une structure qui enregistre des informations sur un système informatique. l’exemple ci-dessous illustre ce cas de figure.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

Vous pouvez maintenant déclarer des variables de ce type. La déclaration suivante illustre cela.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> Dans les classes et les modules, les structures déclarées à l’aide de l' [instruction Dim](../../../language-reference/statements/dim-statement.md) utilisent par défaut l’accès public. Si vous envisagez de disposer d’une structure privée, assurez-vous de la déclarer à l’aide du mot clé [Private](../../../language-reference/modifiers/private.md) .

## <a name="access-to-structure-values"></a>Accès aux valeurs de structure

Pour assigner et récupérer des valeurs à partir des éléments d’une variable de structure, vous utilisez la même syntaxe que celle utilisée pour définir et obtenir des propriétés sur un objet. Vous placez l’opérateur d’accès aux membres ( `.` ) entre le nom de la variable de structure et le nom de l’élément. L’exemple suivant accède aux éléments des variables précédemment déclarées en tant que type `systemInfo` .

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Affectation de variables de structure

Vous pouvez également assigner une variable à une autre si les deux sont du même type de structure. Cela permet de copier tous les éléments d’une structure dans les éléments correspondants de l’autre. La déclaration suivante illustre cela.

```vb
yourSystem = mySystem
```

Si un élément de structure est un type référence, tel qu' `String` un `Object` tableau, ou, le pointeur vers les données est copié. Dans l’exemple précédent, si `systemInfo` avait inclus une variable objet, l’exemple précédent aurait copié le pointeur de `mySystem` vers `yourSystem` , et une modification apportée aux données de l’objet par le biais d’une structure serait appliquée lors de l’accès par le biais de l’autre structure.

## <a name="see-also"></a>Voir aussi

- [Types de données](index.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types de données composites](composite-data-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Structures](structures.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Procédure : Déclarer une structure](how-to-declare-a-structure.md)
- [Structures et autres éléments de programmation](structures-and-other-programming-elements.md)
- [Structures et classes](structures-and-classes.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
