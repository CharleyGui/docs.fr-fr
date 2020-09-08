---
title: Récupération d’un seul attribut-LINQ to XML
description: Récupérez un seul attribut d’un élément, en fonction du nom de l’attribut.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553659"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a>Comment récupérer un seul attribut (LINQ to XML)

Cet article explique comment récupérer un seul attribut d’un élément, étant donné le nom de l’attribut. Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.

La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a>Exemple : récupérer des valeurs d’attribut, en fonction des noms d’élément et d’attribut

L’exemple suivant utilise la <xref:System.Xml.Linq.XElement> méthode pour créer un élément nommé `PhoneNumbers` . Il recherche ensuite tous les éléments descendants nommés `Phone` et, pour chacun d’entre eux, utilise la <xref:System.Xml.Linq.XElement.Attribute%2A> méthode pour obtenir et générer la sortie de la valeur de l’attribut nommé `type` :

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

Cet exemple produit la sortie suivante :

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a>Exemple : récupérer une valeur d’attribut avec un cast

Vous pouvez récupérer la valeur d’un attribut en la castant, comme vous le feriez avec des <xref:System.Xml.Linq.XElement> objets. Cela est illustré par l'exemple suivant :

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

Cet exemple produit la sortie suivante :

```output
home
work
```

LINQ to XML fournit des opérateurs de cast explicites pour la <xref:System.Xml.Linq.XAttribute> classe à `string` , `bool` , `bool?` , `int` ,,,,,,,, `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` ,,,, `TimeSpan` `TimeSpan?` `GUID` et `GUID?` .

## <a name="example-cast-for-an-attribute-in-a-namespace"></a>Exemple : cast pour un attribut dans un espace de noms

L’exemple suivant montre le même code pour un attribut qui se trouve dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
home
work
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
