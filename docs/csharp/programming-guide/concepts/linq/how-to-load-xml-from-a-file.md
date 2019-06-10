---
title: 'Procédure : Charger du code XML à partir d’un fichier (C#)'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: cd4e45767b2f72de8d9a3de9814da6260d2413fe
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485312"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="0ce81-102">Procédure : Charger du code XML à partir d’un fichier (C#)</span><span class="sxs-lookup"><span data-stu-id="0ce81-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="0ce81-103">Cette rubrique montre comment charger des données XML à partir d'un URI en utilisant la méthode <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ce81-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce81-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="0ce81-104">Example</span></span>  
 <span data-ttu-id="0ce81-105">L'exemple suivant montre comment charger un document XML à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="0ce81-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="0ce81-106">L’exemple suivant charge books.xml et affiche l’arborescence XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="0ce81-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="0ce81-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0ce81-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="0ce81-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0ce81-108">This code produces the following output:</span></span>  
  
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
  