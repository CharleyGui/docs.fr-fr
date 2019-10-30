---
title: Opérateur NameOf-Visual Basic
description: Découvrez comment utiliser l’opérateur NameOf dans Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041316"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="8c176-103">Opérateur NameOf-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c176-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="8c176-104">L’opérateur `NameOf` obtient le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :</span><span class="sxs-lookup"><span data-stu-id="8c176-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

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

<span data-ttu-id="8c176-105">Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="8c176-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="8c176-106">L’opérateur `NameOf` est évalué au moment de la compilation et n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8c176-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="8c176-107">Vous pouvez utiliser l’opérateur `NameOf` pour rendre le code de vérification des arguments plus gérable :</span><span class="sxs-lookup"><span data-stu-id="8c176-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

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

<span data-ttu-id="8c176-108">L’opérateur `NameOf` est disponible dans Visual Basic 14 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8c176-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c176-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c176-109">See also</span></span>

- [<span data-ttu-id="8c176-110">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c176-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="8c176-111">Opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c176-111">Operators (Visual Basic)</span></span>](index.md)
