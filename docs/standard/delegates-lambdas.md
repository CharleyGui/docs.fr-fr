---
title: Délégués et expressions lambda
description: Découvrez comment les délégués définissent un type, qui spécifie une signature de méthode particulière, qui peut être appelée directement ou passée à une autre méthode et appelée.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 34bfa4c6007ec771f784e927675f4e24d52e194f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391232"
---
# <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Les délégués définissent un type, qui spécifie la signature d’une méthode particulière. Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée. L’exemple suivant montre l’utilisation des délégués.

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

Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer. Il s’agit de `Func<>`, `Action<>` et `Predicate<>`. Ils peuvent être utilisés à plusieurs endroits dans les API .NET, sans avoir à définir de nouveaux types délégués. Bien sûr, il existe certaines différences entre ces trois types, comme vous pouvez le constater dans leurs signatures, qui sont principalement liées à la manière dont ils doivent être utilisés :

* `Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué. La méthode qu’il encapsule ne retourne pas une valeur.
* `Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent. C’est le cas, par exemple, des projections. La méthode qu’il encapsule renvoie une valeur spécifiée.
* `Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué. Il peut également être `Func<T, bool>`écrit comme un , ce qui signifie que la méthode retourne une valeur boolean.

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

Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode `Main`. C’est pourquoi .NET Framework 2.0 a introduit le concept des **délégués anonymes**. Grâce à eux, vous pouvez créer des délégués « inline », sans avoir à spécifier un autre type ou méthode. Vous insérez simplement la définition du délégué là où vous en avez besoin.

En guise d’exemple, nous allons utiliser notre délégué anonyme pour filtrer une liste uniquement sur les nombres pairs et les imprimer dans la console.

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

Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué. Mais au lieu d’en faire une définition distincte, nous l’avons introduit _ad hoc_ dans notre appel à la méthode <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.

Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile. C’est là que les **expressions lambda** interviennent.

Les expressions lambda ont été initialement introduites dans C# 3.0 comme l’un des principaux blocs de construction de la requête LINQ (Language-Integrated Query). Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués. Ils déclarent une signature et un organisme de méthode, mais n’ont pas leur propre identité formelle, à moins qu’ils ne soient affectés à un délégué. Contrairement aux délégués, elles peuvent être directement affectées comme côté gauche de l’inscription d’un événement, ou dans plusieurs clauses et méthodes LINQ.

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

Dans l’exemple précédent, l’expression lambda utilisée est `i => i % 2 == 0`. Là encore, il s’agit simplement d’une syntaxe **très** pratique pour l’utilisation des délégués. Par conséquent, ce qui se passe en coulisses est très proche de ce qui se passe avec le délégué anonyme.

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

Dans ce contexte, l’opérateur `+=` est utilisé pour s’abonner à un [événement](../../docs/csharp/language-reference/keywords/event.md). Pour plus d’informations, voir [Comment vous abonner et désabonner des événements](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Ressources et informations supplémentaires

* [Délégués](../../docs/csharp/programming-guide/delegates/index.md)
* [Fonctions anonymes](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Expressions lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
