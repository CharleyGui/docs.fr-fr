---
title: Covariance et contravariance
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 11dd71a8cfde12b7af1de79e3f5a095f79d8aa6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400628"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Covariance et contravariance (Visual Basic)

En Visual Basic, la covariance et la contravariance permettent la conversion de références implicite pour les types tableau, les types délégués et les arguments de type générique. La covariance conserve la compatibilité d’assignation et la contravariance l’inverse.

Le code suivant illustre la différence entre la compatibilité d’assignation, la covariance et la contravariance.

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

La covariance pour les tableaux permet la conversion implicite d’un tableau d’un type plus dérivé en un tableau d’un type moins dérivé. Cette opération n’est cependant pas sécurisée au niveau des types, comme le montre l’exemple de code suivant.

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

La prise en charge de la covariance et la contravariance pour les groupes de méthodes permet la correspondance des signatures de méthode avec des types délégués. Ceci vous permet d’affecter aux délégués non seulement les méthodes ayant des signatures correspondantes, mais aussi des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Pour plus d’informations, consultez [Variance dans les délégués (Visual Basic)](variance-in-delegates.md) et [Utilisation de la variance dans les délégués (Visual Basic)](using-variance-in-delegates.md).

L’exemple de code suivant montre la prise en charge de la covariance et de la contravariance pour les groupes de méthode.

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

Dans .NET Framework 4 ou version ultérieure, Visual Basic prend en charge la covariance et la contravariance dans les interfaces et les délégués génériques, et permet la conversion implicite de paramètres de type générique. Pour plus d’informations, consultez [Variance dans les interfaces génériques (Visual Basic)](variance-in-generic-interfaces.md) et [Variance dans les délégués (Visual Basic)](variance-in-delegates.md).

L’exemple de code suivant illustre la conversion de références implicite pour les interfaces génériques.

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

Une interface ou un délégué générique est dit de type *variant* si ses paramètres génériques sont déclarés covariants ou contravariants. Visual Basic vous permet de créer vos propres interfaces et délégués de type variant. Pour plus d’informations, consultez [Création d’interfaces génériques de type variant (Visual Basic)](creating-variant-generic-interfaces.md) et [Variance dans les délégués (Visual Basic)](variance-in-delegates.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Variance dans les interfaces génériques (Visual Basic)](variance-in-generic-interfaces.md)|Décrit la covariance et la contravariance dans les interfaces génériques et fournit la liste des interfaces génériques de type variant dans le .NET Framework.|
|[Création d'interfaces génériques de type variant (Visual Basic)](creating-variant-generic-interfaces.md)|Montre comment créer des interfaces de type variant personnalisées.|
|[Utilisation de la variance dans les interfaces pour les collections génériques (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md)|Montre comment la prise en charge de la covariance et de la contravariance dans les interfaces <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IComparable%601> peut vous aider à réutiliser du code.|
|[Variance dans les délégués (Visual Basic)](variance-in-delegates.md)|Présente la covariance et la contravariance dans les délégués génériques et non génériques, et fournit une liste des délégués génériques de type variant dans le .NET Framework.|
|[Utilisation de la variance dans les délégués (Visual Basic)](using-variance-in-delegates.md)|Montre comment utiliser la prise en charge de la covariance et de la contravariance dans les délégués non génériques pour faire correspondre des signatures de méthode avec des types délégués.|
|[Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)|Montre comment la prise en charge de la covariance et de la contravariance dans les délégués `Func` et `Action` peut vous aider à réutiliser du code.|
