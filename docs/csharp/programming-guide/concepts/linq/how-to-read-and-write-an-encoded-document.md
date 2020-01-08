---
title: Comment lire et écrire un document encodé (C#)
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347661"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="96a0d-102">Comment lire et écrire un document encodé (C#)</span><span class="sxs-lookup"><span data-stu-id="96a0d-102">How to read and write an encoded document (C#)</span></span>
<span data-ttu-id="96a0d-103">Pour créer un document XML encodé, vous devez ajouter un objet <xref:System.Xml.Linq.XDeclaration> à l'arborescence XML et définir l'encodage au nom de la page de codes souhaitée.</span><span class="sxs-lookup"><span data-stu-id="96a0d-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="96a0d-104">Toute valeur retournée par <xref:System.Text.Encoding.WebName%2A> est une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="96a0d-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="96a0d-105">Si vous lisez un document encodé, la propriété <xref:System.Xml.Linq.XDeclaration.Encoding%2A> sera définie au nom de la page de codes.</span><span class="sxs-lookup"><span data-stu-id="96a0d-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="96a0d-106">Si vous affectez un nom de page de codes valide à <xref:System.Xml.Linq.XDeclaration.Encoding%2A>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sérialise avec l'encodage spécifié.</span><span class="sxs-lookup"><span data-stu-id="96a0d-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96a0d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="96a0d-107">Example</span></span>  
 <span data-ttu-id="96a0d-108">L'exemple suivant crée deux documents, un avec l'encodage utf-8 et l'autre avec l'encodage utf-16.</span><span class="sxs-lookup"><span data-stu-id="96a0d-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="96a0d-109">Il charge ensuite les documents et imprime l'encodage sur la console.</span><span class="sxs-lookup"><span data-stu-id="96a0d-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
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
  
 <span data-ttu-id="96a0d-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96a0d-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96a0d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96a0d-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
