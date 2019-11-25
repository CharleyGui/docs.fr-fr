---
title: Variables de structure
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 16b6cdc5a849b50f6caa8b7963dac5c12d63cf3e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346304"
---
# <a name="structure-variables-visual-basic"></a>Variables de structure (Visual Basic)

Once you have created a structure, you can declare procedure-level and module-level variables as that type. For example, you can create a structure that records information about a computer system. Cela est illustré par l'exemple suivant.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

You can now declare variables of that type. The following declaration illustrates this.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access. If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.

## <a name="access-to-structure-values"></a>Access to Structure Values

To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object. You place the member access operator (`.`) between the structure variable name and the element name. The following example accesses elements of the variables previously declared as type `systemInfo`.

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Assigning Structure Variables

You can also assign one variable to another if both are of the same structure type. This copies all the elements of one structure to the corresponding elements in the other. The following declaration illustrates this.

```vb
yourSystem = mySystem
```

If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied. In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.

## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
