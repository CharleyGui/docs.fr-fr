---
title: Variance dans les interfaces génériques
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: df28a9f24518f24d1be89acba726da7dfbbf9570
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375588"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Variance dans les interfaces génériques (Visual Basic)

.NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. La prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces. Les interfaces suivantes sont maintenant variantes :

- <xref:System.Collections.Generic.IEnumerable%601> (T est covariant)

- <xref:System.Collections.Generic.IEnumerator%601> (T est covariant)

- <xref:System.Linq.IQueryable%601> (T est covariant)

- <xref:System.Linq.IGrouping%602> (`TKey` et `TElement` sont covariants)

- <xref:System.Collections.Generic.IComparer%601> (T est contravariant)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T est contravariant)

- <xref:System.IComparable%601> (T est contravariant)

La covariance permet à une méthode d’avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface. Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable(Of Object)` et `IEnumerable(Of String)`. L’interface `IEnumerable(Of String)` n’hérite pas de l’interface `IEnumerable(Of Object)`. Toutefois, le type `String` hérite du type `Object` et, dans certains cas, vous pouvez assigner des objets de ces interfaces de l’un à l’autre. Ce cas de figure est présenté dans l’exemple de code suivant :

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

Dans les versions antérieures du .NET Framework, ce code provoque une erreur de compilation dans Visual Basic avec `Option Strict On` . Cependant, vous pouvez désormais utiliser `strings` au lieu d’`objects`, comme illustré dans l’exemple précédent, parce que l’interface <xref:System.Collections.Generic.IEnumerable%601> est covariante.

La contravariance permet à une méthode d’avoir des types d’argument moins dérivés que ceux spécifiés par le paramètre générique de l’interface. Pour illustrer la contravariance, supposez que vous avez créé une classe `BaseComparer` pour comparer des instances de la classe `BaseClass`. La classe `BaseComparer` implémente l’interface `IEqualityComparer(Of BaseClass)`. Étant donné que l’interface <xref:System.Collections.Generic.IEqualityComparer%601> est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances des classes qui héritent de la classe `BaseClass`. Ce cas de figure est présenté dans l’exemple de code suivant :

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

Pour obtenir d’autres exemples, consultez Utilisation de la [variance dans les interfaces pour les collections génériques (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).

La variance dans les interfaces génériques est prise en charge uniquement pour les types référence. Les types valeur ne prennent pas en charge la variance. Par exemple, `IEnumerable(Of Integer)` ne peut pas être converti implicitement en `IEnumerable(Of Object)`, car les entiers sont représentés par un type valeur.

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes. Par exemple, même si <xref:System.Collections.Generic.List%601> implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List(Of Object)` en `List(Of String)`. En voici une illustration dans l’exemple de code suivant.

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de la variance dans les interfaces pour les collections génériques (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md)
- [Création d'interfaces génériques de type variant (Visual Basic)](creating-variant-generic-interfaces.md)
- [Interfaces génériques](../../../../standard/generics/interfaces.md)
- [Variance dans les délégués (Visual Basic)](variance-in-delegates.md)
