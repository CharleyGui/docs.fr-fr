---
title: Chaîner les opérateurs de requête standard (C#)-LINQ to XML
description: Découvrez comment chaîner des opérateurs de requête.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552376"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a>Chaîner des opérateurs de requête standard (C#) (LINQ to XML)

Les opérateurs de requête standard peuvent être chaînés ensemble. Par exemple, vous pouvez lancer l' <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> opérateur (appelé par la `where` clause) et il fonctionne de manière différée ; autrement dit, aucun résultat intermédiaire n’est matérialisé par ce dernier.

## <a name="example-interject-a-where-clause"></a>Exemple : lancer une clause WHERE

Dans cet exemple, la méthode <xref:System.Linq.Enumerable.Where%2A> est appelée avant `ConvertCollectionToUpperCase`. La méthode <xref:System.Linq.Enumerable.Where%2A> opère presque exactement de la même façon que les méthodes différées utilisées dans les exemples précédents de ce didacticiel, `ConvertCollectionToUpperCase` et `AppendString`.

L’une des différences est que dans ce cas, la méthode itère au sein de <xref:System.Linq.Enumerable.Where%2A> sa collection source, détermine que le premier élément ne passe pas le prédicat, puis obtient l’élément suivant qui passe. Elle génère ensuite le deuxième élément.

Toutefois, l’idée de base est la même : les collections intermédiaires ne sont pas matérialisées, sauf si elles doivent l’être.

Lorsque des expressions de requête sont utilisées, elles sont converties en appels aux opérateurs de requête standard, et les mêmes principes s’appliquent.

Tous les exemples de cette section qui interrogent des documents Office Open XML utilisent le même principe. L’exécution et l’évaluation différées sont des concepts fondamentaux que vous devez comprendre pour utiliser LINQ et LINQ to XML.

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            where s.CompareTo("D") >= 0
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

Cet exemple produit la sortie suivante :

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

Il s’agit du dernier article du didacticiel [: chaînage de requêtes (C#)](chain-queries-example.md) .
