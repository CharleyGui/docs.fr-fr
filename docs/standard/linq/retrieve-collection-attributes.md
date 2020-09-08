---
title: Récupération d’une collection d’attributs-LINQ to XML
description: Découvrez comment utiliser la méthode XElement. Attributes pour récupérer les attributs d’un élément.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: a15375ffd6b3af7fb9119e3321495cffa00268e4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552485"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml"></a>Comment récupérer une collection d’attributs (LINQ to XML)

Cet article présente l’utilisation de la <xref:System.Xml.Linq.XElement.Attributes%2A> méthode pour récupérer les attributs d’un élément.

## <a name="example-iterate-through-the-attributes-of-an-element"></a>Exemple : itérer au sein des attributs d’un élément

L’exemple suivant montre comment itérer au sein de la collection d’attributs d’un élément.

```csharp
XElement val = new XElement("Value",
    new XAttribute("ID", "1243"),
    new XAttribute("Type", "int"),
    new XAttribute("ConvertableTo", "double"),
    "100");
IEnumerable<XAttribute> listOfAttributes =
    from att in val.Attributes()
    select att;
foreach (XAttribute a in listOfAttributes)
    Console.WriteLine(a);
```

```vb
Dim val = _
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>
Dim listOfAttributes As IEnumerable(Of XAttribute) = _
    From att In val.Attributes() _
    Select att
For Each att As XAttribute In listOfAttributes
    Console.WriteLine(att)
Next
```

Cet exemple produit la sortie suivante :

```output
ID="1243"
Type="int"
ConvertableTo="double"
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
