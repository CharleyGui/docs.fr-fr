---
title: Exemples de requêtes de chaîne (C#)-LINQ to XML
description: Découvrez ce qui se passe lorsque vous chaînez deux requêtes qui utilisent toutes deux l’exécution et l’évaluation différées.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553492"
---
# <a name="chain-queries-example-c-linq-to-xml"></a>Exemples de requêtes de chaîne (C#) (LINQ to XML)

Cet exemple s’appuie sur l’exemple dans l' [exemple d’exécution différée](deferred-execution-example.md) et montre ce qui se passe lorsque vous chaînez deux requêtes qui utilisent toutes deux l’exécution différée et l’évaluation différée.

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a>Exemple : ajouter une deuxième méthode d’extension qui utilise `yield return` pour différer l’exécution

Dans cet exemple, une autre méthode d’extension est introduite, `AppendString` , qui ajoute une chaîne spécifiée à chaque chaîne de la collection source, puis génère la chaîne modifiée.

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
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

Dans cet exemple, vous pouvez constater que chaque méthode d'extension opère l'une après l'autre pour chaque élément de la collection source.

Il doit être clair, au vu de cet exemple, que bien que nous ayons chaîné des requêtes qui produisent des collections, aucune collection intermédiaire n'est matérialisée. Au lieu de cela, chaque élément est passé d'une méthode différée à la suivante. L'encombrement mémoire est par conséquent beaucoup plus faible par rapport à une approche qui consisterait à prendre d'abord un tableau de chaînes, à créer un deuxième tableau de chaînes converties en majuscules, puis à créer un troisième tableau de chaînes où des points d'exclamations sont ajoutés à chaque chaîne.

L’article suivant de ce didacticiel illustre la matérialisation intermédiaire :

- [Matérialisation intermédiaire (C#)](intermediate-materialization.md)

## <a name="see-also"></a>Voir aussi

- [Exécution différée et évaluation différée](deferred-execution-lazy-evaluation.md)
