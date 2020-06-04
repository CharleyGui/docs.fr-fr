---
title: 'Procédure : créer une arborescence à partir d’un XmlReader'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 25c15ff08563b12b26041a536dfbca1c9cce260a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414606"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="753a7-102">Comment : créer une arborescence à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="753a7-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="753a7-103">Cette rubrique montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="753a7-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="753a7-104">Pour créer un objet <xref:System.Xml.Linq.XElement> à partir d'un objet <xref:System.Xml.XmlReader>, vous devez placer l'objet <xref:System.Xml.XmlReader> sur un nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="753a7-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="753a7-105">L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée.</span><span class="sxs-lookup"><span data-stu-id="753a7-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="753a7-106">Pour éviter de telles erreurs, placez toujours l'objet <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="753a7-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="753a7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="753a7-107">Example</span></span>

<span data-ttu-id="753a7-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="753a7-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="753a7-109">Le code suivant crée un objet `T:System.Xml.XmlReader`, puis il lit les nœuds jusqu'à trouver le premier nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="753a7-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="753a7-110">Il charge ensuite l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="753a7-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="753a7-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="753a7-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="753a7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="753a7-112">See also</span></span>

- [<span data-ttu-id="753a7-113">Analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="753a7-113">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
