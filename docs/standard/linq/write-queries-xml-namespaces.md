---
title: Comment écrire des requêtes sur du code XML dans des espaces de noms-LINQ to XML
description: Pour écrire une requête sur du code XML qui se trouve dans un espace de noms, vous utilisez des objets XName qui possèdent l’espace de noms correct. Découvrez comment procéder en C# et Visual Basic, et comment créer des requêtes.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552457"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a>Comment écrire des requêtes sur du code XML dans des espaces de noms (LINQ to XML)

Pour écrire une requête sur du code XML qui se trouve dans un espace de noms, vous devez utiliser des <xref:System.Xml.Linq.XName> objets qui ont l’espace de noms correct.

Pour C#, l'approche la plus courante consiste à initialiser un objet <xref:System.Xml.Linq.XNamespace> à l'aide d'une chaîne contenant l'URI, puis à utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local.

Par Visual Basic, l’approche la plus courante consiste à définir un espace de noms global, puis à utiliser des littéraux XML et des propriétés XML qui utilisent l’espace de noms global. Vous pouvez définir un espace de noms par défaut global, auquel cas les éléments dans les littéraux XML seront par défaut dans l'espace de noms. Vous pouvez également définir un espace de noms global avec un préfixe, puis utiliser le préfixe comme requis dans les littéraux XML et les propriétés XML. Comme avec d'autres formes de code XML, les attributs ne sont jamais dans aucun espace de noms par défaut.

Le premier exemple de cet article montre comment créer une arborescence XML dans un espace de noms par défaut. Le deuxième montre comment créer une arborescence XML dans un espace de noms avec un préfixe.

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a>Exemple : créer une arborescence dans un espace de noms par défaut et récupérer des éléments

L’exemple suivant crée une arborescence XML qui se trouve dans un espace de noms par défaut, puis récupère une collection d’éléments.

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
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
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a>Exemple : créer une arborescence dans un espace de noms avec un préfixe et récupérer des éléments

En C#, vous écrivez des requêtes de la même façon que vous écriviez des requêtes sur une arborescence XML qui utilise un espace de noms avec un préfixe ou sur une arborescence XML avec un espace de noms par défaut.

L’exemple suivant crée une arborescence XML qui se trouve dans un espace de noms avec un préfixe, puis récupère une collection d’éléments.

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
1
2
3
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)
