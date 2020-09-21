---
title: Opérateur NameOf
description: Découvrez comment utiliser l’opérateur NameOf dans Visual Basic
ms.date: 10/27/2019
f1_keywords:
- NameOf
- vb.NameOf
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 0e72c4cb0c10113e53067ea4a743ca5ee77bcc95
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828901"
---
# <a name="nameof-operator---visual-basic"></a>Opérateur NameOf-Visual Basic

L’opérateur `NameOf` obtient le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

L’opérateur `NameOf` est évalué au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez utiliser l’opérateur `NameOf` pour rendre le code de vérification des arguments plus gérable :

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

L' `NameOf` opérateur est disponible dans Visual Basic 14 et versions ultérieures.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](../index.md)
- [Opérateurs (Visual Basic)](index.md)
