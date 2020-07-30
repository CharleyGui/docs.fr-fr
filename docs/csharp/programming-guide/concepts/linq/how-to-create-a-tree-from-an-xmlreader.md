---
title: Comment créer une arborescence à partir d’un XmlReader (C#)
description: Découvrez comment créer une arborescence XML directement à partir d’un XmlReader. Consultez un exemple illustrant comment créer un objet T:System.Xml.XmlReader.
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302657"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Comment créer une arborescence à partir d’un XmlReader (C#)
Cette rubrique montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>. Pour créer un objet <xref:System.Xml.Linq.XElement> à partir d'un objet <xref:System.Xml.XmlReader>, vous devez placer l'objet <xref:System.Xml.XmlReader> sur un nœud d'élément. L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée. Pour éviter de telles erreurs, placez toujours l'objet <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de l'objet <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Le code suivant crée un objet `T:System.Xml.XmlReader`, puis il lit les nœuds jusqu'à trouver le premier nœud d'élément. Il charge ensuite l'objet <xref:System.Xml.Linq.XElement>.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
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

- [Analyse de code XML (C#)](how-to-parse-a-string.md)
