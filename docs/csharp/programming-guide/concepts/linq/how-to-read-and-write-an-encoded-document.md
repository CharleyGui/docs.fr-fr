---
title: Comment lire et écrire un document encodé (C#)
description: Apprenez à créer un document XML encodé en C# en ajoutant un XDeclaration à l’arborescence XML et en définissant l’encodage sur le nom de la page de codes souhaitée.
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: ed02b7467f4de71455da516a6c894070337684e7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104313"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="42cf2-103">Comment lire et écrire un document encodé (C#)</span><span class="sxs-lookup"><span data-stu-id="42cf2-103">How to read and write an encoded document (C#)</span></span>
<span data-ttu-id="42cf2-104">Pour créer un document XML encodé, vous devez ajouter un objet <xref:System.Xml.Linq.XDeclaration> à l'arborescence XML et définir l'encodage au nom de la page de codes souhaitée.</span><span class="sxs-lookup"><span data-stu-id="42cf2-104">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="42cf2-105">Toute valeur retournée par <xref:System.Text.Encoding.WebName%2A> est une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="42cf2-105">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="42cf2-106">Si vous lisez un document encodé, la propriété <xref:System.Xml.Linq.XDeclaration.Encoding%2A> sera définie au nom de la page de codes.</span><span class="sxs-lookup"><span data-stu-id="42cf2-106">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="42cf2-107">Si vous affectez un nom de page de codes valide à <xref:System.Xml.Linq.XDeclaration.Encoding%2A>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sérialise avec l'encodage spécifié.</span><span class="sxs-lookup"><span data-stu-id="42cf2-107">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42cf2-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="42cf2-108">Example</span></span>  
 <span data-ttu-id="42cf2-109">L'exemple suivant crée deux documents, un avec l'encodage utf-8 et l'autre avec l'encodage utf-16.</span><span class="sxs-lookup"><span data-stu-id="42cf2-109">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="42cf2-110">Il charge ensuite les documents et imprime l'encodage sur la console.</span><span class="sxs-lookup"><span data-stu-id="42cf2-110">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="42cf2-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="42cf2-111">This example produces the following output:</span></span>  
  
```output  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="42cf2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42cf2-112">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
