---
title: Délégués et expressions lambda
description: Découvrez comment les délégués, qui définissent un type spécifiant une signature de méthode particulière, peuvent être appelés directement ou passés à une autre méthode et appelés.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 43e896bfe267299d3b0cb12a8f71e42fe2c87a88
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280788"
---
# <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Les délégués définissent un type qui spécifie une signature de méthode particulière. Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée. L’exemple suivant montre l’utilisation des délégués.

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* La ligne `public delegate string Reverse(string s);` crée un type délégué d’une certaine signature : dans notre exemple, une méthode qui prend un paramètre de type chaîne, puis retourne un paramètre de type chaîne.
* La méthode `static string ReverseString(string s)`, qui a exactement la même signature que le type délégué défini, implémente le délégué.
* La ligne `Reverse rev = ReverseString;` montre que vous pouvez affecter une méthode à une variable du type délégué correspondant.
* La ligne `Console.WriteLine(rev("a string"));` montre comment utiliser une variable d’un type délégué pour appeler le délégué.

Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer. Ces types sont `Func<>` , `Action<>` et `Predicate<>` , et ils peuvent être utilisés sans avoir à définir de nouveaux types délégués. Il existe quelques différences entre les trois types qui sont à faire avec la manière dont ils étaient destinés à être utilisés :

* `Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué. La méthode qu’elle encapsule ne retourne pas de valeur.
* `Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent. Les projections sont un bon exemple. La méthode qu’il encapsule retourne une valeur spécifiée.
* `Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué. Elle peut également être écrite sous la forme d’un `Func<T, bool>` , ce qui signifie que la méthode retourne une valeur booléenne.

Nous pouvons maintenant reprendre notre exemple ci-dessus et le réécrire à l’aide du délégué `Func<>` au lieu d’un type personnalisé. Le programme continue à s’exécuter exactement de la même façon.

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode `Main`. .NET Framework 2,0 a introduit le concept de *délégués anonymes*, qui vous permettent de créer des délégués « Inline » sans avoir à spécifier de type ou de méthode supplémentaire.

Dans l’exemple suivant, un délégué anonyme filtre une liste uniquement sur les nombres pairs, puis les imprime sur la console.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué. Mais au lieu d’être une définition distincte, nous l’avons introduite _ad hoc_ dans notre appel à la <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> méthode.

Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile. C’est là que les *expressions lambda* interviennent. Les expressions lambda, ou simplement des « lambdas », ont été introduites en C# 3,0 comme un des blocs de construction de base de LINQ (Language Integrated Query). Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués. Elles déclarent une signature et un corps de méthode, mais n’ont pas d’identité formelle propre, sauf si elles sont assignées à un délégué. Contrairement aux délégués, elles peuvent être directement affectées comme côté gauche de l’inscription d’un événement, ou dans plusieurs clauses et méthodes LINQ.

Dans la mesure où une expression lambda est simplement une autre façon de spécifier un délégué, nous pouvons réécrire l’exemple ci-dessus pour utiliser une expression lambda au lieu d’un délégué anonyme.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

Dans l’exemple précédent, l’expression lambda utilisée est `i => i % 2 == 0`. Là encore, il s’agit simplement d’une syntaxe pratique pour l’utilisation de délégués. Ce qui se passe en coulisses est semblable à ce qui se passe avec le délégué anonyme.

Comme les expressions lambda sont juste des délégués, elles peuvent servir de gestionnaire d’événements sans aucun problème, comme l’illustre l’extrait de code suivant.

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

Dans ce contexte, l’opérateur `+=` est utilisé pour s’abonner à un [événement](../csharp/language-reference/keywords/event.md). Pour plus d’informations, consultez [Comment s’abonner et annuler l’abonnement à des événements](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Ressources et informations supplémentaires

* [Délégués](../csharp/programming-guide/delegates/index.md)
* [Fonctions anonymes](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Expressions lambda](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
