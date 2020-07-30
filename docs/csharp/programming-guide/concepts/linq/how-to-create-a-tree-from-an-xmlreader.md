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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="b9cfd-104">Comment créer une arborescence à partir d’un XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cfd-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="b9cfd-105">Cette rubrique montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b9cfd-106">Pour créer un objet <xref:System.Xml.Linq.XElement> à partir d'un objet <xref:System.Xml.XmlReader>, vous devez placer l'objet <xref:System.Xml.XmlReader> sur un nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="b9cfd-107">L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="b9cfd-108">Pour éviter de telles erreurs, placez toujours l'objet <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9cfd-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9cfd-109">Example</span></span>  
 <span data-ttu-id="b9cfd-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b9cfd-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b9cfd-111">Le code suivant crée un objet `T:System.Xml.XmlReader`, puis il lit les nœuds jusqu'à trouver le premier nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="b9cfd-112">Il charge ensuite l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b9cfd-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b9cfd-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b9cfd-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9cfd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9cfd-114">See also</span></span>

- [<span data-ttu-id="b9cfd-115">Analyse de code XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cfd-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
