---
title: Comment charger du code XML à partir d’un fichier (C#)
description: Découvrez comment charger du code XML à partir d’un URI à l’aide de la méthode XElement. Load en C#. Cet exemple charge le fichier XML et imprime l’arborescence XML sur la console.
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 29de914139d1e9abcda2097addca9219d44d2696
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104952"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="84f37-104">Comment charger du code XML à partir d’un fichier (C#)</span><span class="sxs-lookup"><span data-stu-id="84f37-104">How to load XML from a file (C#)</span></span>
<span data-ttu-id="84f37-105">Cette rubrique montre comment charger des données XML à partir d'un URI en utilisant la méthode <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84f37-105">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84f37-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="84f37-106">Example</span></span>  
 <span data-ttu-id="84f37-107">L'exemple suivant montre comment charger un document XML à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="84f37-107">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="84f37-108">L’exemple suivant charge books.xml et affiche l’arborescence XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="84f37-108">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="84f37-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="84f37-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="84f37-110">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="84f37-110">This code produces the following output:</span></span>  
  
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
  