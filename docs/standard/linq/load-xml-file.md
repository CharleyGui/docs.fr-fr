---
title: Comment charger du code XML à partir d’un fichier-LINQ to XML
description: Vous pouvez utiliser la méthode XElement. Load en C# et Visual Basic pour charger un document XML à partir d’un fichier.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 7ac77205eb1f7637982e8f40d31df0a422ecba22
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553300"
---
# <a name="how-to-load-xml-from-a-file-linq-to-xml"></a>Comment charger du code XML à partir d’un fichier (LINQ to XML)

Cet article explique comment charger du code XML à partir d’un fichier en C# et Visual Basic à l’aide de la <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> méthode.

## <a name="example-load-xml-document-from-a-file"></a>Exemple : charger un document XML à partir d’un fichier

L’exemple suivant montre comment charger un document XML à partir d’un fichier en fournissant <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> avec l’URI qui fait référence au fichier. L’exemple charge books.xml et génère l’arborescence XML sur la console.

Le contenu de books.xml s’affiche dans [exemple de fichier XML : livres](sample-xml-file-books.md).

```csharp
XElement booksFromFile = XElement.Load(@"books.xml");
Console.WriteLine(booksFromFile);
```

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
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
