---
title: Refactoriser dans des fonctions pures-LINQ to XML
description: Découvrez les fonctions pures et comment les utiliser pour Refactoriser le code.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553773"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a>Refactoriser dans des fonctions pures (LINQ to XML)

L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.

> [!NOTE]
> La nomenclature courante dans la programmation fonctionnelle consiste à refactoriser les programmes à l'aide de fonctions pures. En Visual Basic et C++, cela correspond à l'utilisation des fonctions dans les langages respectifs. Toutefois, en C#, les fonctions portent le nom de méthodes. Pour les besoins de cette discussion, une fonction pure est implémentée en tant que méthode en C#.

Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :

- Elle n'a aucun effet secondaire. La fonction ne modifie pas les variables ou les données de tout type en dehors de la fonction.
- Elle est cohérente. Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.

L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes. De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.

Cet article explique ce qu’est une fonction pure et ce qu’elle ne fait pas. Le didacticiel [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md) montre comment manipuler un document WordprocessingML et propose deux exemples de refactorisation à l’aide d’une fonction pure.

Les exemples suivants comparent deux fonctions non pures et une fonction pure.

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a>Exemple : implémenter une fonction non pure qui modifie un membre de classe statique

Dans le code suivant, la `HyphenatedConcat` fonction n’est pas une fonction pure, car elle modifie le `aMember` membre de classe statique :

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
StringOne-StringTwo
```

Notez qu’il est inutile de savoir si les données modifiées `public` ont `private` un accès à ou un membre, un membre ou un membre d' `static` `shared` instance. Une fonction pure ne change aucune donnée en dehors de la fonction.

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a>Exemple : implémenter une fonction non pure qui modifie un paramètre

En outre, la version suivante de cette même fonction n’est pas pure car elle modifie le contenu de son paramètre, `sb` .

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

Cette version du programme génère la même sortie que la première version, car la fonction `HyphenatedConcat` a modifié la valeur (l'état) de son premier paramètre en appelant la fonction membre <xref:System.Text.StringBuilder.Append%2A>. Notez que cette modification se produit en dépit du fait que `HyphenatedConcat` utilise le passage de paramètre appel par valeur.

> [!IMPORTANT]
> Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée. Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet). L’appel par référence n’est pas nécessairement requis pour qu’une fonction modifie un paramètre.

## <a name="example-implement-a-pure-function"></a>Exemple : implémenter une fonction pure

Cette autre version du programme montre comment implémenter la fonction `HyphenatedConcat` en tant que fonction pure.

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`. Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2` .

L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures. Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.

## <a name="standard-query-operators"></a>Opérateurs de requête standard

L’une des caractéristiques importantes des opérateurs de requête standard est qu’ils sont implémentés en tant que fonctions pures.

Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) et [vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures](introduction-pure-functional-transformations.md)
- [Programmation fonctionnelle et programmation impérative](functional-vs-imperative-programming.md)
