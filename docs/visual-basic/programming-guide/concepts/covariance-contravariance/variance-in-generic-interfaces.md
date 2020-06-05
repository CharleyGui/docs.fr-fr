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
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="a2a9d-102">Variance dans les interfaces génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-102">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="a2a9d-103">.NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="a2a9d-104">La prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="a2a9d-105">Les interfaces suivantes sont maintenant variantes :</span><span class="sxs-lookup"><span data-stu-id="a2a9d-105">The following interfaces are now variant:</span></span>

- <span data-ttu-id="a2a9d-106"><xref:System.Collections.Generic.IEnumerable%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="a2a9d-107"><xref:System.Collections.Generic.IEnumerator%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="a2a9d-108"><xref:System.Linq.IQueryable%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="a2a9d-109"><xref:System.Linq.IGrouping%602> (`TKey` et `TElement` sont covariants)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="a2a9d-110"><xref:System.Collections.Generic.IComparer%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="a2a9d-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="a2a9d-112"><xref:System.IComparable%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="a2a9d-113">La covariance permet à une méthode d’avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="a2a9d-114">Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable(Of Object)` et `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="a2a9d-115">L’interface `IEnumerable(Of String)` n’hérite pas de l’interface `IEnumerable(Of Object)`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="a2a9d-116">Toutefois, le type `String` hérite du type `Object` et, dans certains cas, vous pouvez assigner des objets de ces interfaces de l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="a2a9d-117">Ce cas de figure est présenté dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="a2a9d-117">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="a2a9d-118">Dans les versions antérieures du .NET Framework, ce code provoque une erreur de compilation dans Visual Basic avec `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="a2a9d-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="a2a9d-119">Cependant, vous pouvez désormais utiliser `strings` au lieu d’`objects`, comme illustré dans l’exemple précédent, parce que l’interface <xref:System.Collections.Generic.IEnumerable%601> est covariante.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="a2a9d-120">La contravariance permet à une méthode d’avoir des types d’argument moins dérivés que ceux spécifiés par le paramètre générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="a2a9d-121">Pour illustrer la contravariance, supposez que vous avez créé une classe `BaseComparer` pour comparer des instances de la classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="a2a9d-122">La classe `BaseComparer` implémente l’interface `IEqualityComparer(Of BaseClass)`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="a2a9d-123">Étant donné que l’interface <xref:System.Collections.Generic.IEqualityComparer%601> est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances des classes qui héritent de la classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="a2a9d-124">Ce cas de figure est présenté dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="a2a9d-124">This is shown in the following code example.</span></span>

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

<span data-ttu-id="a2a9d-125">Pour obtenir d’autres exemples, consultez Utilisation de la [variance dans les interfaces pour les collections génériques (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="a2a9d-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="a2a9d-126">La variance dans les interfaces génériques est prise en charge uniquement pour les types référence.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="a2a9d-127">Les types valeur ne prennent pas en charge la variance.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-127">Value types do not support variance.</span></span> <span data-ttu-id="a2a9d-128">Par exemple, `IEnumerable(Of Integer)` ne peut pas être converti implicitement en `IEnumerable(Of Object)`, car les entiers sont représentés par un type valeur.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="a2a9d-129">Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="a2a9d-130">Par exemple, même si <xref:System.Collections.Generic.List%601> implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List(Of Object)` en `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="a2a9d-131">En voici une illustration dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a2a9d-131">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="a2a9d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2a9d-132">See also</span></span>

- [<span data-ttu-id="a2a9d-133">Utilisation de la variance dans les interfaces pour les collections génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="a2a9d-134">Création d'interfaces génériques de type variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="a2a9d-135">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="a2a9d-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="a2a9d-136">Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2a9d-136">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
