---
title: Portée des espaces de noms par défaut-LINQ to XML
description: Les espaces de noms par défaut tels qu’ils sont représentés dans l’arborescence XML ne sont pas dans la portée des requêtes. Voici des méthodes correctes et incorrectes pour les interroger.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553827"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a>Portée des espaces de noms par défaut (LINQ to XML)

Les espaces de noms par défaut tels qu’ils sont représentés dans l’arborescence XML ne sont pas dans la portée des requêtes. Si vous avez du code XML qui se trouve dans un espace de noms par défaut, vous devez combiner un espace de noms avec le nom local pour faire en sorte qu’un nom qualifié soit utilisé dans la requête.

Une erreur courante lors de l’interrogation d’une arborescence XML avec un espace de noms par défaut consiste à écrire la requête comme si le XML ne se trouve pas dans un espace de noms. Le premier exemple montre une requête incorrecte standard d’un espace de noms par défaut. Le deuxième affiche une requête appropriée.

## <a name="example-improper-query-of-xml-in-a-namespace"></a>Exemple : requête incorrecte de code XML dans un espace de noms

Cet exemple illustre la création de code XML dans un espace de noms et une requête incorrecte qui retourne un jeu de résultats vide.

```csharp
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
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
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

Cet exemple produit la sortie suivante :

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a>Exemple : interrogation correcte du code XML dans un espace de noms

Cet exemple illustre la création de code XML dans un espace de noms et une requête appropriée.

En C#, l’approche correcte consiste à déclarer et à initialiser un <xref:System.Xml.Linq.XNamespace> objet et à l’utiliser lors de la spécification d' <xref:System.Xml.Linq.XName> objets. Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.

L'approche correcte lors de l'utilisation de Visual Basic consiste à déclarer et à initialiser un espace de noms global par défaut. Cela place toutes les propriétés XML dans l'espace de noms par défaut.

Voici le code :

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

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
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)
