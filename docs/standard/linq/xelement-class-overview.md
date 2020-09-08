---
title: Vue d’ensemble de la classe XElement
description: La classe XElement représente des éléments XML. Vous pouvez l’utiliser pour créer et modifier des éléments, ajouter des attributs et des enfants, et pour sérialiser.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552524"
---
# <a name="xelement-class-overview"></a>Vue d’ensemble de la classe XElement

La <xref:System.Xml.Linq.XElement> classe est l’une des classes fondamentales de LINQ to XML. Elle représente un élément XML. La liste suivante montre ce que vous pouvez utiliser pour :

- Créer des éléments.
- Modifiez le contenu de l’élément.
- Ajoutez, modifiez ou supprimez des éléments enfants.
- Ajoutez des attributs à un élément.
- Sérialiser le contenu d’un élément sous forme de texte.

Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.

Cet article décrit les fonctionnalités fournies par la <xref:System.Xml.Linq.XElement> classe.

## <a name="construct-xml-trees"></a>Construire des arborescences XML

Vous pouvez construire des arborescences XML de différentes façons, notamment :

- Vous pouvez construire une arborescence XML dans du code. Pour plus d’informations, consultez [arborescences XML](functional-construction.md).
- Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL). Pour plus d’informations, consultez [Parse XML](parse-string.md).
- Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence. Pour plus d'informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.
- Si vous avez un module qui peut écrire du contenu dans un <xref:System.Xml.XmlWriter> , vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.CreateWriter%2A> méthode pour créer un writer, passer l’enregistreur au module, puis utiliser le contenu écrit dans <xref:System.Xml.XmlWriter> pour remplir l’arborescence XML.

L’exemple suivant crée une arborescence. La version C# utilise des créations d’éléments imbriqués. Vous pouvez utiliser la même technique dans Visual Basic, mais cet exemple utilise des littéraux XML.

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

Vous pouvez également utiliser une requête LINQ to XML pour remplir une arborescence XML, comme illustré dans l’exemple suivant :

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

Cet exemple produit la sortie suivante :

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a>Sérialiser des arborescences XML

Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.

Pour plus d’informations, consultez [sérialiser des arborescences XML](preserve-white-space-serializing.md).

## <a name="retrieve-xml-data-via-axis-methods"></a>Récupérer des données XML à l’aide de méthodes d’axe

Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres. LINQ to XML requêtes opèrent sur des méthodes d’axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.

Pour plus d’informations, consultez [LINQ to XML vue d’ensemble des axes](linq-xml-axes-overview.md).

## <a name="query-xml-trees"></a>Interroger des arborescences XML

Vous pouvez écrire des LINQ to XML des requêtes qui extraient des données d’une arborescence XML.

Pour plus d’informations, consultez [vue d’ensemble de la requête d’arborescences XML](query-xml-trees-overview.md).

## <a name="modify-xml-trees"></a>Modifier des arborescences XML

Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs. Vous pouvez également supprimer un élément de son parent.

Pour plus d’informations, consultez [modifier des arborescences XML](in-memory-xml-tree-modification-vs-functional-construction.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation LINQ to XML](functional-vs-procedural-programming.md)
