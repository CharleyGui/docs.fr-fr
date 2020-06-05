---
title: 'Procédure : charger du code XML à partir d’un fichier'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: faea93b8eea2b713a8beb7fe199be7d644a07706
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397997"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a>Comment : charger du code XML à partir d’un fichier (Visual Basic)

Cette rubrique montre comment charger des données XML à partir d'un URI en utilisant la méthode <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L'exemple suivant montre comment charger un document XML à partir d'un fichier. L’exemple suivant charge books.xml et affiche l’arborescence XML sur la console.

Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

Ce code génère la sortie suivante :

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

- [Analyse XML (Visual Basic)](parsing-xml.md)
