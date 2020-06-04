---
title: Refactorisation dans des fonctions pures
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413477"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refactorisation dans des fonctions pures (Visual Basic)

L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.

Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :

- Elle n'a aucun effet secondaire. La fonction ne change aucune variable et aucune donnée de tout type en dehors de la fonction.

- Elle est cohérente. Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.

 L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes. De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.

Cette rubrique explique ce qu'est et ce que n'est pas une fonction pure. Le didacticiel [Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) montre comment manipuler un document WordprocessingML et propose deux exemples de refactorisation à l’aide d’une fonction pure.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Suppression des effets secondaires et des dépendances externes

Les exemples suivants comparent deux fonctions non pures et une fonction pure.

### <a name="non-pure-function-that-changes-a-class-member"></a>Fonction non pure qui modifie un membre de classe

Dans le code suivant, la fonction `HyphenatedConcat` n'est pas pure car elle modifie le membre de données `aMember` dans la classe :

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

Ce code génère la sortie suivante :

```console
StringOne-StringTwo
```

Notez qu’il est inutile que les données modifiées aient `public` ou `private` accèdent à, ou qu’il s’agisse d’un `shared` membre ou d’un membre d’instance. Une fonction pure ne change aucune donnée en dehors de la fonction.

### <a name="non-pure-function-that-changes-an-argument"></a>Fonction non pure qui modifie un argument

En outre, la version suivante de cette même fonction n'est pas pure car elle modifie le contenu de son paramètre, `sb`.

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

Cette version du programme génère la même sortie que la première version, car la fonction `HyphenatedConcat` a modifié la valeur (l'état) de son premier paramètre en appelant la fonction membre <xref:System.Text.StringBuilder.Append%2A>. Notez que cette altération a lieu en dépit du fait que `HyphenatedConcat` utilise le passage de paramètre avec appel par valeur.

> [!IMPORTANT]
> Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée. Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet). L'appel par référence n'est pas forcément nécessaire pour qu'une fonction modifie un paramètre.

### <a name="pure-function"></a>Fonction pure

Cette autre version du programme montre comment implémenter la fonction `HyphenatedConcat` en tant que fonction pure.

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

Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`. Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2`.

L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures. Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.

## <a name="standard-query-operators"></a>Opérateurs de requête standard

L'une des caractéristiques importantes des opérateurs de requête standard est qu'ils sont implémentés en tant que fonctions pures.

Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md).

## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Programmation fonctionnelle et programmation impérative (Visual Basic)](functional-programming-vs-imperative-programming.md)
