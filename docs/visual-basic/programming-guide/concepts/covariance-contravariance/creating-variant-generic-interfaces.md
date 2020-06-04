---
title: Création d'interfaces génériques de type variant
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 884349159d2738d8481b217f9dab383483616f2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400640"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Création d'interfaces génériques de type variant (Visual Basic)

Vous pouvez déclarer des paramètres de type générique dans les interfaces comme covariant ou contravariant. La *covariance* permet aux méthodes d’interface d’avoir des types de retour plus dérivés que ceux définis par les paramètres de type générique. La *contravariance* permet aux méthodes d’interface d’avoir des types d’argument moins dérivés que ceux spécifiés par les paramètres génériques. Une interface générique ayant des paramètres de type générique covariant ou contravariant est appelée *variante*.

> [!NOTE]
> .NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. Pour obtenir la liste des interfaces de type Variant dans le .NET Framework, consultez [variance dans les interfaces génériques (Visual Basic)](variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Déclaration d’interfaces génériques de type variant

Vous pouvez déclarer des interfaces génériques de type variant à l’aide des mots clés `in` et `out` pour les paramètres de type générique.

> [!IMPORTANT]
> `ByRef`les paramètres de Visual Basic ne peuvent pas être de type Variant. Les types valeur ne prennent pas non plus en charge la variance.

Vous pouvez déclarer un covariant de paramètre de type générique à l’aide du mot clé `out`. Le type covariant doit remplir les conditions suivantes :

- Le type est utilisé uniquement comme un type de retour de méthodes d’interface, et non pas comme un type d’arguments de méthode. L’exemple suivant en fournit une illustration dans laquelle le type `R` est déclaré covariant.

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    Il existe une exception à cette règle. Si vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type comme paramètre de type générique pour le délégué. L’exemple suivant du type `R` illustre ce principe. Pour plus d’informations, consultez [variance dans les délégués (Visual Basic)](variance-in-delegates.md) et [utilisation de la variance pour les délégués génériques Func et action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- Le type n’est pas utilisé comme contrainte générique pour les méthodes d’interface. C’est ce que montre le code suivant.

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

Vous pouvez déclarer un contravariant de paramètre de type générique à l’aide du mot clé `in`. Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode, et non comme type de retour de méthodes d’interface. Le type contravariant peut également être utilisé pour les contraintes génériques. Le code suivant montre comment déclarer une interface de type contravariant et utiliser une contrainte générique pour l’une de ses méthodes.

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

Il est également possible de prendre en charge à la fois la covariance et la contravariance dans la même interface, mais pour des paramètres de type différent, comme indiqué dans l’exemple de code suivant.

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

Dans Visual Basic, vous ne pouvez pas déclarer d’événements dans des interfaces variant sans spécifier le type délégué. En outre, une interface de variante ne peut pas avoir de classes, d’énumérations ou de structures imbriquées, mais elle peut avoir des interfaces imbriquées. C’est ce que montre le code suivant.

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a>Implémentation d’interfaces génériques de type variant

Vous implémentez des interfaces génériques de type variant dans les classes en utilisant la même syntaxe que celle utilisée pour les interfaces invariantes. L’exemple de code suivant montre comment implémenter une interface de type covariant dans une classe générique.

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

Les classes qui implémentent des interfaces de type variant sont invariantes. Par exemple, prenons le code suivant.

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a>Extension d’interfaces génériques de type variant

Quand vous étendez une interface générique de type variant, vous devez utiliser les mots clés `in` et `out` pour spécifier explicitement si l’interface dérivée prend en charge la variance. Le compilateur ne déduit pas la variance de l’interface étendue. Observons, par exemple, les interfaces suivantes.

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

Dans l' `Invariant(Of T)` interface, le paramètre de type générique `T` est invariant, tandis que dans `IExtCovariant (Of Out T)` le paramètre de type est covariant, bien que les deux interfaces étendent la même interface. La même règle est appliquée aux paramètres de type générique contravariant.

Vous pouvez créer une interface qui étend à la fois l’interface dans laquelle le paramètre de type générique `T` est covariant et l’interface dans laquelle il est contravariant si, dans l’interface étendue, le paramètre de type générique `T` est invariant. En voici une illustration dans l’exemple de code suivant.

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

Toutefois, si un paramètre de type générique `T` est déclaré covariant dans une interface, vous ne pouvez pas le déclarer contravariant dans l’interface étendue, ou vice versa. En voici une illustration dans l’exemple de code suivant.

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a>Éviter l’ambiguïté

Quand vous implémentez des interfaces génériques de type variant, la variance peut parfois mener à une certaine ambiguïté. Cela doit être évité.

Par exemple, si vous implémentez explicitement la même interface générique de type variant avec des paramètres de type générique différents dans une classe, cela peut être source d’ambiguïté. Le compilateur ne génère pas d’erreur dans ce cas, mais l’implémentation d’interface qui sera choisie lors de l’exécution ne lui est pas spécifiée. Des bogues subtils peuvent alors apparaître dans votre code. Prenons l’exemple de code suivant.

> [!NOTE]
> Avec `Option Strict Off` , Visual Basic génère un avertissement du compilateur en cas d’implémentation d’interface ambiguë. Avec `Option Strict On` , Visual Basic génère une erreur du compilateur.

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

Dans cet exemple, la façon dont la méthode `pets.GetEnumerator` choisit entre `Cat` et `Dog` n’est pas spécifiée. Cela peut provoquer des problèmes dans votre code.

## <a name="see-also"></a>Voir aussi

- [Variance dans les interfaces génériques (Visual Basic)](variance-in-generic-interfaces.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)
