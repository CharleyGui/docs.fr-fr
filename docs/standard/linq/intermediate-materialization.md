---
title: Matérialisation intermédiaire (C#)
description: Découvrez comment l’utilisation de certains opérateurs de requête standard peut entraîner la matérialisation des collections dans une requête et modifier radicalement la mémoire et le profil de performances de votre application.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552413"
---
# <a name="intermediate-materialization-c"></a>Matérialisation intermédiaire (C#)

Si vous n’êtes pas prudent, vous pouvez, dans certains cas, modifier radicalement le profil de mémoire et de performances de votre application en provoquant la matérialisation prématurée de collections dans vos requêtes. Certains opérateurs de requête standard provoquent la matérialisation de leur collection source avant de générer un seul élément. Par exemple, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> itère au sein de l'ensemble de sa collection source, trie tous les éléments, puis génère le premier élément. Cela signifie qu’il est coûteux d’avoir le premier élément d’une collection ordonnée ; chaque élément par la suite n’est pas onéreux. Tout cela est logique : il serait impossible pour cet opérateur de requête de faire autrement.

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a>Exemple : ajouter une méthode qui appelle `ToList` , provoquant la matérialisation

Cet exemple modifie l’exemple dans [exemples de requêtes de chaîne (C#)](chain-queries-example.md): la `AppendString` méthode est modifiée pour appeler <xref:System.Linq.Enumerable.ToList%2A> avant d’itérer au sein de la source, ce qui provoque la matérialisation.

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
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
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
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

Dans cet exemple, on observe que l'appel de <xref:System.Linq.Enumerable.ToList%2A> force `AppendString` à parcourir l'ensemble de sa source avant de générer le premier élément. Si la source est un grand tableau, cela modifie considérablement le profil de mémoire de l'application.

Les opérateurs de requête standard peuvent également être chaînés, comme indiqué dans le dernier article de ce didacticiel :

- [Chaîner des opérateurs de requête standard (C#)](chain-standard-query-operators-together.md)

## <a name="see-also"></a>Voir aussi

- [Exécution différée et évaluation différée](deferred-execution-lazy-evaluation.md)
