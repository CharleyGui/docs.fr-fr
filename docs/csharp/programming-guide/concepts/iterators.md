---
title: Effectuer une itération dans des collections (C#)
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626268"
---
# <a name="iterators-c"></a><span data-ttu-id="ed6a6-102">Itérateurs (C#)</span><span class="sxs-lookup"><span data-stu-id="ed6a6-102">Iterators (C#)</span></span>

<span data-ttu-id="ed6a6-103">Un *itérateur* peut être utilisé pour parcourir des collections, comme des listes et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="ed6a6-104">Une méthode d’itérateur ou un accesseur `get` effectue une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="ed6a6-105">Une méthode d’itérateur utilise l’instruction [yield return](../../language-reference/keywords/yield.md) pour retourner chaque élément un par un.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="ed6a6-106">Quand une instruction `yield return` est atteinte, l’emplacement actuel dans le code est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="ed6a6-107">L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="ed6a6-108">Vous consommez un itérateur à partir du code client en utilisant une instruction [foreach](../../language-reference/keywords/foreach-in.md) ou une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="ed6a6-109">Dans l’exemple suivant, la première itération de la boucle `foreach` fait que l’exécution continue dans la méthode d’itérateur `SomeNumbers`, jusqu’à ce que la première instruction `yield return` soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="ed6a6-110">Cette itération retourne la valeur 3, et l’emplacement actif dans la méthode d’itérateur est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="ed6a6-111">Dans l’itération suivante de la boucle, l’exécution de la méthode d’itérateur continue là où elle s’était arrêtée, et s’arrête de nouveau quand elle atteint une instruction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="ed6a6-112">Cette itération retourne la valeur 5, et l’emplacement actif dans la méthode d’itérateur est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="ed6a6-113">La boucle se termine quand la fin de la méthode d’itérateur est atteinte.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-113">The loop completes when the end of the iterator method is reached.</span></span>

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

<span data-ttu-id="ed6a6-114">Le type de retour d’une méthode d’itérateur ou de l’accesseur `get` peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="ed6a6-115">Utilisez une instruction `yield break` pour terminer l'itération.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="ed6a6-116">Tous les exemples de cette rubrique, à l’exception de l’exemple de l’itérateur simple, incluent des directives [using](../../language-reference/keywords/using-directive.md) pour les espaces de noms `System.Collections` et `System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="ed6a6-117">Itérateur simple</span><span class="sxs-lookup"><span data-stu-id="ed6a6-117">Simple Iterator</span></span>

<span data-ttu-id="ed6a6-118">L’exemple suivant comprend une seule instruction `yield return` qui se trouve dans une boucle [for](../../language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="ed6a6-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="ed6a6-119">Dans `Main`, chaque itération du corps d’instruction `foreach` crée un appel à la fonction d’itérateur, qui poursuit avec l’instruction `yield return` suivante.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a><span data-ttu-id="ed6a6-120">Création d’une classe de collection</span><span class="sxs-lookup"><span data-stu-id="ed6a6-120">Creating a Collection Class</span></span>

<span data-ttu-id="ed6a6-121">Dans l’exemple suivant, la classe `DaysOfTheWeek` implémente l’interface <xref:System.Collections.IEnumerable>, ce qui nécessite la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="ed6a6-122">Le compilateur appelle implicitement la méthode `GetEnumerator`, qui retourne un <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="ed6a6-123">La méthode `GetEnumerator` retourne chaque chaîne une à la fois en utilisant l’instruction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

<span data-ttu-id="ed6a6-124">L’exemple suivant crée une classe `Zoo` qui contient une collection d’animaux.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="ed6a6-125">L’instruction `foreach` qui fait référence à l’instance de classe (`theZoo`) appelle implicitement la méthode `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="ed6a6-126">Les instructions `foreach` qui font référence aux propriétés `Birds` et `Mammals` utilisent la méthode d’itérateur nommée `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="ed6a6-127">Utilisation d’itérateurs avec une liste générique</span><span class="sxs-lookup"><span data-stu-id="ed6a6-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="ed6a6-128">Dans l’exemple suivant, la classe générique <xref:System.Collections.Generic.Stack%601> implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="ed6a6-129">La méthode <xref:System.Collections.Generic.Stack%601.Push%2A> affecte des valeurs à un tableau de type `T`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="ed6a6-130">La méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retourne les valeurs de tableau à l’aide de l’instruction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="ed6a6-131">Outre la méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> générique, la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> non générique doit également être implémentée.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="ed6a6-132">C’est parce que <xref:System.Collections.Generic.IEnumerable%601> hérite de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="ed6a6-133">L’implémentation non générique s’en remet à l’implémentation générique.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="ed6a6-134">L’exemple utilise des itérateurs nommés pour prendre en charge différentes façons d’itérer au sein de la même collection de données.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="ed6a6-135">Ces itérateurs nommés sont les propriétés `TopToBottom` et `BottomToTop`, et la méthode `TopN`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="ed6a6-136">La propriété `BottomToTop` utilise un itérateur dans un accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a><span data-ttu-id="ed6a6-137">Informations sur la syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed6a6-137">Syntax Information</span></span>

<span data-ttu-id="ed6a6-138">Un itérateur peut être une méthode ou un accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="ed6a6-139">Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un finaliseur statique.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="ed6a6-140">Une conversion implicite doit exister du `yield return` type d’expression `IEnumerable<T>` dans la déclaration à l’argument de type pour le retourné par l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="ed6a6-141">En C#, une méthode d’itérateur ne peut avoir aucun paramètre `in`, `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="ed6a6-142">Dans C, `yield` n’est pas un mot réservé et n’a une signification particulière que lorsqu’il est utilisé avant un `return` ou `break` un mot clé.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="ed6a6-143">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="ed6a6-143">Technical Implementation</span></span>

<span data-ttu-id="ed6a6-144">Bien que vous écriviez un itérateur comme une méthode, le compilateur le traduit en une classe imbriquée, qui est en réalité une machine à états.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="ed6a6-145">Cette classe fait le suivi de la position de l’itérateur tant que la boucle `foreach` du code client se poursuit.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="ed6a6-146">Pour voir ce que fait le compilateur, vous pouvez utiliser l’outil Ildasm.exe et afficher le code du langage intermédiaire Microsoft généré pour une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="ed6a6-147">Quand vous créez un itérateur pour une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md), vous n’avez pas besoin d’implémenter l’ensemble de l’interface <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="ed6a6-148">Quand le compilateur détecte l’itérateur, il génère automatiquement les méthodes `Current`, `MoveNext` et `Dispose` de l’interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="ed6a6-149">À chaque itération successive de la boucle `foreach` (ou de l’appel direct à `IEnumerator.MoveNext`), le corps du code de l’itérateur suivant reprend après l’instruction `yield return` précédente.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="ed6a6-150">Il continue ensuite jusqu’à l’instruction `yield return` suivante, jusqu’à atteindre la fin du corps de l’itérateur ou jusqu’à rencontrer une instruction `yield break`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="ed6a6-151">Les itérateurs ne prennent pas en charge la méthode <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ed6a6-152">Pour réitérer à partir du début, vous devez obtenir un nouvel itérateur.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="ed6a6-153">L’appel de <xref:System.Collections.IEnumerator.Reset%2A> sur l’itérateur retourné par une méthode d’itérateur lève un <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="ed6a6-154">Pour plus d’informations, consultez la [spécification du langage C#](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="ed6a6-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="ed6a6-155">Utilisation d’itérateurs</span><span class="sxs-lookup"><span data-stu-id="ed6a6-155">Use of Iterators</span></span>

<span data-ttu-id="ed6a6-156">Les itérateurs vous permettent de conserver la simplicité d’une boucle `foreach` quand vous avez besoin d’utiliser un code complexe pour remplir la séquence d’une liste.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="ed6a6-157">Ceci peut être utile quand vous voulez faire les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed6a6-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="ed6a6-158">Modifier la séquence de la liste après la première itération de la boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="ed6a6-159">Éviter de charger entièrement une grande liste avant la première itération d’une boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="ed6a6-160">Une extraction paginée pour charger un lot de lignes d’une table est un exemple.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="ed6a6-161">Un autre exemple est la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , qui implémente les itérateurs dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="ed6a6-162">Encapsuler la création de la liste dans l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="ed6a6-163">Dans la méthode d’itérateur, vous pouvez créer la liste et générer ensuite chaque résultat dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="ed6a6-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed6a6-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed6a6-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="ed6a6-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="ed6a6-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="ed6a6-166">Rendement</span><span class="sxs-lookup"><span data-stu-id="ed6a6-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="ed6a6-167">Utiliser foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="ed6a6-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="ed6a6-168">Génériques</span><span class="sxs-lookup"><span data-stu-id="ed6a6-168">Generics</span></span>](../generics/index.md)
