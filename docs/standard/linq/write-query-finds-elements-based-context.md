---
title: Comment écrire une requête qui recherche des éléments en fonction du contexte-LINQ to XML
description: Écrire une requête qui sélectionne des éléments en fonction du contexte ; par exemple, filtrez les résultats en fonction des éléments frères précédents ou suivants.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 2c51a790a2a8adef565f186992a6a3faa5f102ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550459"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-linq-to-xml"></a>Comment écrire une requête qui recherche des éléments en fonction du contexte (LINQ to XML)

Parfois, vous devez écrire une requête qui sélectionne des éléments en fonction de leur contexte. Par exemple, vous souhaiterez peut-être filtrer en fonction des éléments frères précédents ou suivants, ou sur des éléments enfants ou ancêtres.

Vous pouvez pour cela écrire une requête et utiliser ses résultats dans la clause `where`. Si vous devez d’abord effectuer un test par rapport à null, puis tester la valeur, il est plus pratique d’exécuter la requête dans une `let` clause, puis d’utiliser les résultats dans la `where` clause.

## <a name="example-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a>Exemple : sélectionner `p` des éléments qui sont immédiatement suivis d’un `ul` élément

L'exemple suivant sélectionne tous les éléments `p` qui sont suivis immédiatement d'un élément `ul`.

```csharp
XElement doc = XElement.Parse(@"<Root>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

IEnumerable<XElement> items =
    from e in doc.Descendants("p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name.LocalName == "ul"
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Dim doc As XElement = _
    <Root>
        <p id='1'/>
        <ul>abc</ul>
        <Child>
            <p id='2'/>
            <notul/>
            <p id='3'/>
            <ul>def</ul>
            <p id='4'/>
        </Child>
        <Child>
            <p id='5'/>
            <notul/>
            <p id='6'/>
            <ul>abc</ul>
            <p id='7'/>
        </Child>
    </Root>

Dim items As IEnumerable(Of XElement) = _
    From e In doc...<p> _
    Let z = e.ElementsAfterSelf().FirstOrDefault() _
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _
    Select e

For Each e As XElement In items
    Console.WriteLine("id = {0}", e.@<id>)
Next
```

Cet exemple produit la sortie suivante :

```output
id = 1
id = 3
id = 6
```

## <a name="example-in-a-namespace-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a>Exemple : dans un espace de noms, sélectionnez `p` les éléments qui sont immédiatement suivis par un `ul` élément

L’exemple suivant illustre la même requête que ci-dessus, mais pour le code XML qui se trouve dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

XNamespace ad = "http://www.adatum.com";

IEnumerable<XElement> items =
    from e in doc.Descendants(ad + "p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name == ad.GetName("ul")
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim doc As XElement = _
            <Root>
                <p id='1'/>
                <ul>abc</ul>
                <Child>
                    <p id='2'/>
                    <notul/>
                    <p id='3'/>
                    <ul>def</ul>
                    <p id='4'/>
                </Child>
                <Child>
                    <p id='5'/>
                    <notul/>
                    <p id='6'/>
                    <ul>abc</ul>
                    <p id='7'/>
                </Child>
            </Root>

        Dim items As IEnumerable(Of XElement) = _
            From e In doc...<p> _
            Let z = e.ElementsAfterSelf().FirstOrDefault() _
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _
            Select e

        For Each e As XElement In items
            Console.WriteLine("id = {0}", e.@<id>)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
id = 1
id = 3
id = 6
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [Requêtes de base (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
