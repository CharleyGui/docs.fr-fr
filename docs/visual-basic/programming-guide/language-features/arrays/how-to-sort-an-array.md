---
title: 'Procédure : Trier un tableau dans Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700975"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Comment : trier un tableau dans Visual Basic

Cet article montre un exemple de tri d’un tableau de chaînes dans Visual Basic.

## <a name="example"></a>Exemple

Cet exemple déclare un tableau d’objets `String` nommés `zooAnimals`, le remplit, puis le trie par ordre alphabétique :
  
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

- Le tableau est vide (classe <xref:System.ArgumentNullException>).
- Le tableau est multidimensionnel (classe <xref:System.RankException>).
- Un ou plusieurs éléments du tableau n’implémentent pas l’interface <xref:System.IComparable> (classe <xref:System.InvalidOperationException>).

## <a name="see-also"></a>Voir aussi

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Tableaux](index.md)
- [Dépannage des tableaux](troubleshooting-arrays.md)
- [Collections](../../concepts/collections.md)
- [For Each...Next (instruction)](../../../language-reference/statements/for-each-next-statement.md)
