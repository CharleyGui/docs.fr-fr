---
title: Variance dans les délégués
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 11146bc4a60f55fc0373f0b5dfa5d44dcf748a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348999"
---
# <a name="variance-in-delegates-visual-basic"></a>Variance in Delegates (Visual Basic)

.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic. Cela signifie que vous pouvez assigner aux délégués non seulement les méthodes ayant des signatures correspondantes, mais également des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Cela inclut à la fois des délégués génériques et non génériques.

Par exemple, considérez le code suivant, qui a deux classes et deux délégués : génériques et non génériques.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Quand vous créez des délégués des types `SampleDelegate` ou `SampleDelegate(Of A, R)`, vous pouvez assigner l’une des méthodes suivantes à ces délégués.

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

L’exemple de code suivant illustre la conversion implicite entre la signature de méthode et le type délégué.

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Variance dans les paramètres de type générique

In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.

Pour activer la conversion implicite, vous devez déclarer explicitement les paramètres génériques dans un délégué comme covariant ou contravariant à l’aide du mot clé `in` ou `out`.

L’exemple de code suivant indique comment vous pouvez créer un délégué ayant un paramètre de type générique covariant.

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

Si vous utilisez uniquement la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués et que vous n’utilisez pas les mots clés `in` et `out`, vous pouvez réaliser qu’il est parfois possible d’instancier des délégués avec des expressions ou méthodes lambda identiques, mais que vous ne pouvez pas assigner un délégué à un autre.

In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`. Vous pouvez résoudre ce problème en marquant le paramètre générique `T` avec le mot clé `out`.

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Délégués génériques ayant des paramètres de type variant dans le .NET Framework

.NET Framework 4 a introduit la prise en charge de la variance pour les paramètres de type générique dans plusieurs délégués génériques existants :

- Les délégués `Action` de l’espace de noms <xref:System>, par exemple, <xref:System.Action%601> et <xref:System.Action%602>

- Les délégués `Func` de l’espace de noms <xref:System>, par exemple, <xref:System.Func%601> et <xref:System.Func%602>

- Le délégué <xref:System.Predicate%601>

- Le délégué <xref:System.Comparison%601>

- Le délégué <xref:System.Converter%602>

For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Déclaration de paramètres de type variant dans les délégués génériques

Si un délégué générique possède des paramètres de type générique covariant ou contravariant, il peut être désigné sous le nom de *délégué générique variant*.

Vous pouvez déclarer un paramètre de type générique covariant dans un délégué générique à l’aide du mot clé `out`. Le type covariant peut être utilisé uniquement comme type de retour de méthode et non comme type d’arguments de méthode. L’exemple de code suivant indique comment déclarer un délégué générique covariant.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Vous pouvez déclarer un paramètre de type générique contravariant dans un délégué générique à l’aide du mot clé `in`. Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme type de retour de méthode. L’exemple de code suivant indique comment déclarer un délégué générique contravariant.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef` parameters in Visual Basic can't be marked as variant.

Il est également possible de prendre en charge à la fois la variance et la covariance dans le même délégué, mais pour des paramètres de type différents. L'exemple suivant le démontre.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Instanciation et appel de délégués génériques variants

Vous pouvez instancier et appeler des délégués variants de la même façon que vous instanciez et appelez des délégués invariants. Dans l’exemple suivant, le délégué est instancié par une expression lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Combinaison des délégués génériques variants

Vous ne devez pas combiner les délégués variants. La méthode <xref:System.Delegate.Combine%2A> ne prend pas en charge la conversion des délégués variants et nécessite le même type pour tous les délégués. This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance dans les paramètres de type générique pour les types valeur et référence

La variance pour les paramètres de type générique est prise en charge uniquement pour les types référence. For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.

L’exemple suivant montre que la variance dans les paramètres de type générique n’est pas prise en charge pour les types valeur.

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Relaxed Delegate Conversion in Visual Basic

Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types. For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate. For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Voir aussi

- [Génériques](../../../../standard/generics/index.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
