---
title: Comment lire et écrire un document encodé-LINQ to XML
description: Découvrez comment ajouter un XDeclaration à une arborescence XML pour créer un document XML encodé.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: 66d4fd5521118c76788c677efc75fcce564f0a5c
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553701"
---
# <a name="how-to-read-and-write-an-encoded-document-linq-to-xml"></a><span data-ttu-id="acaa0-103">Comment lire et écrire un document encodé (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="acaa0-103">How to read and write an encoded document (LINQ to XML)</span></span>

<span data-ttu-id="acaa0-104">Pour créer un document XML encodé, vous devez ajouter un objet <xref:System.Xml.Linq.XDeclaration> à l'arborescence XML et définir l'encodage au nom de la page de codes souhaitée.</span><span class="sxs-lookup"><span data-stu-id="acaa0-104">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="acaa0-105">Toute valeur retournée par <xref:System.Text.Encoding.WebName%2A> est une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="acaa0-105">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="acaa0-106">Si vous lisez un document encodé, la propriété <xref:System.Xml.Linq.XDeclaration.Encoding%2A> sera définie au nom de la page de codes.</span><span class="sxs-lookup"><span data-stu-id="acaa0-106">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="acaa0-107">Si vous définissez <xref:System.Xml.Linq.XDeclaration.Encoding%2A> sur un nom de page de codes valide, LINQ to XML sérialisera avec l’encodage spécifié.</span><span class="sxs-lookup"><span data-stu-id="acaa0-107">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, LINQ to XML will serialize with the specified encoding.</span></span>

## <a name="example-create-two-documents-that-have-different-encoding-and-identify-the-encoding"></a><span data-ttu-id="acaa0-108">Exemple : créer deux documents avec un encodage différent et identifier l’encodage.</span><span class="sxs-lookup"><span data-stu-id="acaa0-108">Example: Create two documents that have different encoding and identify the encoding.</span></span>

<span data-ttu-id="acaa0-109">L'exemple suivant crée deux documents, un avec l'encodage utf-8 et l'autre avec l'encodage utf-16.</span><span class="sxs-lookup"><span data-stu-id="acaa0-109">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="acaa0-110">Il charge ensuite les documents et imprime l'encodage sur la console.</span><span class="sxs-lookup"><span data-stu-id="acaa0-110">It then loads the documents and prints the encoding to the console.</span></span>

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

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

<span data-ttu-id="acaa0-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="acaa0-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="acaa0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acaa0-112">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
