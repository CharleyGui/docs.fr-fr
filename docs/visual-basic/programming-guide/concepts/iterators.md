---
title: Iterators
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 465a8e6650c3d015520164030a146c9502ebe603
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353736"
---
# <a name="iterators-visual-basic"></a>Iterators (Visual Basic)

Un *itérateur* peut être utilisé pour parcourir des collections, comme des listes et des tableaux.

Une méthode d’itérateur ou un accesseur `get` effectue une itération personnalisée sur une collection. An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time. Quand une instruction `Yield` est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.

You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.

Dans l’exemple suivant, la première itération de la boucle `For Each` fait que l’exécution continue dans la méthode d’itérateur `SomeNumbers`, jusqu’à ce que la première instruction `Yield` soit atteinte. Cette itération retourne la valeur 3, et l’emplacement actif dans la méthode d’itérateur est mémorisé. Dans l’itération suivante de la boucle, l’exécution de la méthode d’itérateur continue là où elle s’était arrêtée, et s’arrête de nouveau quand elle atteint une instruction `Yield`. Cette itération retourne la valeur 5, et l’emplacement actif dans la méthode d’itérateur est mémorisé. La boucle se termine quand la fin de la méthode d’itérateur est atteinte.

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

Le type de retour d’une méthode d’itérateur ou de l’accesseur `get` peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

You can use an `Exit Function` or `Return` statement to end the iteration.

A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.

Iterators were introduced in Visual Basic in Visual Studio 2012.

**Dans cette rubrique**

- [Itérateur simple](#BKMK_SimpleIterator)

- [Création d’une classe de collection](#BKMK_CollectionClass)

- [Try Blocks](#BKMK_TryBlocks)

- [Méthodes anonymes](#BKMK_AnonymousMethods)

- [Utilisation d’itérateurs avec une liste générique](#BKMK_GenericList)

- [Informations sur la syntaxe](#BKMK_SyntaxInformation)

- [Implémentation technique](#BKMK_Technical)

- [Utilisation d’itérateurs](#BKMK_UseOfIterators)

> [!NOTE]
> For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.

## <a name="BKMK_SimpleIterator"></a> Itérateur simple

The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Dans `Main`, chaque itération du corps d’instruction `For Each` crée un appel à la fonction d’itérateur, qui poursuit avec l’instruction `Yield` suivante.

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="BKMK_CollectionClass"></a> Création d’une classe de collection

Dans l’exemple suivant, la classe `DaysOfTheWeek` implémente l’interface <xref:System.Collections.IEnumerable>, ce qui nécessite la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Le compilateur appelle implicitement la méthode `GetEnumerator`, qui retourne un <xref:System.Collections.IEnumerator>.

The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

L’exemple suivant crée une classe `Zoo` qui contient une collection d’animaux.

L’instruction `For Each` qui fait référence à l’instance de classe (`theZoo`) appelle implicitement la méthode `GetEnumerator`. Les instructions `For Each` qui font référence aux propriétés `Birds` et `Mammals` utilisent la méthode d’itérateur nommée `AnimalsForType`.

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="BKMK_TryBlocks"></a> Try Blocks

Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.

The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function. The `Finally` block in the iterator function executes before the `For Each` iteration finishes.

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.

If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed. A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.

## <a name="BKMK_AnonymousMethods"></a> Anonymous Methods

In Visual Basic, an anonymous function can be an iterator function. L'exemple suivant illustre ce comportement.

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

The following example has a non-iterator method that validates the arguments. The method returns the result of an anonymous iterator that describes the collection elements.

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.

## <a name="BKMK_GenericList"></a> Utilisation d’itérateurs avec une liste générique

Dans l’exemple suivant, la classe générique `Stack(Of T)` implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601>. La méthode `Push` affecte des valeurs à un tableau de type `T`. La méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retourne les valeurs de tableau à l’aide de l’instruction `Yield`.

Outre la méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> générique, la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> non générique doit également être implémentée. C’est parce que <xref:System.Collections.Generic.IEnumerable%601> hérite de <xref:System.Collections.IEnumerable>. L’implémentation non générique s’en remet à l’implémentation générique.

L’exemple utilise des itérateurs nommés pour prendre en charge différentes façons d’itérer au sein de la même collection de données. Ces itérateurs nommés sont les propriétés `TopToBottom` et `BottomToTop`, et la méthode `TopN`.

The `BottomToTop` property declaration includes the `Iterator` keyword.

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="BKMK_SyntaxInformation"></a> Informations sur la syntaxe

Un itérateur peut être une méthode ou un accesseur `get`. Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.

Une conversion implicite doit exister depuis le type d’expression dans l’instruction `Yield` vers le type de retour de l’itérateur.

In Visual Basic, an iterator method cannot have any `ByRef` parameters.

In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.

## <a name="BKMK_Technical"></a> Implémentation technique

Bien que vous écriviez un itérateur comme une méthode, le compilateur le traduit en une classe imbriquée, qui est en réalité une machine à états. Cette classe fait le suivi de la position de l’itérateur tant que la boucle `For Each...Next` du code client se poursuit.

Pour voir ce que fait le compilateur, vous pouvez utiliser l’outil Ildasm.exe pour afficher le code du langage intermédiaire Microsoft généré pour une méthode d’itérateur.

When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface. Quand le compilateur détecte l’itérateur, il génère automatiquement les méthodes `Current`, `MoveNext` et `Dispose` de l’interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

À chaque itération successive de la boucle `For Each…Next` (ou de l’appel direct à `IEnumerator.MoveNext`), le corps du code de l’itérateur suivant reprend après l’instruction `Yield` précédente. It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.

Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method. Pour réitérer à partir du début, vous devez obtenir un nouvel itérateur.

For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).

## <a name="BKMK_UseOfIterators"></a> Utilisation d’itérateurs

Les itérateurs vous permettent de conserver la simplicité d’une boucle `For Each` quand vous avez besoin d’utiliser un code complexe pour remplir la séquence d’une liste. Ceci peut être utile quand vous voulez faire les opérations suivantes :

- Modifier la séquence de la liste après la première itération de la boucle `For Each`.

- Éviter de charger entièrement une grande liste avant la première itération d’une boucle `For Each`. Une extraction paginée pour charger un lot de lignes d’une table est un exemple. Un autre exemple est la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , qui implémente les itérateurs dans le .NET Framework.

- Encapsuler la création de la liste dans l’itérateur. Dans la méthode d’itérateur, vous pouvez créer la liste et générer ensuite chaque résultat dans une boucle.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Yield (instruction)](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
