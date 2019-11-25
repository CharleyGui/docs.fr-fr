---
title: 'How to: Sort An Array'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3fb9af8de0fc86075fdccd64506c855c1c720660
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351850"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>How to: sort an array in Visual Basic

This article shows an example of how to sort an array of strings in Visual Basic.

## <a name="example"></a>Exemple

This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>Programmation fiable

Les conditions ci-dessous peuvent générer une exception.

- Array is empty (<xref:System.ArgumentNullException> class).
- Array is multidimensional (<xref:System.RankException> class).
- One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).

## <a name="see-also"></a>Voir aussi

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Tableaux](index.md)
- [Dépannage des tableaux](troubleshooting-arrays.md)
- [Regroupements](../../concepts/collections.md)
- [For Each...Next (instruction)](../../../language-reference/statements/for-each-next-statement.md)
