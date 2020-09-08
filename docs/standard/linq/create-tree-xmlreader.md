---
title: Comment créer une arborescence à partir d’un LINQ to XML XmlReader
description: Vous pouvez utiliser un XmlReader en C# ou Visual Basic pour lire XML et créer une arborescence XML. Vous devez positionner correctement le XmlReader sur un nœud d’élément.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553199"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a>Création d’une arborescence à partir d’un XmlReader (LINQ to XML)

Cet article explique comment créer une arborescence XML directement à partir d’un <xref:System.Xml.XmlReader> en C# ou d’un Visual Basic. Pour créer un <xref:System.Xml.Linq.XElement> à partir d’un <xref:System.Xml.XmlReader> , vous positionnez le <xref:System.Xml.XmlReader> sur un nœud d’élément. L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée. Pour éviter de telles erreurs, placez le <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de <xref:System.Xml.XmlReader> .

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a>Exemple : charger un objet XElement à partir d’un objet XmlReader

Cet exemple utilise le document XML [exemple de fichier XML : livres](sample-xml-file-books.md).

Le code suivant crée un <xref:System.Xml.XmlReader> objet, lit les nœuds jusqu’à ce qu’il trouve le premier nœud d’élément et charge l' <xref:System.Xml.Linq.XElement> objet.

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

Cet exemple produit la sortie suivante :

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a>Voir aussi

- [XML Parse](parse-string.md)
