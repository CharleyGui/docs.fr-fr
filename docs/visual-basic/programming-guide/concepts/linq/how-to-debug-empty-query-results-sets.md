---
title: 'Procédure : déboguer des ensembles de résultats de requête vides'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: b2059ccd4638d2fb77c524773cb4bd50f721b5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398036"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Procédure : déboguer des ensembles de résultats de requête vides (Visual Basic)

L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.

Le premier ensemble d'exemples dans cette rubrique illustre le chargement de code XML dans un espace de noms par défaut et son interrogation incorrecte.

Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.

Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).

## <a name="example"></a>Exemple

Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

Cet exemple génère le résultat suivant :

```console
Result set follows:
End of result set
```

## <a name="example"></a>Exemple

Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.

La solution consiste à déclarer et à initialiser un espace de noms global par défaut. Cela place toutes les propriétés XML dans l'espace de noms par défaut. Aucune autre modification n'est nécessaire pour que l'exemple fonctionne correctement.

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

Cet exemple génère le résultat suivant :

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Voir aussi

- [Requêtes de base (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
