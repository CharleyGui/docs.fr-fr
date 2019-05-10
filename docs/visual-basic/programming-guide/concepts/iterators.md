---
title: Itérateurs (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 73561cf5bed583e2dbf853b7771b9e949a5c0267
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642282"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="b8f4d-102">Itérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8f4d-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="b8f4d-103">Un *itérateur* peut être utilisé pour parcourir des collections, comme des listes et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="b8f4d-104">Une méthode d’itérateur ou un accesseur `get` effectue une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="b8f4d-105">Une méthode d’itérateur utilise le [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément un par un.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="b8f4d-106">Quand une instruction `Yield` est atteinte, l’emplacement actif dans le code est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="b8f4d-107">L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="b8f4d-108">Vous consommez un itérateur depuis le code client en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction, ou en utilisant une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="b8f4d-109">Dans l’exemple suivant, la première itération de la boucle `For Each` fait que l’exécution continue dans la méthode d’itérateur `SomeNumbers`, jusqu’à ce que la première instruction `Yield` soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="b8f4d-110">Cette itération retourne la valeur 3, et l’emplacement actif dans la méthode d’itérateur est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="b8f4d-111">Dans l’itération suivante de la boucle, l’exécution de la méthode d’itérateur continue là où elle s’était arrêtée, et s’arrête de nouveau quand elle atteint une instruction `Yield`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="b8f4d-112">Cette itération retourne la valeur 5, et l’emplacement actif dans la méthode d’itérateur est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="b8f4d-113">La boucle se termine quand la fin de la méthode d’itérateur est atteinte.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="b8f4d-114">Le type de retour d’une méthode d’itérateur ou de l’accesseur `get` peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="b8f4d-115">Vous pouvez utiliser un `Exit Function` ou `Return` instruction pour terminer l’itération.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="b8f4d-116">Une fonction d’itérateur de Visual Basic ou `get` déclaration d’accesseur comprend un [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="b8f4d-117">Itérateurs ont été introduites dans Visual Basic dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="b8f4d-118">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="b8f4d-118">**In this topic**</span></span>  
  
- [<span data-ttu-id="b8f4d-119">Itérateur simple</span><span class="sxs-lookup"><span data-stu-id="b8f4d-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
- [<span data-ttu-id="b8f4d-120">Création d’une classe de collection</span><span class="sxs-lookup"><span data-stu-id="b8f4d-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
- [<span data-ttu-id="b8f4d-121">Blocs try</span><span class="sxs-lookup"><span data-stu-id="b8f4d-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
- [<span data-ttu-id="b8f4d-122">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="b8f4d-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
- [<span data-ttu-id="b8f4d-123">Utilisation d’itérateurs avec une liste générique</span><span class="sxs-lookup"><span data-stu-id="b8f4d-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
- [<span data-ttu-id="b8f4d-124">Informations sur la syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f4d-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
- [<span data-ttu-id="b8f4d-125">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="b8f4d-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
- [<span data-ttu-id="b8f4d-126">Utilisation d’itérateurs</span><span class="sxs-lookup"><span data-stu-id="b8f4d-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="b8f4d-127">Pour tous les exemples dans la rubrique à l’exception de l’exemple d’itérateur Simple, ajoutez [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instructions pour le `System.Collections` et `System.Collections.Generic` espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
## <a name="BKMK_SimpleIterator"></a> <span data-ttu-id="b8f4d-128">Itérateur simple</span><span class="sxs-lookup"><span data-stu-id="b8f4d-128">Simple Iterator</span></span>  
 <span data-ttu-id="b8f4d-129">L’exemple suivant comprend un seul `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="b8f4d-130">Dans `Main`, chaque itération du corps d’instruction `For Each` crée un appel à la fonction d’itérateur, qui poursuit avec l’instruction `Yield` suivante.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="BKMK_CollectionClass"></a> <span data-ttu-id="b8f4d-131">Création d’une classe de collection</span><span class="sxs-lookup"><span data-stu-id="b8f4d-131">Creating a Collection Class</span></span>  
 <span data-ttu-id="b8f4d-132">Dans l’exemple suivant, la classe `DaysOfTheWeek` implémente l’interface <xref:System.Collections.IEnumerable>, ce qui nécessite la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="b8f4d-133">Le compilateur appelle implicitement la méthode `GetEnumerator`, qui retourne un <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="b8f4d-134">Le `GetEnumerator` méthode retourne chaque chaîne une à la fois à l’aide de la `Yield` instruction et un `Iterator` modificateur est dans la déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
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
  
 <span data-ttu-id="b8f4d-135">L’exemple suivant crée une classe `Zoo` qui contient une collection d’animaux.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="b8f4d-136">L’instruction `For Each` qui fait référence à l’instance de classe (`theZoo`) appelle implicitement la méthode `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="b8f4d-137">Les instructions `For Each` qui font référence aux propriétés `Birds` et `Mammals` utilisent la méthode d’itérateur nommée `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
## <a name="BKMK_TryBlocks"></a> <span data-ttu-id="b8f4d-138">Blocs try</span><span class="sxs-lookup"><span data-stu-id="b8f4d-138">Try Blocks</span></span>  
 <span data-ttu-id="b8f4d-139">Visual Basic permet un `Yield` instruction dans le `Try` de blocs à un [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8f4d-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="b8f4d-140">Un `Try` bloc qui a un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="b8f4d-141">L’exemple suivant inclut `Try`, `Catch`, et `Finally` bloque dans une fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="b8f4d-142">Le `Finally` bloc dans la fonction d’itérateur s’exécute avant le `For Each` fin de l’itération.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
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
  
 <span data-ttu-id="b8f4d-143">Un `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="b8f4d-144">Si le `For Each` corps (au lieu de la méthode iterator) lève une exception, un `Catch` bloc dans la fonction d’itérateur n’est pas exécuté, mais un `Finally` bloc dans la fonction d’itérateur est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="b8f4d-145">Un `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="b8f4d-146">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="b8f4d-146">Anonymous Methods</span></span>  
 <span data-ttu-id="b8f4d-147">Dans Visual Basic, une fonction anonyme peut être une fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="b8f4d-148">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-148">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="b8f4d-149">L’exemple suivant comprend une méthode d’itérateur non qui valide les arguments.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="b8f4d-150">La méthode retourne le résultat d’un itérateur anonyme qui décrit les éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
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
  
 <span data-ttu-id="b8f4d-151">Si la validation est à la place à l’intérieur de la fonction d’itérateur, la validation ne peut pas être effectuée avant le démarrage de la première itération de la `For Each` corps.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
## <a name="BKMK_GenericList"></a> <span data-ttu-id="b8f4d-152">Utilisation d’itérateurs avec une liste générique</span><span class="sxs-lookup"><span data-stu-id="b8f4d-152">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="b8f4d-153">Dans l’exemple suivant, la classe générique `Stack(Of T)` implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="b8f4d-154">La méthode `Push` affecte des valeurs à un tableau de type `T`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="b8f4d-155">La méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retourne les valeurs de tableau à l’aide de l’instruction `Yield`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="b8f4d-156">Outre la méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> générique, la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> non générique doit également être implémentée.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="b8f4d-157">C’est parce que <xref:System.Collections.Generic.IEnumerable%601> hérite de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="b8f4d-158">L’implémentation non générique s’en remet à l’implémentation générique.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="b8f4d-159">L’exemple utilise des itérateurs nommés pour prendre en charge différentes façons d’itérer au sein de la même collection de données.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="b8f4d-160">Ces itérateurs nommés sont les propriétés `TopToBottom` et `BottomToTop`, et la méthode `TopN`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="b8f4d-161">Le `BottomToTop` déclaration de propriété inclut le `Iterator` mot clé.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
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
  
## <a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="b8f4d-162">Informations sur la syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f4d-162">Syntax Information</span></span>  
 <span data-ttu-id="b8f4d-163">Un itérateur peut être une méthode ou un accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="b8f4d-164">Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="b8f4d-165">Une conversion implicite doit exister depuis le type d’expression dans l’instruction `Yield` vers le type de retour de l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="b8f4d-166">En Visual Basic, une méthode d’itérateur ne peut avoir aucun `ByRef` paramètres.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="b8f4d-167">En Visual Basic, « Yield » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’elle est utilisée dans un `Iterator` méthode ou `get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
## <a name="BKMK_Technical"></a> <span data-ttu-id="b8f4d-168">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="b8f4d-168">Technical Implementation</span></span>  
 <span data-ttu-id="b8f4d-169">Bien que vous écriviez un itérateur comme une méthode, le compilateur le traduit en une classe imbriquée, qui est en réalité une machine à états.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="b8f4d-170">Cette classe fait le suivi de la position de l’itérateur tant que la boucle `For Each...Next` du code client se poursuit.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="b8f4d-171">Pour voir ce que fait le compilateur, vous pouvez utiliser l’outil Ildasm.exe pour afficher le code du langage intermédiaire Microsoft généré pour une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="b8f4d-172">Lorsque vous créez un itérateur pour un [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), il est inutile d’implémenter l’ensemble <xref:System.Collections.IEnumerator> interface.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="b8f4d-173">Quand le compilateur détecte l’itérateur, il génère automatiquement les méthodes `Current`, `MoveNext` et `Dispose` de l’interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="b8f4d-174">À chaque itération successive de la boucle `For Each…Next` (ou de l’appel direct à `IEnumerator.MoveNext`), le corps du code de l’itérateur suivant reprend après l’instruction `Yield` précédente.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="b8f4d-175">Il continue ensuite à la prochaine `Yield` instruction jusqu'à la fin du corps d’itérateur, ou jusqu'à ce qu’un `Exit Function` ou `Return` est rencontrée.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="b8f4d-176">Les itérateurs ne gèrent pas la <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b8f4d-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b8f4d-177">Pour réitérer à partir du début, vous devez obtenir un nouvel itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="b8f4d-178">Pour plus d’informations, consultez le [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8f4d-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
## <a name="BKMK_UseOfIterators"></a> <span data-ttu-id="b8f4d-179">Utilisation d’itérateurs</span><span class="sxs-lookup"><span data-stu-id="b8f4d-179">Use of Iterators</span></span>  
 <span data-ttu-id="b8f4d-180">Les itérateurs vous permettent de conserver la simplicité d’une boucle `For Each` quand vous avez besoin d’utiliser un code complexe pour remplir la séquence d’une liste.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="b8f4d-181">Ceci peut être utile quand vous voulez faire les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8f4d-181">This can be useful when you want to do the following:</span></span>  
  
- <span data-ttu-id="b8f4d-182">Modifier la séquence de la liste après la première itération de la boucle `For Each`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
- <span data-ttu-id="b8f4d-183">Éviter de charger entièrement une grande liste avant la première itération d’une boucle `For Each`.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="b8f4d-184">Une extraction paginée pour charger un lot de lignes d’une table est un exemple.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="b8f4d-185">Un autre exemple est la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , qui implémente les itérateurs dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
- <span data-ttu-id="b8f4d-186">Encapsuler la création de la liste dans l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="b8f4d-187">Dans la méthode d’itérateur, vous pouvez créer la liste et générer ensuite chaque résultat dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="b8f4d-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f4d-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8f4d-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="b8f4d-189">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="b8f4d-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="b8f4d-190">Yield (instruction)</span><span class="sxs-lookup"><span data-stu-id="b8f4d-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
- [<span data-ttu-id="b8f4d-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="b8f4d-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
