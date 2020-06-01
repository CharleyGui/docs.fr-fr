---
title: Effectuer une itération dans des collections (C#)
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 15b77fd11c0ff606119425ec7aae8e7127315e82
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240692"
---
# <a name="iterators-c"></a>Itérateurs (C#)

Un *itérateur* peut être utilisé pour parcourir des collections, comme des listes et des tableaux.

Une méthode d’itérateur ou un accesseur `get` effectue une itération personnalisée sur une collection. Une méthode d’itérateur utilise l’instruction [yield return](../../language-reference/keywords/yield.md) pour retourner chaque élément un par un. Quand une instruction `yield return` est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.

Vous consommez un itérateur à partir du code client en utilisant une instruction [foreach](../../language-reference/keywords/foreach-in.md) ou une requête LINQ.

Dans l’exemple suivant, la première itération de la boucle `foreach` fait que l’exécution continue dans la méthode d’itérateur `SomeNumbers`, jusqu’à ce que la première instruction `yield return` soit atteinte. Cette itération retourne la valeur 3, et l’emplacement actif dans la méthode d’itérateur est mémorisé. Dans l’itération suivante de la boucle, l’exécution de la méthode d’itérateur continue là où elle s’était arrêtée, et s’arrête de nouveau quand elle atteint une instruction `yield return`. Cette itération retourne la valeur 5, et l’emplacement actif dans la méthode d’itérateur est mémorisé. La boucle se termine quand la fin de la méthode d’itérateur est atteinte.

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

Le type de retour d’une méthode d’itérateur ou de l’accesseur `get` peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

Utilisez une instruction `yield break` pour terminer l'itération.

> [!NOTE]
> Tous les exemples de cette rubrique, à l’exception de l’exemple de l’itérateur simple, incluent des directives [using](../../language-reference/keywords/using-directive.md) pour les espaces de noms `System.Collections` et `System.Collections.Generic`.

## <a name="simple-iterator"></a>Itérateur simple

L’exemple suivant comprend une seule instruction `yield return` qui se trouve dans une boucle [for](../../language-reference/keywords/for.md). Dans `Main`, chaque itération du corps d’instruction `foreach` crée un appel à la fonction d’itérateur, qui poursuit avec l’instruction `yield return` suivante.

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

## <a name="creating-a-collection-class"></a>Création d’une classe de collection

Dans l’exemple suivant, la classe `DaysOfTheWeek` implémente l’interface <xref:System.Collections.IEnumerable>, ce qui nécessite la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Le compilateur appelle implicitement la méthode `GetEnumerator`, qui retourne un <xref:System.Collections.IEnumerator>.

La méthode `GetEnumerator` retourne chaque chaîne une à la fois en utilisant l’instruction `yield return`.

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

L’exemple suivant crée une classe `Zoo` qui contient une collection d’animaux.

L’instruction `foreach` qui fait référence à l’instance de classe (`theZoo`) appelle implicitement la méthode `GetEnumerator`. Les instructions `foreach` qui font référence aux propriétés `Birds` et `Mammals` utilisent la méthode d’itérateur nommée `AnimalsForType`.

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

## <a name="using-iterators-with-a-generic-list"></a>Utilisation d’itérateurs avec une liste générique

Dans l’exemple suivant, la classe générique <xref:System.Collections.Generic.Stack%601> implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601>. La méthode <xref:System.Collections.Generic.Stack%601.Push%2A> affecte des valeurs à un tableau de type `T`. La méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retourne les valeurs de tableau à l’aide de l’instruction `yield return`.

Outre la méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> générique, la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> non générique doit également être implémentée. C’est parce que <xref:System.Collections.Generic.IEnumerable%601> hérite de <xref:System.Collections.IEnumerable>. L’implémentation non générique s’en remet à l’implémentation générique.

L’exemple utilise des itérateurs nommés pour prendre en charge différentes façons d’itérer au sein de la même collection de données. Ces itérateurs nommés sont les propriétés `TopToBottom` et `BottomToTop`, et la méthode `TopN`.

La propriété `BottomToTop` utilise un itérateur dans un accesseur `get`.

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

## <a name="syntax-information"></a>Informations sur la syntaxe

Un itérateur peut être une méthode ou un accesseur `get`. Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un finaliseur statique.

Une conversion implicite doit exister du type d’expression dans l' `yield return` instruction à l’argument de type pour le `IEnumerable<T>` retourné par l’itérateur.

En C#, une méthode d’itérateur ne peut avoir aucun paramètre `in`, `ref` ou `out`.

En C#, `yield` n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’il est utilisé avant un `return` `break` mot clé ou.

## <a name="technical-implementation"></a>Implémentation technique

Bien que vous écriviez un itérateur comme une méthode, le compilateur le traduit en une classe imbriquée, qui est en réalité une machine à états. Cette classe fait le suivi de la position de l’itérateur tant que la boucle `foreach` du code client se poursuit.

Pour voir ce que fait le compilateur, vous pouvez utiliser l’outil Ildasm.exe et afficher le code du langage intermédiaire Microsoft généré pour une méthode d’itérateur.

Quand vous créez un itérateur pour une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md), vous n’avez pas besoin d’implémenter l’ensemble de l’interface <xref:System.Collections.IEnumerator>. Quand le compilateur détecte l’itérateur, il génère automatiquement les méthodes `Current`, `MoveNext` et `Dispose` de l’interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

À chaque itération successive de la boucle `foreach` (ou de l’appel direct à `IEnumerator.MoveNext`), le corps du code de l’itérateur suivant reprend après l’instruction `yield return` précédente. Il continue ensuite jusqu’à l’instruction `yield return` suivante, jusqu’à atteindre la fin du corps de l’itérateur ou jusqu’à rencontrer une instruction `yield break`.

Les itérateurs ne prennent pas en charge la méthode <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>. Pour réitérer à partir du début, vous devez obtenir un nouvel itérateur. L’appel de <xref:System.Collections.IEnumerator.Reset%2A> sur l’itérateur retourné par une méthode d’itérateur lève un <xref:System.NotSupportedException>.

Pour plus d’informations, consultez la [spécification du langage C#](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Utilisation d’itérateurs

Les itérateurs vous permettent de conserver la simplicité d’une boucle `foreach` quand vous avez besoin d’utiliser un code complexe pour remplir la séquence d’une liste. Ceci peut être utile quand vous voulez faire les opérations suivantes :

- Modifier la séquence de la liste après la première itération de la boucle `foreach`.

- Éviter de charger entièrement une grande liste avant la première itération d’une boucle `foreach`. Une extraction paginée pour charger un lot de lignes d’une table est un exemple. Un autre exemple est la <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> méthode, qui implémente les itérateurs dans .net.

- Encapsuler la création de la liste dans l’itérateur. Dans la méthode d’itérateur, vous pouvez créer la liste et générer ensuite chaque résultat dans une boucle.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Utiliser foreach avec des tableaux](../arrays/using-foreach-with-arrays.md)
- [Génériques](../generics/index.md)
